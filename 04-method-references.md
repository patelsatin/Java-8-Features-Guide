# Method References in Java 8 🔗

Java 8 introduced **Method References**, a shorthand notation of **Lambda Expressions** to refer to existing methods by name. They make code more **concise, readable, and expressive**.

---

## Table of Contents

1. [What is a Method Reference?](#what-is-a-method-reference)
2. [Types of Method References](#types-of-method-references)
3. [Syntax of Method References](#syntax-of-method-references)
4. [Examples](#examples)
5. [Method References with Collections](#method-references-with-collections)
6. [Streams and Method References](#streams-and-method-references)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## What is a Method Reference? 💡

A **Method Reference** is a **shortcut of a Lambda Expression** that executes an existing method.
It improves **code readability** by eliminating boilerplate.

**Example:**

```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

// Lambda expression
names.forEach(name -> System.out.println(name));

// Method reference
names.forEach(System.out::println);
```

![Method Reference Concept](https://i.imgur.com/ojJ28rQ.png)

---

## Types of Method References 🔧

1. **Static Method Reference:** `ClassName::staticMethod`
2. **Instance Method of Particular Object:** `instance::method`
3. **Instance Method of Arbitrary Object of a Class:** `ClassName::instanceMethod`
4. **Constructor Reference:** `ClassName::new`

---

## Syntax of Method References ✍️

| Type                                 | Syntax                      | Example               |
| ------------------------------------ | --------------------------- | --------------------- |
| Static Method Reference              | `ClassName::staticMethod`   | `Math::max`           |
| Instance Method of Particular Object | `instance::method`          | `myPrinter::print`    |
| Instance Method of Arbitrary Object  | `ClassName::instanceMethod` | `String::toUpperCase` |
| Constructor Reference                | `ClassName::new`            | `ArrayList::new`      |

---

## Examples 📝

**1. Static Method Reference**

```java
List<Integer> numbers = Arrays.asList(5, 2, 9, 1);
numbers.sort(Integer::compare);
System.out.println(numbers); // [1, 2, 5, 9]
```

**2. Instance Method of Particular Object**

```java
class Printer {
    void printMessage(String message) {
        System.out.println(message);
    }
}

Printer printer = new Printer();
List<String> messages = Arrays.asList("Hello", "World");
messages.forEach(printer::printMessage);
```

**3. Instance Method of Arbitrary Object of a Class**

```java
List<String> names = Arrays.asList("alice", "bob");
List<String> upper = names.stream()
                          .map(String::toUpperCase)
                          .toList();
System.out.println(upper); // [ALICE, BOB]
```

**4. Constructor Reference**

```java
Supplier<List<String>> listSupplier = ArrayList::new;
List<String> newList = listSupplier.get();
System.out.println(newList); // []
```

![Method Reference Examples](https://i.imgur.com/Zo3iHc7.png)

---

## Method References with Collections 📚

```java
List<String> fruits = Arrays.asList("Apple", "Banana", "Cherry");

// Sort using static method reference
fruits.sort(String::compareToIgnoreCase);
System.out.println(fruits); // [Apple, Banana, Cherry]

// Print using instance method reference
fruits.forEach(System.out::println);
```

---

## Streams and Method References 🌊

Method references are commonly used with **Streams** for functional-style operations:

```java
List<String> words = Arrays.asList("java", "lambda", "stream");

// Transform words to uppercase
List<String> upperWords = words.stream()
                               .map(String::toUpperCase)
                               .toList();
System.out.println(upperWords); // [JAVA, LAMBDA, STREAM]

// Print words
upperWords.forEach(System.out::println);
```

---

## Daily Life Uses 🛠️

1. **Printing or logging outputs** using `System.out::println`.
2. **Sorting collections** using `Comparator` static methods.
3. **Data transformation** in Streams using instance methods.
4. **Object creation** using constructor references.
5. **Event handling** in GUI frameworks using method references instead of lambdas.

---

## Conclusion ✅

Method References in Java 8 are **a concise, readable alternative to Lambdas**.
They make code cleaner, easier to maintain, and are heavily used in **Streams, Collections, and functional programming**.

Mastering method references will make your Java code **more expressive and elegant**.
