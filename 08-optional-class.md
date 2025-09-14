# Java 8 Optional Class 🛡️

The **Optional** class in Java 8 is a **container object** which may or may not contain a non-null value. It helps to **avoid NullPointerExceptions** and promotes **cleaner, more expressive code**.

---

## Table of Contents

1. [What is Optional?](#what-is-optional)
2. [Creating Optional Objects](#creating-optional-objects)
3. [Checking Values](#checking-values)
4. [Retrieving Values](#retrieving-values)
5. [Transforming Values](#transforming-values)
6. [Examples](#examples)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## What is Optional? 💡

Optional is a **wrapper for a value** that may be **null**. It encourages **null-safe programming**.

```java
Optional<String> name = Optional.of("John");
Optional<String> emptyName = Optional.empty();
```

---

## Creating Optional Objects 🔧

```java
// Non-empty optional
Optional<String> opt1 = Optional.of("Hello");

// Optional that may be null
Optional<String> opt2 = Optional.ofNullable(null);

// Empty optional
Optional<String> opt3 = Optional.empty();
```

---

## Checking Values ✅

```java
if(opt1.isPresent()) {
    System.out.println("Value: " + opt1.get());
}

// Using ifPresent
opt1.ifPresent(value -> System.out.println("Value: " + value));
```

---

## Retrieving Values 🛠️

```java
// OrElse - default if value is absent
String result = opt2.orElse("Default");
System.out.println(result); // Default

// OrElseGet - using Supplier
String result2 = opt2.orElseGet(() -> "Generated Default");

// OrElseThrow - throw exception if absent
opt2.orElseThrow(() -> new RuntimeException("Value missing"));
```

---

## Transforming Values ✨

```java
Optional<String> optName = Optional.of("john");

// Map
Optional<String> upper = optName.map(String::toUpperCase);
upper.ifPresent(System.out::println); // JOHN

// Filter
Optional<String> filtered = optName.filter(n -> n.startsWith("J"));
System.out.println(filtered.isPresent()); // false
```

---

## Examples 📝

**1. Handling nullable values**

```java
String name = null;
Optional<String> opt = Optional.ofNullable(name);
System.out.println(opt.orElse("Default Name")); // Default Name
```

**2. Transforming with map**

```java
Optional<String> email = Optional.of("user@example.com");
Optional<String> domain = email.map(e -> e.substring(e.indexOf("@") + 1));
domain.ifPresent(System.out::println); // example.com
```

**3. Chaining Optionals**

```java
Optional<String> optional = Optional.ofNullable(null);
String value = optional.map(String::toUpperCase).orElse("N/A");
System.out.println(value); // N/A
```

---

## Daily Life Uses 🛠️

1. **Avoid NullPointerException** in business logic.
2. **Return optional values** from database queries or APIs.
3. **Chaining operations** safely without null checks.
4. **Default values** for missing inputs.
5. **Cleaner code** in configuration or properties reading.

---

## Conclusion ✅

The **Optional class** promotes **null-safe programming**, making your code more readable, maintainable, and less error-prone.
It is a **must-use tool** for Java 8 and beyond to handle **potentially absent values**.
