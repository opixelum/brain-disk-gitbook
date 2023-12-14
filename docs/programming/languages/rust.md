# Rust

## `String` vs `str`

- `String` is a **mutable**, **growable** heap-allocated string, implemented by
  a struct wrapping a `Vec<u8>`.
- `str` is an **immutable**, **fixed length** string slice.

## Traits

- Collection of methods;
- Contains functions declarations & default implementations;
- Can be implemented by any type.

```rust
trait Animal {
    // Method declarations
    fn new(name: &'static str) -> Self;
    
    // Method definitions with default implementation
    fn move(&self, destination: &'static str) {
        println!("{} moves to {}", self.name, destination);
    }
}

struct Horse {
    name: &'static str,
}

impl Animal for Horse {
    // Define the methods declared in the trait
    fn new(name: &'static str) -> Horse {
        Horse { name: name }
    }
    
    // Override the default implementation
    fn move(&self, destination: &'static str) {
        println!("{} gallops to {}", self.name, destination);
    }
}
```

## Generics

- Define any data type, or ones implementing one or more traits;
- Specified inside angle brackets (`<>`);
- Can be used in structs, enums, functions, methods, and impl blocks.

```rust
// Any type
struct Point<T> {
    x: T,
    y: T,
}

// `impl<T>` is required to use `T` in the following block
impl<T> Point<T> {
    fn new(x: T, y: T) -> Self {
        Point { x, y }
    }
}

// Only types implementing the `Ord` trait
fn sort<T: Ord>(list: &mut [T]) {
    // ...
}

// Multiple generic types
enum ComputationResult<T, E> {
    Success(T),
    Failure(E),
}
```
