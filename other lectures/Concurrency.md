# 第二章 线程管理

## 线程，启动！

```cpp
void DoSomething() {};
std::thread my_thread(DoSomething);
```

这样就创建了一个线程。一般使用的是void函数。这样，当函数执行结束后，线程也跟着结束了。

如果一个类重载了函数运算符，那么它的实例也可以作为thread的构造参数。

把函数对象传入线程构造函数之时，我们不可以使用临时变量。假设我们创建了一个名为A的类，其已重载了函数运算符，如果我们写

```cpp
std::thread my_thread(A());
```

天才的C++就会认为这是一个函数声明。

为了避免出现这个问题，也许把调用构造函数时的小括号换成大括号是个不错的方法。

如果主线程终止后，新线程依旧在瞎搞，就会出现UB。是故，我们应当使用join方法或者detach方法。

如果我们打算等待新线程结束后再退出主线程，那么我们可以写：

```cpp
my_thread.join();
```

需要注意的是，如果线程运行时抛出异常，并且抛出异常的时机在调用join方法之前，那么就会跳过join。最好在异常处理的语句中也加上join方法的调用。

如果使用detach方法，那么线程就会在后台开始运行，其与主线程之间不再有交互的可能，其他的线程亦不可访问之。并且，被detach的线程不可再join。

分离线程常被称为守护线程。其运行时间长，可能进行很多操作。

## 传参

```cpp
void f(int x, const int &y);
std::thread my_thread(f, 114514, 1919810);
```

即使函数参数采用了引用传递的方式，其也会被拷贝至新线程的内存空间中。因此，倘若不是const引用，编译器运行时，发现我们试图引用一个右值，就会报错。

```cpp
void f(int x, int & y) {
  cout << ++y << endl;
}
int main() {
  int data = 1919810;
  thread my_thread(f, 114514, data);
  my_thread.join();
  return 0;
}//CE

void f(int x, int & y) {
  cout << ++y << endl;
}
int main() {
  int data = 1919810;
  thread my_thread(f, 114514, ref(data));
  my_thread.join();
  return 0;
}//Correct
```

需要传入引用！

```cpp
class A {
  public:
    void Test() {
      cout << "OK";
    };
};
int main() {
  A x;
  thread my_thread(&A::Test, &x);
  my_thread.join();
  return 0;
}
```

使用引用的方式，我们可以调用成员函数。

## 转移所有权

线程属于资源占有的类型，它不可以进行复制操作。但是可以进行移动操作。

```cpp
void f();
std::thread thread_1(f);
std::thread thread_2 = std::move(thread_1);
```

这样，我们就转移了线程的所有权。thread_1已经和它所控制的线程不再有任何联系了。如果在转移时，thread_2拥有某个线程的控制权，那么thread_2的原线程会被终止。

## 确定线程数量

```cpp
std::thread::hardware_concurrency()//可以返回并发线程的数量。
```

## 线程标识

```cpp
std::thread::id//是一种类型。可以存储线程的id。
std::this_thread::get_id()//可以返回当前线程的id。为上述提到的类型。
```
