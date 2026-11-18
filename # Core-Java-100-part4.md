# Core-Java-100.md
# Part 4 (Q76–Q100)
# Multithreading & Concurrency

---

# Q76. What is Multithreading in Java?

## Detailed Answer
Multithreading is the capability of a program to execute multiple threads concurrently. A thread is the smallest unit of execution within a process. Multithreading improves application responsiveness and CPU utilization.

## Real-world Use Case
An e-commerce application simultaneously handles user requests, payment processing, and notification services.

## Code Example

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread Running");
    }
}

public class Main {
    public static void main(String[] args) {
        new MyThread().start();
    }
}
```

---

# Q77. What is the difference between Process and Thread?

## Detailed Answer
A process is an independent program with its own memory space, while a thread is a lightweight execution unit within a process. Threads share memory with other threads in the same process.

## Real-world Use Case
A browser is a process, while each tab may run multiple threads.

## Code Example

```java
Process:
Chrome.exe

Threads:
UI Thread
Network Thread
Rendering Thread
```

---

# Q78. How do you create a Thread in Java?

## Detailed Answer
A thread can be created by extending the Thread class or implementing the Runnable interface. Runnable is preferred because it supports multiple inheritance through interfaces.

## Real-world Use Case
Background report generation tasks.

## Code Example

```java
class Task implements Runnable {
    public void run() {
        System.out.println("Task Executed");
    }
}

new Thread(new Task()).start();
```

---

# Q79. Difference between Thread and Runnable?

## Detailed Answer
Thread is a class, whereas Runnable is a functional interface. Implementing Runnable provides better flexibility because the class can still extend another class.

## Real-world Use Case
Most enterprise applications use Runnable with thread pools.

## Code Example

```java
Runnable task = () ->
        System.out.println("Running");

new Thread(task).start();
```

---

# Q80. What is Thread Lifecycle?

## Detailed Answer
A thread moves through New, Runnable, Running, Waiting/Blocked, and Terminated states. JVM manages state transitions based on scheduling and synchronization.

## Real-world Use Case
Understanding performance bottlenecks during thread dumps.

## Code Example

```java
Thread t = new Thread();

t.start();
```

Lifecycle:

```text
NEW → RUNNABLE → RUNNING
          ↓
      WAITING
          ↓
     TERMINATED
```

---

# Q81. What is start() vs run()?

## Detailed Answer
start() creates a new thread and invokes run() internally. Directly calling run() executes code in the current thread without creating a new thread.

## Real-world Use Case
A common interview trap for beginners.

## Code Example

```java
Thread t = new Thread(() ->
        System.out.println("Child Thread"));

t.start(); // New thread

t.run();   // Current thread
```

---

# Q82. What is Thread Scheduler?

## Detailed Answer
Thread Scheduler decides which runnable thread gets CPU time. Scheduling behavior depends on JVM and operating system implementation.

## Real-world Use Case
Multiple API requests competing for execution time.

## Code Example

```java
Thread t1 = new Thread();
Thread t2 = new Thread();

t1.start();
t2.start();
```

---

# Q83. What is Thread Priority?

## Detailed Answer
Thread priority suggests the relative importance of a thread. Values range from 1 to 10. Priority is only a hint and does not guarantee execution order.

## Real-world Use Case
Background logging threads may have lower priority.

## Code Example

```java
thread.setPriority(
        Thread.MAX_PRIORITY);
```

---

# Q84. What is join() Method?

## Detailed Answer
join() causes the current thread to wait until another thread completes execution.

## Real-world Use Case
Waiting for report generation before sending an email.

## Code Example

```java
Thread t = new Thread(task);

t.start();

t.join();
```

---

# Q85. What is sleep() Method?

## Detailed Answer
sleep() temporarily pauses the execution of a thread for a specified duration. It does not release locks held by the thread.

## Real-world Use Case
Retry mechanisms between API calls.

## Code Example

```java
Thread.sleep(2000);
```

---

# Q86. What is Synchronization?

## Detailed Answer
Synchronization ensures only one thread accesses a critical section at a time. It prevents race conditions and inconsistent data updates.

## Real-world Use Case
Account balance updates in banking applications.

## Code Example

```java
public synchronized void withdraw() {
    balance -= 100;
}
```

---

# Q87. What is Race Condition?

## Detailed Answer
A race condition occurs when multiple threads access and modify shared data simultaneously, producing unpredictable results.

## Real-world Use Case
Incorrect stock quantity updates during flash sales.

## Code Example

```java
count++;
```

Two threads updating count simultaneously can produce incorrect values.

---

# Q88. What is Deadlock?

## Detailed Answer
Deadlock occurs when two or more threads wait indefinitely for resources held by each other. None of the threads can proceed.

## Real-world Use Case
Competing database resource locks.

## Code Example

```java
Thread1 : Lock A -> Lock B

Thread2 : Lock B -> Lock A
```

Result:

```text
Deadlock
```

---

# Q89. How can Deadlock be avoided?

## Detailed Answer
Deadlocks can be avoided using consistent lock ordering, timeout-based locking, minimizing synchronized blocks, and using concurrent utilities.

## Real-world Use Case
Large-scale banking systems avoid deadlocks through predefined lock ordering.

## Code Example

```java
Always acquire locks:

LockA
then
LockB
```

---

# Q90. What is volatile Keyword?

## Detailed Answer
volatile ensures visibility of variable updates across threads. It prevents caching of variable values in thread-local memory.

## Real-world Use Case
Shutdown flags used by multiple threads.

## Code Example

```java
private volatile boolean running = true;
```

---

# Q91. What is Executor Framework?

## Detailed Answer
Executor Framework provides a higher-level API for thread management. It separates task submission from thread execution.

## Real-world Use Case
Spring Boot applications use thread pools extensively.

## Code Example

```java
ExecutorService executor =
        Executors.newFixedThreadPool(5);

executor.submit(() ->
        System.out.println("Task"));
```

---

# Q92. What is Callable Interface?

## Detailed Answer
Callable is similar to Runnable but can return a value and throw checked exceptions.

## Real-world Use Case
Fetching results from asynchronous database queries.

## Code Example

```java
Callable<Integer> task =
        () -> 100;
```

---

# Q93. Difference between Runnable and Callable?

## Detailed Answer
Runnable does not return values and cannot throw checked exceptions. Callable returns results and supports checked exceptions.

## Real-world Use Case
Background processing with a response value.

## Code Example

```java
Callable<String> task =
        () -> "Completed";
```

---

# Q94. What is Future Interface?

## Detailed Answer
Future represents the result of an asynchronous computation. It allows checking completion status and retrieving results.

## Real-world Use Case
Order processing systems waiting for external service responses.

## Code Example

```java
Future<Integer> future =
executor.submit(() -> 100);

System.out.println(future.get());
```

---

# Q95. What is CompletableFuture?

## Detailed Answer
CompletableFuture provides asynchronous programming with chaining, combining, and exception handling. It simplifies complex async workflows.

## Real-world Use Case
Fetching customer, payment, and order data simultaneously.

## Code Example

```java
CompletableFuture<String> future =
    CompletableFuture.supplyAsync(
        () -> "Java"
    );

future.thenAccept(System.out::println);
```

---

# Q96. What is ConcurrentHashMap?

## Detailed Answer
ConcurrentHashMap allows concurrent reads and writes without locking the entire map. It provides better scalability than synchronized maps.

## Real-world Use Case
Session caches in highly concurrent systems.

## Code Example

```java
ConcurrentHashMap<Integer,String>
map = new ConcurrentHashMap<>();
```

---

# Q97. What is ReentrantLock?

## Detailed Answer
ReentrantLock provides advanced locking functionality compared to synchronized blocks. It supports fairness, tryLock(), and interruptible locking.

## Real-world Use Case
Enterprise transaction processing systems.

## Code Example

```java
Lock lock = new ReentrantLock();

lock.lock();

try {
    // business logic
}
finally {
    lock.unlock();
}
```

---

# Q98. What is Producer Consumer Problem?

## Detailed Answer
Producer Consumer is a synchronization problem where producers generate data and consumers process it. Coordination prevents overflow and underflow issues.

## Real-world Use Case
Message queue systems such as Kafka and RabbitMQ.

## Code Example

```java
BlockingQueue<Integer> queue =
        new ArrayBlockingQueue<>(10);
```

---

# Q99. What is Fork Join Framework?

## Detailed Answer
Fork Join Framework breaks large tasks into smaller subtasks and executes them in parallel using work-stealing algorithms.

## Real-world Use Case
Parallel processing of huge datasets.

## Code Example

```java
ForkJoinPool pool =
        new ForkJoinPool();

pool.invoke(task);
```

---

# Q100. What are the most frequently asked Java Concurrency Interview Questions?

## Detailed Answer
Interviewers commonly focus on synchronization, volatile, deadlock, ConcurrentHashMap, ExecutorService, CompletableFuture, race conditions, thread lifecycle, and lock mechanisms. Real-world problem-solving scenarios are usually preferred over theoretical definitions.

## Real-world Use Case
Senior Java Full Stack interviews at product-based companies often involve thread safety and performance optimization questions.

## Code Example

```java
ExecutorService executor =
    Executors.newFixedThreadPool(10);

CompletableFuture.runAsync(
    () -> processOrders(),
    executor
);
```

---

# ✅ Part 4 Completed (Q76–Q100)

## Topics Covered

### Multithreading Fundamentals
- Threads
- Runnable
- Thread Lifecycle
- Thread States
- start() vs run()
- join()
- sleep()

### Synchronization & Thread Safety
- Synchronization
- Race Condition
- Deadlock
- Volatile
- Locks

### Java Concurrency APIs
- Executor Framework
- Callable
- Future
- CompletableFuture
- ConcurrentHashMap
- ReentrantLock

### Concurrent Design Patterns
- Producer Consumer
- Fork Join Framework

---

# ✅ Core-Java-100.md Completed

### Final Distribution

| Section | Questions |
|----------|------------|
| Core Java Fundamentals | Q1-Q30 |
| Collections Framework | Q31-Q50 |
| Generics + Java 8 + Streams | Q51-Q75 |
| Multithreading & Concurrency | Q76-Q100 |
| **Total** | **100 Questions** |

This provides a strong repository-ready foundation for **3-8 years Java Full Stack Developer interviews**, covering the most commonly asked topics in service-based and product-based companies.