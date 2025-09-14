# Java 8 Minor Enhancements 🛠️

Java 8 introduced several **minor enhancements** to improve code readability, performance, and usability. These include **new String methods, numeric operations, annotations, and more**.

---

## Table of Contents

1. [String Enhancements](#string-enhancements)
2. [New Numeric Methods](#new-numeric-methods)
3. [Optional Enhancements](#optional-enhancements)
4. [Type Annotations](#type-annotations)
5. [Base64 Encoding/Decoding](#base64-encodingdecoding)
6. [Examples](#examples)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## String Enhancements ✨

Java 8 added **useful methods** in `String` class:

* `lines()` → Stream of lines
* `strip()`, `stripLeading()`, `stripTrailing()` → Remove whitespaces
* `repeat(int n)` → Repeat string n times

```java
String text = "  Hello World  ";
System.out.println(text.strip()); // "Hello World"
System.out.println("abc\ndef".lines().count()); // 2
System.out.println("Hi! ".repeat(3)); // Hi! Hi! Hi! 
```

---

## New Numeric Methods 🔢

`Integer` and `Long` classes got new utility methods:

* `Integer.sum(a, b)` → Sum of two integers
* `Integer.max(a, b)` → Max of two integers
* `Integer.min(a, b)` → Min of two integers
* `Math.addExact(a, b)` → Throws exception on overflow

```java
System.out.println(Integer.sum(5, 10)); // 15
System.out.println(Integer.max(5, 10)); // 10
```

---

## Optional Enhancements 🛡️

Optional got new methods:

* `ifPresentOrElse()` → Run action if value present or alternative if empty
* `or()` → Provide alternative Optional

```java
Optional<String> opt = Optional.ofNullable(null);
opt.ifPresentOrElse(System.out::println, () -> System.out.println("No value"));
```

---

## Type Annotations 🏷️

* Java 8 allows **annotations on types** (`@NonNull`, `@Nullable`) for better **static analysis**.

```java
public void process(@NonNull String input) {}
```

---

## Base64 Encoding/Decoding 🔐

Java 8 introduced `java.util.Base64` for **encoding and decoding**:

```java
String original = "Hello Java 8";
String encoded = Base64.getEncoder().encodeToString(original.getBytes());
String decoded = new String(Base64.getDecoder().decode(encoded));
System.out.println(encoded);
System.out.println(decoded);
```

---

## Examples 📝

**1. Strip and Repeat**

```java
String text = "  Java 8  ";
System.out.println(text.strip().repeat(2)); // Java 8Java 8
```

**2. Optional ifPresentOrElse**

```java
Optional<String> opt = Optional.ofNullable("Hi");
opt.ifPresentOrElse(System.out::println, () -> System.out.println("Empty"));
```

**3. Base64 Encoding**

```java
String secret = "password";
String encoded = Base64.getEncoder().encodeToString(secret.getBytes());
System.out.println(encoded);
```

---

## Daily Life Uses 🛠️

1. **String formatting and processing**.
2. **Numeric calculations with overflow safety**.
3. **Safe optional handling**.
4. **Data encoding for web communication**.
5. **Annotations for better static analysis and documentation**.

---

## Conclusion ✅

These **minor enhancements in Java 8** improve **developer productivity** and **code readability**.
They complement major features like **Lambda, Streams, and Date-Time API** for **more expressive and concise coding**.
