# C

## Introduction

## Types

## Conditional

## Iteration

## Memory management

### Pointers

A pointer is a variable that stores a memory location (or an address of a
variable).

```c
datatype *ptr_name;
```

Example:

```c
int *ptr;
```

### Operators

#### * (asterisk)

The unary operator **\* (asterisk)** is used for two things:

- To declare a pointer variable (see example above);
- To access the value stored in a pointer. This is called **"deferencing"**.

#### & (ampersand)

To get the address of a variable, we use the unary operator **& (ampersand)**.
For example, **&x** gives us the **address of variable x**.

Example:

```c
int x = 5; // variable declaration
int *ptr; // pointer declaration
ptr = &x; // pointer assignment
printf("%d", *ptr); // prints 5 by dereferencing ptr
```

## Functions

## Structures

## Multi-file
