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

### Dynamic memory allocation

#### malloc()

Allocate memory in the heap.

```c
type *ptr = (type*) malloc(byte_size * sizeof *ptr)
```

Example:

```c
int *ptr = (int*) malloc(10 * sizeof *ptr);
```

#### calloc()

Allocate memory in the heap and initialize it to zero.

```c
type *ptr = (type*) calloc(num_elements, element_size)
```

Example:

```c
int *ptr = (int*) calloc(10, sizeof *ptr);
```

#### realloc()

Reallocate memory in the heap.

```c
type *ptr = (type*) realloc(ptr, new_size)
```

Example:

```c
int *ptr = (int*) malloc(10 * sizeof *ptr);
ptr = (int*) realloc(ptr, 20 * sizeof ptr);
```

#### free()

Free memory in the heap.

```c
free(ptr)
```

### Tips

- Always check if allocation was successful:

```c
int *ptr = (int*) malloc(10 * sizeof *ptr);
if (!ptr)
{
    fprintf(stderr, "Memory allocation failed");
    exit(EXIT_FAILURE);
}
```

- It must be as mallocs or callocs as frees;
- Don't forget to count the null terminator when allocating memory for strings.

## Functions

## Structures

## Multi-file
