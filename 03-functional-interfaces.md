# Functional Interfaces in Java 8 ⚡

Functional interfaces are a key concept in Java 8 that allow us to write **concise, functional-style code** using **Lambda expressions**. They have exactly **one abstract method** and can have multiple default or static methods.

---

## Table of Contents

1. [What is a Functional Interface?](#what-is-a-functional-interface)
2. [Annotation @FunctionalInterface](#annotation-functionalinterface)
3. [Common Java 8 Functional Interfaces](#common-java-8-functional-interfaces)
4. [Custom Functional Interfaces](#custom-functional-interfaces)
5. [Examples with Lambdas](#examples-with-lambdas)
6. [Method References](#method-references)
7. [Streams and Functional Interfaces](#streams-and-functional-interfaces)
8. [Daily Life Uses](#daily-life-uses)
9. [Conclusion](#conclusion)

---

## What is a Functional Interface? 💡

A **Functional Interface** is an interface with exactly **one abstract method**.
It can be used with **Lambda expressions** to represent a single behavior concisely.

**Example:**

```java
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b);
}

Calculator addition = (a, b) -> a + b;
System.out.println(addition.calculate(5, 3)); // 8
```

![Functional Interface Concept](https://i.imgur.com/Blh4q1k.png)

---

## Annotation @FunctionalInterface 🏷️

* The `@FunctionalInterface` annotation **ensures** that the interface has exactly one abstract method.
* Optional, but recommended for clarity and compiler validation.

```java
@FunctionalInterface
interface Printer {
    void print(String message);
}
```

---

## Common Java 8 Functional Interfaces 🔧

| Interface    | Description                              | Method Signature    |
| ------------ | ---------------------------------------- | ------------------- |
| `Runnable`   | Represents a task with no input/output   | `void run()`        |
| `Callable`   | Returns a result and may throw exception | `V call()`          |
| `Consumer`   | Accepts a single input, returns nothing  | `void accept(T t)`  |
| `Supplier`   | Provides a result without input          | `T get()`           |
| `Function`   | Accepts input, returns output            | `R apply(T t)`      |
| `Predicate`  | Tests a condition on input               | `boolean test(T t)` |
| `BiFunction` | Accepts two inputs, returns output       | `R apply(T t, U u)` |

---

## Custom Functional Interfaces ✨

You can define your own functional interface for specific tasks:

```java
@FunctionalInterface
interface StringModifier {
    String modify(String s);
}

StringModifier toUpper = s -> s.toUpperCase();
System.out.println(toUpper.modify("hello")); // HELLO
```

---

## Examples with Lambdas 📝

**1. Consumer Example**

```java
Consumer<String> printer = message -> System.out.println("Message: " + message);
printer.accept("Hello World");
```

**2. Supplier Example**

```java
Supplier<Double> randomValue = () -> Math.random();
System.out.println(randomValue.get());
```

**3. Function Example**

```java
Function<String, Integer> stringLength = s -> s.length();
System.out.println(stringLength.apply("Java")); // 4
```

**4. Predicate Example**

```java
Predicate<Integer> isEven = n -> n % 2 == 0;
System.out.println(isEven.test(10)); // true
```

![Functional Interfaces Examples](https://i.imgur.com/8rzgYgR.png)

---

## Method References 🔗

Method references can simplify functional interfaces:

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Using Consumer with method reference
names.forEach(System.out::println);
```

---

## Streams and Functional Interfaces 🌊

Streams use functional interfaces extensively:

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// Filter even numbers using Predicate
List<Integer> evens = numbers.stream()
                             .filter(n -> n % 2 == 0)
                             .toList();
System.out.println(evens); // [2, 4]

// Transform using Function
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .toList();
System.out.println(squares); // [1, 4, 9, 16, 25]
```

---

## Daily Life Uses 🛠️

1. **Event Handling:** Lambda expressions simplify GUI event listeners.
2. **Data Transformation:** Functional interfaces are used in Streams for mapping and filtering data.
3. **Configuration Callbacks:** APIs use Consumer, Supplier, or Function for flexible callbacks.
4. **Concurrent Programming:** Runnable and Callable simplify multithreaded tasks.
5. **Validation & Testing:** Predicate interfaces for business rules and checks.

---

## Conclusion ✅

Functional interfaces are **the backbone of Lambda expressions in Java 8**.
They enable **cleaner, concise, and functional programming**, especially when combined with **Streams** and **method references**.

Mastering functional interfaces will make your Java code **more readable, reusable, and maintainable**.

```}
```
