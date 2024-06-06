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

# 第三章 共享数据

## 条件竞争

我们引入了不变量的概念，比如BPT中的左儿子和右儿子节点等。当进行查询操作时，这些内容没有被修改，所以不变量没有改变，顺序没有任何关系。如果不变量被修改时，其他线程又恰好访问了这一部分数据，那么就会出现UB。我们把这样的数据竞争称为条件竞争。调试过程中，一般调不出来这些问题。因为这样的条件竞争显然是时间敏感的，必须非常凑巧。

## 互斥量

```cpp
mutex my_mutex;
vector<int> test; 
void MyPushBack(int x) {
  lock_guard<mutex> my_guard(my_mutex);
  test.push_back(x);
  return;
}
int MyUnder(int x) {
  lock_guard<mutex> my_guard(my_mutex);
  return test[x];
}
```

使用这样的代码，可以保证两种函数不会同时对数据进行访问。lock_guard类可以自动给对象上锁，并且在析构的时候自动解锁。

在进行编程的时候，尽量不要把受保护的内容引用或指针传递到互斥量作用域之外。

我们需要想办法找到一个锁的合适的颗粒度。如果颗粒度过大，可能BPT的并发两行就写完了，没有意义。如果颗粒度过小，数据的保护效果可能不是很好。

死锁的出现：互相持有一个不同的互斥量，但是相互又想要请求对方的互斥量锁。

```cpp
mutex mymutex1, mymutex2;
void Test() {
  lock(mymutex1, mymutex2);
  lock_guard my_guard1(mymutex1, adopt_lock);
  lock_guard my_guard2(mymutex2, adopt_lock);
}
```

此为一种解决方案。也就是说，在申请锁的时候，一下子申请两个锁。随后将其分配给lock_guard的实例，转移互斥量的控制权。

为了避免死锁，一般有这么几种方式：避免嵌套锁、使用自己的代码，保持获取锁的固定顺序、使用层次锁结构。

使用herarchical_mutex可以创建不同层的锁实例。一个线程持有高层次锁的时候，可以进一步申请低层次锁。但是持有低层次锁时，无法申请高层次锁。

在初始化时，我们需要将最初的所有线程的初始值设置为最大值，以便于获取任意层次的锁。

unique_lock是一种类似于lock_guard的类型。但是，它更加灵活，可以自行调用lock和unlock函数。在作用域结束后一样会被析构。使用defer_lock而非adopt_lock，就可以只记录互斥量的信息，但不会上锁。unique_lock也是只可移动，不可复制。

## 保护共享数据的方式

为了避免多个线程对同一部分数据进行初始化操作。我们可以引入once_flag和call_once。once_flag用来标记只能执行一次。call_once能够保证只有一个线程可以执行这部分函数。

```cpp
void f(){};
once_flag flag;
call_once(flag,f);
```

我们也可以保护那些不常用的数据。

如果使用recursive_mutex，那么我们就允许一个线程多次对同一个互斥量上锁。并且需要多次解锁。

# 第四章 同步操作

## 等待事件或条件

一种方式，是采用

```cpp
mutex x;
void test(){
unique_lock test(x);
test.unlock();
this_thread::sleep_for(chrono::milliseconds(100));
test.lock();
}
```

这样操作，允许其他线程在该线程休眠期间，获取mutex的锁。

notify_one函数和wait函数通常会同时使用。这两者都是条件变量的成员函数。notify_one函数是在一个线程的操作基本完成之后，通知其他的线程。其他的线程如果已经调用了wait函数，那么就会重新开始检查，是否满足条件。如果满足条件，就会继续运行。wait函数在条件不满足时，会解锁mutex，保证其他线程可以获取这个互斥量，并且继续等待。否则，则获取这个互斥量。需要注意，在使用notify_one的时候，需要保证当前线程已经获得了所需的mutex。

## future

```cpp
int f() {
  return 114514;
}
int main() {
  future<int> test = async(f);
  this_thread::sleep_for(chrono::seconds(1));
  cout << test.get() << endl;
  return 0;
}
```

采用这种方式，可以异步处理一定的对象。通过get函数，我们可以返回future事件的处理结果。当然，也可以传参。

```cpp
auto f1 = async(launch::deferred, f);
auto f2 = async(lauch::async, f);
```

f1会在调用get函数或者wait函数的时候才会执行。其被延迟了。f2则会立刻开启了一个新线程开始工作。

packaged_task是一个全新的模版类型，其参数是一个函数的类型签名，（包含函数的类型，形参表）。它会返回一个future类型，并且，它的主要作用在于可以在不同的线程之间达到通信的效果，从而传递数据。不过需要注意的是，一个packaged_task只能执行一次！

promise也是一种类型，其模版参数的使用方法和future相同。

```cpp
void doWork(std::promise<int>& p) {
    // 模拟耗时操作
    std::this_thread::sleep_for(std::chrono::seconds(2));

    int result = 42;

    // 设置值给 promise
    p.set_value(result);
}

int main() {
    std::promise<int> myPromise;
    std::future<int> result = myPromise.get_future();  // 获取与 promise 关联的 future

    std::thread worker(doWork, std::ref(myPromise));  // 启动线程执行任务

    // 获取任务的返回值
    int value = result.get();
    std::cout << "任务的结果：" << value << std::endl;

    worker.join();

    return 0;
}
```

使用这种方法，我们可以把线程与promise相连接。通过get_future函数，我们可以获得产生的future类型，并且捕捉相关的异常信息。在async过程中，如果出现了异常，在使用get函数的过程中就可以再次抛出这个异常。对于promise，我们可以调用promise类的set_ecxeption函数，从而显式地给promise对象存储一个异常。

但是，future类是只移动的。我们希望可以使用shared_future实例来进行。shared_future返回的结果是不同步的，我们需要使用互斥量来对访问进行保护。为了减少数据竞争的出现，由于shared_future实例是可拷贝的，所以我们可以将其进行拷贝到线程之中，再次进行操作。

shared_future类型可以使用move函数，将future类型的所有权转移。

## 限时等待

我们可以对线程的等待做出一定的限制。如果等待时间过长，我们就认为其超时了。一般而言，我们具有两种方式进行超时判断。第一种，是时间段，使线程等待比如30ms之类的时间。第二种，是时间点，比如规定在某个时间超时。

mutex和recursive_mutex都不支持超时操作。但是，time_mutex和recursive_timed_mutex都是支持超时操作的。这两种类型都具有try_lock_for()和try_lock_until()函数，可以在一个时间段内持续尝试获取锁，或者在指定的时间点前获取互斥锁。这两个函数的返回值均为bool类型。成功获取锁时，会返回true，失败时，则会返回false。

# 
