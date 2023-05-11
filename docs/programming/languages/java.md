# Java

## Description

- General-purpose programming language;
- Object-oriented;
- Runs on a virtual machine (JVM), so it's cross-platform;
- Compiled to bytecode, which is then executed by the JVM.

## History

- Created by Sun Microsystems in 1995;
- Open source since 2006;
- Acquired by Oracle in 2010.

## Principles

1. It must be simple, object-oriented, and familiar;
2. It must be robust and secure;
3. It must be architecture-neutral and portable;
4. It must execute with high performance;
5. It must be interpreted, threaded, and dynamic.

## Usage

- Android apps;
- Desktop apps;
- Client-server web apps.

## Inheritance

- Inherit from a class using the `extends` keyword;
- `final` classes cannot be extended;
- Every class in Java inherits from `Object`;
- Multiple inheritance is not supported.

### Constructors in inheritance

- If parent hasn't any constructor, child can define its own or not;
- If no constructor is defined in both, the default constructor of each class is
  called;
- If parent has one or more constructors, child must define at least one
  constructor, and it must call one of the parent's constructors using the
  `super` keyword.

### Overriding methods

- Use the `@Override` annotation to override a method.

```java
public class Child extends Parent {
  @Override
  public void method() {
    // method() is already defined in Parent. We're overriding it.
  }
}
```

## Error & Exception handling

Although it's safer to handle errors and exceptions, it slows down the program.
So, it's better to handle only the exceptions that are likely to occur.

### Checked & unchecked exceptions

- Checked exceptions are exceptions that must be handled by the programmer;
- Unchecked exceptions are exceptions that don't need to be handled by the
  programmer.

### Error

- Exceptional conditions that are external to the application, and that the
  application usually cannot anticipate or recover from;
- Examples: JVM running out of memory, stack overflow, etc.
- Errors are unchecked.
- Errors are not meant to be caught or handled (although it's possible).

### Exception

- Exceptional conditions that are internal to the application, and that the
  application should anticipate and recover from;
- Examples: invalid user input, file not found, network connection lost, etc.
- Exceptions are checked.

### RuntimeException

- Exceptions that can be thrown anywhere in the code;
- Examples: `NullPointerException`, `IndexOutOfBoundsException`, etc.
- RuntimeExceptions are unchecked.
- RuntimeExceptions are not meant to be caught or handled (although it's
  possible).

### Errors & Exceptions hierarchy

![Errors & Exceptions hierarchy](../../.gitbook/assets/programming/languages/java/errors-exceptions-hierarchy.png)

### try-catch-finally

```java
try {
  // Code that may throw an exception
} catch (Exception e) {
  // Code that handles the exception
} finally {
  // Code that always runs
}
```

## Collections

### List

- Ordered collection of elements;
- Implemented by:
  - `ArrayList`: Resizable array;
  - `LinkedList`: Doubly-linked list;
  - `Vector`: Thread-safe resizable array;
    - `Stack`: LIFO (last-in-first-out) collection.

### Set

- Unordered collection of unique elements;
- Implemented by:
  - `EnumSet`: Abstract class for sets of enum types;
  - `HashSet`: Hash table;
  - SortedSet: Interface for sorted sets;
    - `TreeSet`: Red-black tree.

## References

- [Java (programming language) - Wikipedia](https://en.wikipedia.org/wiki/Java_(programming_language))
- [Exceptions in Java - GeeksforGeeks](https://www.geeksforgeeks.org/exceptions-in-java/)
- Olivier Denier ([odenier@yakacoder.fr](mailto:odenier@yakacoder.fr))
