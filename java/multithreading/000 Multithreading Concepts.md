# Java Multithreading Concepts

## Basic Concepts

### What is a thread?
A thread is the smallest unit of execution in a program. It is a separate path of execution, making it possible to perform multiple operations concurrently within a single process.

### What is multithreading?
Multithreading is a programming concept that allows multiple threads to run concurrently, improving the performance of applications by performing tasks in parallel.

### Difference between `Thread` class and `Runnable` interface?
- **`Thread` class**: By extending the `Thread` class, you can create a new thread by overriding its `run()` method.
- **`Runnable` interface**: By implementing the `Runnable` interface, you can create a new thread by passing an instance of `Runnable` to a `Thread` object and then calling `start()`.

## Thread Lifecycle

### Describe the lifecycle of a thread.
- **New**: A thread is in this state when it is created but not yet started.
- **Runnable**: The thread is ready to run and waiting for CPU cycles.
- **Running**: The thread is executing.
- **Blocked/Waiting**: The thread is blocked or waiting for a condition to be met or resources to be available.
- **Terminated**: The thread has finished its execution.

### What is the difference between `wait()` and `sleep()`?
- **`wait()`**: This method causes the current thread to wait until another thread calls `notify()` or `notifyAll()` on the same object. It releases the lock on the object.
- **`sleep()`**: This method causes the current thread to pause execution for a specified period. It does not release the lock on the object.

## Synchronization

### What is synchronization in Java?
Synchronization is a mechanism to control the access of multiple threads to a shared resource. It helps to prevent thread interference and memory consistency errors.

### What are the ways to achieve synchronization in Java?
- Using the `synchronized` keyword: applied to methods or blocks.
- Using locks from the `java.util.concurrent.locks` package, such as `ReentrantLock`.

### What is a deadlock? How can it be avoided?
A deadlock is a situation where two or more threads are blocked forever, waiting for each other to release resources.
It can be avoided by following practices like avoiding nested locks, using a timeout, and ensuring that all threads acquire locks in the same order.

## Advanced Topics

### What is the difference between `synchronized` and `ReentrantLock`?
- **`synchronized`**: Simpler and is a keyword in Java. It provides automatic release of the lock.
- **`ReentrantLock`**: More flexible, with features like lock polling, timed locks, and interruptible locks. However, it requires explicit lock and unlock calls.

### What is the `volatile` keyword in Java?
`volatile` is a keyword that ensures that the value of a variable is always read from and written to the main memory. It is used to avoid memory consistency errors in multi-threaded programs.

### What is the `ThreadLocal` class?
`ThreadLocal` provides thread-local variables. Each thread accessing such a variable has its own, independently initialized copy of the variable.

## Concurrency Utilities

### What are the differences between `Executor`, `ExecutorService`, and `ScheduledExecutorService`?
- **`Executor`**: A simple interface for launching new tasks.
- **`ExecutorService`**: Extends `Executor` and provides methods for managing the lifecycle of threads and asynchronous task execution.
- **`ScheduledExecutorService`**: Extends `ExecutorService` and provides methods to execute commands periodically or after a given delay.

### What is a `Callable` and how does it differ from `Runnable`?
- **`Callable`**: Similar to `Runnable` but can return a result and throw a checked exception.
- **`Runnable`**: Does not return a result and cannot throw a checked exception.

### What are the benefits of using the `ForkJoinPool`?
`ForkJoinPool` is designed for work that can be broken into smaller pieces recursively. It uses a work-stealing algorithm to keep all threads busy, which can improve performance for certain types of tasks.

### What is a `CountDownLatch`?
`CountDownLatch` is a synchronization aid that allows one or more threads to wait until a set of operations being performed in other threads completes.

## Practical Scenarios

### How would you handle thread safety in a Java class?
- Use synchronized blocks or methods.
- Use thread-safe collections from the `java.util.concurrent` package.
- Use `volatile` for shared variables.
- Use atomic variables from the `java.util.concurrent.atomic` package.

### What is the purpose of the `Thread.yield()` method?
`Thread.yield()` is a hint to the thread scheduler that the current thread is willing to yield its current use of the CPU. It can help improve the responsiveness of an application.

### Explain the concept of thread starvation and how to prevent it.
Thread starvation occurs when a thread is perpetually denied access to resources. This can be prevented by using fair scheduling policies, priority adjustments, and avoiding long-running exclusive locks.

Preparing for these questions will give you a good foundation in Java multithreading concepts. Good luck with your interview!
