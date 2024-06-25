# Java Multithreading Types of creating threads examples

## - Extending the Thread class
## - Implementing the Runnable interface

### Method 1: Extending the Thread Class
When you extend the `Thread` class, you override its `run()` method to define the code that should execute in the new thread.

#### Example:
```java
// Extending the Thread class
class MyThread extends Thread {
    @Override
    public void run() {
        // This is the code that will run in the new thread
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName() + " - " + i);
            try {
                Thread.sleep(500); // Sleep for 500 milliseconds
            } catch (InterruptedException e) {
                System.out.println(e.getMessage());
            }
        }
    }
}
```
```java
public class ThreadExample {
    public static void main(String[] args) {
        // Creating instances of the MyThread class
        MyThread thread1 = new MyThread();
        MyThread thread2 = new MyThread();
        
        // Starting the threads
        thread1.start();
        thread2.start();
    }
}
```
#### Explanation:
Extending Thread: We create a class MyThread that extends Thread and override its run() method. This method contains the code that will be executed in the new thread.
Creating Instances: In the main method, we create instances of MyThread.
Starting Threads: We call the start() method on each instance. This method internally calls the run() method in a new thread of execution.

---------------

### Method 2: Implementing the Runnable Interface
Implementing the Runnable interface is more flexible because it allows you to extend another class if needed.

#### Example:
```java
// Implementing the Runnable interface
class MyRunnable implements Runnable {
    @Override
    public void run() {
        // This is the code that will run in the new thread
        for (int i = 0; i < 5; i++) {
            System.out.println(Thread.currentThread().getName() + " - " + i);
            try {
                Thread.sleep(500); // Sleep for 500 milliseconds
            } catch (InterruptedException e) {
                System.out.println(e.getMessage());
            }
        }
    }
}
```
```java
public class RunnableExample {
    public static void main(String[] args) {
        // Creating instances of the MyRunnable class
        MyRunnable myRunnable = new MyRunnable();
        
        // Creating Thread objects and passing the MyRunnable instances
        Thread thread1 = new Thread(myRunnable);
        Thread thread2 = new Thread(myRunnable);
        
        // Starting the threads
        thread1.start();
        thread2.start();
    }
}
```
#### Explanation:
Implementing Runnable: We create a class MyRunnable that implements the Runnable interface and override its run() method.
Creating Runnable Instance: In the main method, we create an instance of MyRunnable.
Creating Threads: We create Thread objects and pass the MyRunnable instance to the Thread constructor.
Starting Threads: We call the start() method on each Thread object to begin execution in new threads.
