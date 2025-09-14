# Java 8 Nashorn JavaScript Engine 🖥️

Java 8 introduced the **Nashorn JavaScript Engine**, which allows Java applications to **run JavaScript code** on the JVM. Nashorn **replaces the old Rhino engine** and provides **better performance and integration** with Java.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Nashorn Engine](#getting-nashorn-engine)
3. [Executing JavaScript](#executing-javascript)
4. [Passing Data Between Java and JS](#passing-data-between-java-and-js)
5. [Examples](#examples)
6. [Daily Life Uses](#daily-life-uses)
7. [Conclusion](#conclusion)

---

## Introduction 💡

Nashorn allows **embedding JavaScript code** within Java applications.
It can execute scripts, call Java methods from JS, and vice versa.

```java
import javax.script.ScriptEngine;
import javax.script.ScriptEngineManager;
import javax.script.ScriptException;

public class NashornExample {
    public static void main(String[] args) throws ScriptException {
        ScriptEngine engine = new ScriptEngineManager().getEngineByName("nashorn");
        engine.eval("print('Hello from JavaScript!')");
    }
}
```

---

## Getting Nashorn Engine 🔧

```java
ScriptEngineManager manager = new ScriptEngineManager();
ScriptEngine engine = manager.getEngineByName("nashorn");
```

* Returns a `ScriptEngine` object to execute JS code.
* Requires **Java 8+**.

---

## Executing JavaScript ✨

```java
engine.eval("var x = 10; var y = 20; print(x + y);"); // 30
```

* Use `eval()` to execute scripts.
* You can define functions and variables.

---

## Passing Data Between Java and JS 🔄

**1. From Java to JS**

```java
engine.put("num", 5);
engine.eval("print(num * 2)"); // 10
```

**2. From JS to Java**

```java
Object result = engine.eval("var a = 10; var b = 20; a + b;");
System.out.println(result); // 30
```

**3. Invoking Java Methods from JS**

```java
engine.eval("var System = Java.type('java.lang.System'); System.out.println('Hello from JS');");
```

---

## Examples 📝

**1. JavaScript function execution**

```java
engine.eval("function sum(a, b) { return a + b; } print(sum(5, 3));"); // 8
```

**2. Using Java Collections in JS**

```java
import java.util.*;
engine.put("list", new ArrayList<>());
engine.eval("list.add('Java'); list.add('JS'); print(list); "); // [Java, JS]
```

**3. Complex script with loops**

```java
engine.eval("for(var i=0;i<3;i++){ print('Iteration ' + i); }");
```

---

## Daily Life Uses 🛠️

1. **Scripting support** in Java applications.
2. **Embedding dynamic logic** without recompiling Java code.
3. **Integration with legacy JavaScript libraries**.
4. **Quick prototyping** of logic using JS.
5. **Automation and dynamic configuration**.

---

## Conclusion ✅

Nashorn in Java 8 provides a **fast and integrated JavaScript engine** for JVM.
It allows **embedding, executing, and integrating JS code** directly in Java applications.

Perfect for \*\*dynamic scripting, automation, and hybrid application
