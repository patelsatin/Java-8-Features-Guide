# Lambda Expressions in Java 8 🚀

Java 8 introduced **Lambda Expressions**, a major feature that allows us to write **concise and functional-style code**. Lambda expressions enable you to treat functionality as a method argument or treat code as data.

---

## Table of Contents

1. [What is a Lambda Expression?](#what-is-a-lambda-expression)
2. [Syntax of Lambda Expressions](#syntax-of-lambda-expressions)
3. [Functional Interfaces](#functional-interfaces)
4. [Basic Examples](#basic-examples)
5. [Lambda with Collections](#lambda-with-collections)
6. [Advanced Lambda Concepts](#advanced-lambda-concepts)
7. [Method References](#method-references)
8. [Streams and Lambda Expressions](#streams-and-lambda-expressions)
9. [Practical/Daily Life Uses](#practicaldaily-life-uses)
10. [Conclusion](#conclusion)

---

## What is a Lambda Expression? 💡

A **Lambda Expression** is an **anonymous function** (a function without a name) that can be passed around as a parameter or used to define inline behavior.
It helps reduce boilerplate code, especially when using interfaces with a single abstract method.

**Example (Java 7 vs Java 8):**

```java
// Java 7
Runnable r1 = new Runnable() {
    @Override
    public void run() {
        System.out.println("Hello World!");
    }
};
r1.run();

// Java 8 (Lambda)
Runnable r2 = () -> System.out.println("Hello World!");
r2.run();
```

![Lambda Concept](https://i.imgur.com/3XlOQG6.png)

---

## Syntax of Lambda Expressions ✍️

The general syntax is:

```
(parameters) -> expression
or
(parameters) -> { statements; }
```

**Rules:**

1. Parentheses are optional if there's **only one parameter**.
2. Curly braces are optional if the body has **only one statement**.
3. The compiler infers the return type.

**Examples:**

```java
// No parameters
() -> System.out.println("No parameters");

// Single parameter
x -> x * x

// Multiple parameters
(x, y) -> x + y

// Multiple statements
(x, y) -> {
    System.out.println("Adding numbers");
    return x + y;
}
```

---

## Functional Interfaces 🔧

A **Functional Interface** is an interface with **only one abstract method**.
Lambda expressions can be used to instantiate functional interfaces.

**Common Java 8 Functional Interfaces:**

| Interface    | Method Signature          |
| ------------ | ------------------------- |
| `Runnable`   | `void run()`              |
| `Callable`   | `V call()`                |
| `Comparator` | `int compare(T o1, T o2)` |
| `Consumer`   | `void accept(T t)`        |
| `Supplier`   | `T get()`                 |
| `Function`   | `R apply(T t)`            |
| `Predicate`  | `boolean test(T t)`       |

**Example using `Predicate`:**

```java
Predicate<Integer> isEven = n -> n % 2 == 0;
System.out.println(isEven.test(4)); // true
```

![Functional Interface](https://i.imgur.com/Blh4q1k.png)

---

## Basic Examples 📝

**1. Using Runnable:**

```java
Runnable r = () -> System.out.println("Lambda Runnable");
r.run();
```

**2. Using Comparator:**

```java
List<String> names = Arrays.asList("John", "Alice", "Bob");

Collections.sort(names, (a, b) -> a.compareTo(b));
System.out.println(names); // [Alice, Bob, John]
```

**3. Using Consumer:**

```java
List<String> list = Arrays.asList("Java", "Python", "C++");
list.forEach(item -> System.out.println(item));
```

---

## Lambda with Collections 📚

**1. Iterating a list**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.forEach(n -> System.out.println(n));
```

**2. Filtering a list**

```java
List<Integer> evenNumbers = numbers.stream()
                                   .filter(n -> n % 2 == 0)
                                   .toList();
System.out.println(evenNumbers); // [2, 4]
```

**3. Transforming a list**

```java
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .toList();
System.out.println(squares); // [1, 4, 9, 16, 25]
```

![Collections](https://i.imgur.com/R0BfZ1d.png)

---

## Advanced Lambda Concepts ⚡

**1. Capturing variables (effectively final)**

```java
int factor = 2;
List<Integer> multiplied = numbers.stream()
                                  .map(n -> n * factor)
                                  .toList();
System.out.println(multiplied); // [2, 4, 6, 8, 10]
```

**2. Lambda with multiple statements**

```java
Consumer<String> greet = name -> {
    String message = "Hello " + name;
    System.out.println(message);
};
greet.accept("Alice");
```

**3. Composing Functions**

```java
Function<Integer, Integer> multiplyBy2 = x -> x * 2;
Function<Integer, Integer> add3 = x -> x + 3;

Function<Integer, Integer> combined = multiplyBy2.andThen(add3);
System.out.println(combined.apply(5)); // 13
```

---

## Method References 🔗

A **method reference** is a shorthand for a lambda that calls a method.

**Types of Method References:**

1. **Static method reference:** `ClassName::staticMethod`
2. **Instance method reference of an object:** `instance::method`
3. **Instance method reference of a class:** `ClassName::instanceMethod`
4. **Constructor reference:** `ClassName::new`

**Examples:**

```java
// Static method reference
List<String> list = Arrays.asList("a", "b", "c");
list.forEach(System.out::println);

// Instance method reference
String prefix = "Hello ";
Function<String, String> greeter = prefix::concat;
System.out.println(greeter.apply("World")); // Hello World

// Constructor reference
Supplier<List<String>> listSupplier = ArrayList::new;
List<String> newList = listSupplier.get();
```

![Method References](https://i.imgur.com/ojJ28rQ.png)

---

## Streams and Lambda Expressions 🌊

Lambda expressions are commonly used with **Streams** for functional-style programming.

**Examples:**

```java
List<String> names = Arrays.asList("John", "Alice", "Bob");

// Filter and sort
List<String> filtered = names.stream()
                             .filter(n -> n.startsWith("A"))
                             .sorted()
                             .toList();
System.out.println(filtered); // [Alice]

// Sum using reduce
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
int sum = numbers.stream()
                 .reduce(0, (a, b) -> a + b);
System.out.println(sum); // 10
```

![Streams](https://i.imgur.com/Zo3iHc7.png)

---

## Practical/Daily Life Uses 🛠️

1. **Event Handling:**
   Lambda expressions reduce verbosity in GUI frameworks like Swing or JavaFX.

   ```java
   button.addActionListener(e -> System.out.println("Button clicked!"));
   ```

2. **Sorting/Filtering Collections:**
   Example: Sorting users by age or filtering products by price.

3. **Concurrent Programming:**
   Using lambdas with `Runnable` or `Callable` for threads.

4. **Data Processing:**
   Use with Streams for filtering, mapping, and aggregating data efficiently.

5. **Functional Interfaces in APIs:**
   Many Java 8 APIs accept lambdas for configuration or callbacks.

---

## Conclusion ✅

Lambda expressions in Java 8 are powerful tools for writing concise and expressive code.
They encourage **functional programming**, reduce boilerplate code, and are widely used with **Streams**, **Collections**, and **event-driven programming**.

Mastering them will make your Java code **cleaner, more readable, and more maintainable**.

```
```
