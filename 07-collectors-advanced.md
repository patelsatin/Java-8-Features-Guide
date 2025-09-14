# Java 8 Advanced Collectors 📦

Java 8 **Collectors** are used with the **Streams API** to **accumulate elements** into collections, aggregate results, or perform summarization. Advanced collectors make stream processing **more powerful and expressive**.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Basic Collectors](#basic-collectors)
3. [Advanced Collectors](#advanced-collectors)
4. [Grouping and Partitioning](#grouping-and-partitioning)
5. [Summarization and Joining](#summarization-and-joining)
6. [Examples](#examples)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## Introduction 💡

Collectors are **mutable reduction operations** that process elements of a stream and return **collections or aggregated results**.

**Example:**

```java
List<String> names = Arrays.asList("John", "Alice", "Bob");
List<String> nameList = names.stream().collect(Collectors.toList());
System.out.println(nameList); // [John, Alice, Bob]
```

---

## Basic Collectors 🔧

* `toList()` → Collect elements into a List
* `toSet()` → Collect elements into a Set
* `toMap()` → Collect elements into a Map

```java
List<String> list = names.stream().collect(Collectors.toList());
Set<String> set = names.stream().collect(Collectors.toSet());
Map<String, Integer> map = names.stream().collect(Collectors.toMap(name -> name, String::length));
```

---

## Advanced Collectors ✨

1. **Counting** → Count elements in a stream
2. **Summing** → Sum numerical elements
3. **Averaging** → Average numerical values
4. **Max/Min** → Find maximum or minimum values
5. **Joining** → Concatenate strings

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
long count = numbers.stream().collect(Collectors.counting());
int sum = numbers.stream().collect(Collectors.summingInt(Integer::intValue));
double avg = numbers.stream().collect(Collectors.averagingInt(Integer::intValue));
System.out.println(count + ", " + sum + ", " + avg); // 5, 15, 3.0
```

---

## Grouping and Partitioning 📊

**1. Grouping by a classifier**

```java
List<String> names = Arrays.asList("John", "Alice", "Bob", "Amanda");
Map<Integer, List<String>> groupedByLength = names.stream()
    .collect(Collectors.groupingBy(String::length));
System.out.println(groupedByLength); // {3=[Bob, John], 5=[Alice, Amanda]}
```

**2. Partitioning by a predicate**

```java
Map<Boolean, List<String>> partitioned = names.stream()
    .collect(Collectors.partitioningBy(name -> name.startsWith("A")));
System.out.println(partitioned); // {false=[John, Bob], true=[Alice, Amanda]}
```

---

## Summarization and Joining ✍️

**1. Summarization**

```java
IntSummaryStatistics stats = numbers.stream().collect(Collectors.summarizingInt(Integer::intValue));
System.out.println(stats); // IntSummaryStatistics{count=5, sum=15, min=1, average=3.000000, max=5}
```

**2. Joining Strings**

```java
String result = names.stream().collect(Collectors.joining(", "));
System.out.println(result); // John, Alice, Bob, Amanda
```

---

## Examples 📝

**1. Count names starting with 'A'**

```java
long countA = names.stream().filter(n -> n.startsWith("A")).count();
System.out.println(countA); // 2
```

**2. Grouping by first letter**

```java
Map<Character, List<String>> groupByFirstLetter = names.stream()
    .collect(Collectors.groupingBy(name -> name.charAt(0)));
System.out.println(groupByFirstLetter); // {J=[John], A=[Alice, Amanda], B=[Bob]}
```

**3. Sum of squares**

```java
int sumOfSquares = numbers.stream().map(n -> n * n).collect(Collectors.summingInt(Integer::intValue));
System.out.println(sumOfSquares); // 55
```

---

## Daily Life Uses 🛠️

1. **Generate reports** by grouping or summarizing data.
2. **Aggregate financial data** (sum, average).
3. **Concatenate or format strings** from a collection.
4. **Partition datasets** (e.g., adults vs minors).
5. **Collect statistics** for analytics or dashboards.

---

## Conclusion ✅

Advanced Collectors in Java 8 make **stream processing powerful and expressive**.
With grouping, partitioning, summarization, and joining, you can **manipulate and aggregate data efficiently** in a functional
