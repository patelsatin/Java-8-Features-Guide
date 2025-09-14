# Java 8 Date-Time API 📅

Java 8 introduced a new **Date-Time API** (`java.time`) to replace the old `java.util.Date` and `java.util.Calendar`. It is **thread-safe, immutable**, and provides **better API for date-time operations**.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Core Classes](#core-classes)
3. [Creating Date-Time Objects](#creating-date-time-objects)
4. [Formatting and Parsing](#formatting-and-parsing)
5. [Date-Time Manipulations](#date-time-manipulations)
6. [Examples](#examples)
7. [Daily Life Uses](#daily-life-uses)
8. [Conclusion](#conclusion)

---

## Introduction 💡

The old `Date` and `Calendar` classes had **thread-safety issues, mutability, and poor API design**. The new **java.time** API resolves these problems.

---

## Core Classes 🔧

| Class               | Description                             |
| ------------------- | --------------------------------------- |
| `LocalDate`         | Date without time (YYYY-MM-DD)          |
| `LocalTime`         | Time without date (HH\:MM\:SS)          |
| `LocalDateTime`     | Date + Time without timezone            |
| `ZonedDateTime`     | Date + Time + Timezone                  |
| `Instant`           | Timestamp from epoch                    |
| `Duration`          | Time-based amount (hours, minutes)      |
| `Period`            | Date-based amount (days, months, years) |
| `DateTimeFormatter` | Format and parse date-time              |

---

## Creating Date-Time Objects 🛠️

```java
LocalDate date = LocalDate.now();
LocalTime time = LocalTime.now();
LocalDateTime dateTime = LocalDateTime.now();
ZonedDateTime zoned = ZonedDateTime.now();
Instant timestamp = Instant.now();

// Specific date/time
LocalDate birthday = LocalDate.of(1990, Month.JANUARY, 1);
LocalTime meeting = LocalTime.of(14, 30);
```

---

## Formatting and Parsing ✨

```java
LocalDate date = LocalDate.now();
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");

String formatted = date.format(formatter);
System.out.println(formatted); // 14/09/2025

// Parsing
LocalDate parsedDate = LocalDate.parse("14/09/2025", formatter);
System.out.println(parsedDate); // 2025-09-14
```

---

## Date-Time Manipulations 🔄

```java
LocalDate today = LocalDate.now();
LocalDate tomorrow = today.plusDays(1);
LocalDate lastWeek = today.minusWeeks(1);

LocalDate nextMonth = today.plusMonths(1);

// Combining date and time
LocalDateTime dateTime = LocalDateTime.of(today, LocalTime.of(10, 30));

// Duration and Period
Duration duration = Duration.between(LocalTime.of(9, 0), LocalTime.of(17, 0));
System.out.println(duration.toHours()); // 8

Period period = Period.between(LocalDate.of(1990,1,1), today);
System.out.println(period.getYears()); // Age in years
```

---

## Examples 📝

**1. Compare Dates**

```java
LocalDate d1 = LocalDate.of(2025, 9, 14);
LocalDate d2 = LocalDate.of(2025, 12, 25);
System.out.println(d1.isBefore(d2)); // true
System.out.println(d1.isAfter(d2)); // false
```

**2. Zoned Date-Time**

```java
ZonedDateTime zonedNY = ZonedDateTime.now(ZoneId.of("America/New_York"));
System.out.println(zonedNY);
```

**3. Adding/Subtracting Period**

```java
LocalDate nextBirthday = LocalDate.of(2025, Month.JANUARY, 1);
LocalDate reminder = nextBirthday.minusDays(7);
System.out.println(reminder); // 2024-12-25
```

---

## Daily Life Uses 🛠️

1. **Scheduling applications** (meetings, reminders).
2. **Age calculation**.
3. **Time zone conversions**.
4. **Data analytics and timestamps**.
5. **Formatting date-time for UI/Reports**.

---

## Conclusion ✅

The **Java 8 Date-Time API** is **thread-safe, immutable, and easy to use**.
It replaces old APIs and allows **better control, formatting, and manipulation** of dates and times.
