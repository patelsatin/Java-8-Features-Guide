# Java 8 — Introduction & Functional Programming Basics

## 1. Why Java 8?
Java 8 was a landmark release that introduced functional programming concepts into Java. It bridged the gap between traditional OOP and modern functional paradigms.

## 2. What is Functional Programming?
- Treats functions as first-class citizens.
- Focuses on *what to do*, not *how to do*.
- Encourages immutability, statelessness, and pure functions.

## 3. Key Benefits
- Concise and expressive code.
- Parallelism support with Streams API.
- Better readability and maintainability.

## 4. Example
```java
List<Integer> numbers = Arrays.asList(1,2,3,4,5);
numbers.stream()
       .filter(n -> n % 2 == 0)
       .map(n -> n * n)
       .forEach(System.out::println);
```

## 5. Practice Questions
1. What are pure functions? Give an example in Java.
2. Write a program using `for-each` loop and then refactor using Streams.
