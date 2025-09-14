# Java 8 CompletableFuture & Concurrency ⚡

Java 8 introduced **CompletableFuture** to handle **asynchronous programming** and simplify **concurrent operations**. It allows writing **non-blocking, functional-style code** for tasks that run in parallel.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Creating CompletableFuture](#creating-completablefuture)
3. [Chaining Operations](#chaining-operations)
4. [Combining Futures](#combining-futures)
5. [Exception Handling](#exception-handling)
6. [Examples](#examples)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## Introduction 💡

`CompletableFuture` provides a **flexible, non-blocking mechanism** to run tasks asynchronously and **combine multiple asynchronous computations**.

---

## Creating CompletableFuture 🔧

```java
// Run asynchronously, no result
CompletableFuture<Void> future1 = CompletableFuture.runAsync(() -> {
    System.out.println("Running async task");
});

// Run asynchronously, with result
CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> {
    return 10 + 20;
});

System.out.println(future2.get()); // 30
```

---

## Chaining Operations 🔗

```java
CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 5)
    .thenApply(n -> n * 2)       // Transform result
    .thenApply(n -> n + 10);

System.out.println(future.get()); // 20
```

* `thenApply()` → transform result
* `thenAccept()` → consume result without returning
* `thenRun()` → run another task after completion

---

## Combining Futures 🔄

```java
CompletableFuture<Integer> f1 = CompletableFuture.supplyAsync(() -> 10);
CompletableFuture<Integer> f2 = CompletableFuture.supplyAsync(() -> 20);

// Combine results
CompletableFuture<Integer> combined = f1.thenCombine(f2, (a, b) -> a + b);
System.out.println(combined.get()); // 30

// Run after both complete
CompletableFuture<Void> bothDone = f1.thenAcceptBoth(f2, (a, b) -> System.out.println(a * b)); // 200
```

---

## Exception Handling ⚠️

```java
CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
    if(true) throw new RuntimeException("Error!");
    return 5;
}).exceptionally(ex -> {
    System.out.println("Exception: " + ex.getMessage());
    return 0;
});
System.out.println(future.get()); // 0
```

* `exceptionally()` → handle exceptions
* `handle()` → handle result and exception

---

## Examples 📝

**1. Simple async computation**

```java
CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 10 * 2);
future.thenAccept(System.out::println); // 20
```

**2. Multiple async tasks with combination**

```java
CompletableFuture<Integer>
```
