* [Create Thread](#fireCreate-Thread)
    * [Runnable Interface](#by-Implementing-a-Runnable-Interface)
    * [Callable Interface](#by-Implementing-a-Callable-Interface)
    * [Thread Class](#by-Extending-a-Thread-Class)
* [Synchronization](#fireSynchronization)
    * [synchronized](#synchronized)
    * [ReentrantLcok](#fireReentrantLcok)
* [Life cycle of thread](#Life-cycle-of-thread)
## :fire:Create Thread
### by Implementing a Runnable Interface
1) First, implement a run() method provided by a Runnable interface. This method provides an entry point for the thread and you will put your complete business logic inside this method.
```
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        // ...
    }
}
```
2) Second, instantiate a Thread object using the following constructor
3) Once a Thread object is created, you can start it by calling start() method, which executes a call to run( ) method.
```
public static void main(String[] args) {
    MyRunnable instance = new MyRunnable();
    Thread thread = new Thread(instance);
    thread.start();
}
```
### by Implementing a Callable Interface
* Compared with Runnable, Callable has return value. The return value packed by FutureTask
```
public class MyCallable implements Callable<Integer> {
    public Integer call() {
        return 123;
    }
}
public static void main(String[] args) throws ExecutionException, InterruptedException {
    MyCallable mc = new MyCallable();
    FutureTask<Integer> ft = new FutureTask<>(mc);
    Thread thread = new Thread(ft);
    thread.start();
    System.out.println(ft.get());
}
```
### by Extending a Thread Class
* This approach provides more flexibility in handling multiple threads created using available methods in Thread class.
1) override run( ) method available in Thread class.
2) Once Thread object is created, you can start it by calling start() method, which executes a call to run( ) method.
```
public class MyThread extends Thread {
    public void run() {
        // ...
    }
}
public static void main(String[] args) {
    MyThread mt = new MyThread();
    mt.start();
}
```
* Implementing interface is better than extending thread class because JAVA doesn't support multi-inherentican. If extend Thread class, it can not inherit other classes. Besides, it costs a lot for Thread class when the class only wants to execute.

## :fire:Synchronization
* Java provides two **locking mechanisms** to control mutually exclusive access to Shared resources by multiple threads, the first being **synchronized** for the JVM implementation and the other being **ReentrantLock** for the JDK implementation.
### synchronized
* When one thread enters a synchronized block, the other thread must wait.
```
public void func() {
    synchronized (this) {
        // ...
    }
}
public synchronized void func () {
    // ...
}
public void func() {
    synchronized (SynchronizedExample.class) {
        // ...
    }
}
public synchronized static void fun() {
    // ...
}
```
### ReentrantLcok
```
public class LockExample {

    private Lock lock = new ReentrantLock();

    public void func() {
        lock.lock();
        try {
            for (int i = 0; i < 10; i++) {
                System.out.print(i + " ");
            }
        } finally {
            lock.unlock(); // 确保释放锁，从而避免发生死锁。
        }
    }
}
```

## :fire:Life cycle of thread
![](https://www.tutorialspoint.com/java/images/Thread_Life_Cycle.jpg)
* New − A new thread begins its life cycle in the new state. It remains in this state until the program starts the thread. It is also referred to as a born thread.
* Runnable − After a newly born thread is started, the thread becomes runnable. A thread in this state is considered to be executing its task.
* Blocked
* Waiting − Sometimes, a thread transitions to the waiting state while the thread waits for another thread to perform a task. A thread transitions back to the runnable state only when another thread signals the waiting thread to continue executing.
* Timed Waiting − A runnable thread can enter the timed waiting state for a specified interval of time. A thread in this state transitions back to the runnable state when that time interval expires or when the event it is waiting for occurs.
* Terminated (Dead) − A runnable thread enters the terminated state when it completes its task or otherwise terminates.
