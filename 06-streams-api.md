# Java 8 Streams API 🌊

The **Streams API** in Java 8 allows you to process **collections in a functional and declarative style**. It supports operations like filtering, mapping, and reducing data.

---

## Table of Contents

1. [What is a Stream?](#what-is-a-stream)
2. [Stream Characteristics](#stream-characteristics)
3. [Creating Streams](#creating-streams)
4. [Intermediate Operations](#intermediate-operations)
5. [Terminal Operations](#terminal-operations)
6. [Examples](#examples)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## What is a Stream? 💡

A **Stream** is a sequence of elements supporting **functional-style operations**. Streams **do not store data**; they **operate on data sources** like collections, arrays, or I/O channels.

**Key Points:**

* Streams are **not data structures**.
* They **support pipelining**.
* Operations can be **lazy** and **parallelized**.

---

## Stream Characteristics 🔧

1. **No storage:** Streams do not store elements.
2. **Functional in nature:** Operations produce new streams.
3. **Laziness-seeking:** Computation happens only when necessary.
4. **Possibly unbounded:** Can be infinite streams.
5. **Consumable:** A stream can be consumed only once.

---

## Creating Streams 🛠️

```java
List<String> list = Arrays.asList("Java", "Lambda", "Stream");

// From Collection
Stream<String> stream1 = list.stream();

// Parallel Stream
Stream<String> parallelStream = list.parallelStream();

// From Array
Stream<Integer> stream2 = Arrays.stream(new Integer[]{1, 2, 3});

// Using Stream.of()
Stream<String> stream3 = Stream.of("a", "b", "c");

// Infinite Stream
Stream<Integer> infiniteStream = Stream.iterate(0, n -> n + 2);
```

![Stream Creation](https://i.imgur.com/Zo3iHc7.png)

---

## Intermediate Operations 🔄

* Produce **another stream**.
* **Lazy**, executed only when terminal operation is called.

**Common Intermediate Operations:**

* `filter()`
* `map()`
* `distinct()`
* `sorted()`
* `limit()`
* `skip()`

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .toList();
System.out.println(squares); // [1, 4, 9, 16, 25]
```

---

## Terminal Operations ✅

* Produce **result or side-effect**.
* **Trigger the execution** of stream pipeline.

**Common Terminal Operations:**

* `forEach()`
* `collect()`
* `reduce()`
* `count()`
* `anyMatch()`, `allMatch()`, `noneMatch()`
* `findFirst()`, `findAny()`

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

// Filter even numbers and collect
List<Integer> evens = numbers.stream()
                             .filter(n -> n % 2 == 0)
                             .toList();
System.out.println(evens); // [2, 4]

// Sum using reduce
int sum = numbers.stream()
                 .reduce(0, Integer::sum);
System.out.println(sum); // 15
```

---

## Examples 📝

**1. Filter and Map**

```java
List<String> names = Arrays.asList("John", "Alice", "Bob");
List<String> upperCaseNames = names.stream()
                                   .filter(name -> name.length() > 3)
                                   .map(String::toUpperCase)
                                   .toList();
System.out.println(upperCaseNames); // [JOHN, ALICE]
```

**2. Count and Match**

```java
long count = names.stream().filter(name -> name.startsWith("A")).count();
boolean anyStartsWithJ = names.stream().anyMatch(name -> name.startsWith("J"));
System.out.println(count); // 1
System.out.println(anyStartsWithJ); // true
```

**3. Parallel Stream Example**

```java
List<Integer> bigList = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
int sum = bigList.parallelStream().reduce(0, Integer::sum);
System.out.println(sum); // 55
```

---

## Daily Life Uses 🛠️

1. **Filtering lists** (e.g., users over 18).
2. **Mapping and transforming data** (e.g., converting product names to uppercase).
3. **Aggregating data** (sum, max, min).
4. **Parallel processing** large datasets efficiently.
5. **Data pipelines** in functional programming.

---

## Conclusion ✅

The **Streams API** in Java 8 enables **functional-style operations** on collections and other data sources.
Combining **intermediate and terminal operations** allows **powerful, concise, and parallelizable data processing**.
