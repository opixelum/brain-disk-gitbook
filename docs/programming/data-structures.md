# Data Structures

## Arrays

- Fixed-size, indexed collection of elements;
- Elements are of the same type;
- Index starts at 0.

```java
int[] myArray = new int[5];
```

## Hash Map

- Stores key-value pairs;
- Allows for fast lookups;
- Also known as associative array, dictionary, or map.

```python
my_dict = {'key1': 'value1', 'key2': 'value2'}
```

## Struct

- Custom data type grouping variables under a single name;
- Used to group variables of different data types.

```c
struct Person {
    char name[50];
    int age;
    float salary;
};
```

## Linked List

- Dynamic data structure consisting of nodes;
- Each node contains an element and a reference to the next node;
- Allows for efficient insertion and deletion of elements.

```c
struct Node {
    int data;
    struct Node *next;
};
```

## Set

- Unordered collection of unique elements;
- No duplicate elements allowed.

```python
my_set = {1, 2, 3}
```

## Tuple

- Immutable, ordered collection of elements;
- Elements can be of different types;
- Allows for duplicate elements.

```python
my_tuple = (1, 'text', 3.14)
```