# Default and Static Methods in Java 8 🛠️

Java 8 introduced **default** and **static methods** in interfaces. These methods allow **interfaces to have behavior**, not just abstract method declarations, making it easier to **evolve interfaces without breaking implementations**.

---

## Table of Contents

1. [Default Methods](#default-methods)
2. [Static Methods](#static-methods)
3. [Syntax](#syntax)
4. [Examples](#examples)
5. [Multiple Inheritance with Default Methods](#multiple-inheritance-with-default-methods)
6. [Streams and Default/Static Methods](#streams-and-defaultstatic-methods)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## Default Methods 💡

* A **default method** is a method in an interface with a **default implementation**.
* Implementing classes can **use or override** it.
* Introduced to allow **interface evolution** without breaking existing classes.

**Syntax:**

```java
interface Vehicle {
    void start(); // abstract method

    default void honk() {
        System.out.println("Beep Beep!");
    }
}
```

**Example:**

```java
class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car started");
    }
}

Car car = new Car();
car.start(); // Car started
car.honk();  // Beep Beep!
```

![Default Methods](https://i.imgur.com/0J6i2aE.png)

---

## Static Methods 🔧

* A **static method** in an interface belongs to the interface itself.
* Cannot be overridden by implementing classes.
* Can be called using `InterfaceName.methodName()`.

**Syntax:**

```java
interface Calculator {
    static int add(int a, int b) {
        return a + b;
    }
}

System.out.println(Calculator.add(5, 3)); // 8
```

![Static Methods](https://i.imgur.com/2rLMX9u.png)

---

## Syntax 📜

| Method Type    | Keyword   | Description                           |
| -------------- | --------- | ------------------------------------- |
| Default Method | `default` | Provides implementation in interface  |
| Static Method  | `static`  | Interface-level method, not inherited |

---

## Examples 📝

**1. Default Method Example**

```java
interface Printer {
    default void printHello() {
        System.out.println("Hello from interface!");
    }
}

class MyPrinter implements Printer {}

MyPrinter printer = new MyPrinter();
printer.printHello(); // Hello from interface!
```

**2. Static Method Example**

```java
interface MathUtils {
    static int square(int n) {
        return n * n;
    }
}

System.out.println(MathUtils.square(5)); // 25
```

---

## Multiple Inheritance with Default Methods ⚖️

If a class implements multiple interfaces with the same default method, it must **override it**:

```java
interface A {
    default void show() { System.out.println("A"); }
}
interface B {
    default void show() { System.out.println("B"); }
}

class C implements A, B {
    @Override
    public void show() {
        A.super.show(); // or B.super.show()
    }
}

C obj = new C();
obj.show(); // A
```

![Default Method Conflict](https://i.imgur.com/fzj1Sc8.png)

---

## Streams and Default/Static Methods 🌊

Default and static methods can be combined with Streams:

```java
interface StringUtils {
    static boolean isEmpty(String s) {
        return s == null || s.isEmpty();
    }

    default String addExclamation(String s) {
        return s + "!";
    }
}

class MyStringUtils implements StringUtils {}

List<String> words = Arrays.asList("Java", "Lambda");
MyStringUtils utils = new MyStringUtils();

List<String> excitedWords = words.stream()
                                 .map(utils::addExclamation)
                                 .toList();
System.out.println(excitedWords); // [Java!, Lambda!]
```

---

## Daily Life Uses 🛠️

1. **Library/API evolution:** Add methods to interfaces without breaking old implementations.
2. **Default behavior:** Provide common functionality that can be overridden.
3. **Utility methods:** Static methods in interfaces for reusable helper methods.
4. **Streams and data transformations:** Combine default methods with Stream operations.
5. **Event handling defaults:** Interfaces for listeners with optional default implementations.

---

## Conclusion ✅

Default and static methods in Java 8 make interfaces **more powerful and flexible**.
They enable **interface evolution**, reusable utility methods, and cleaner code when used with **Lambda expressions and Streams**.

Mastering these features improves **code maintainability and readability**.
