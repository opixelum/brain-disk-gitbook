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
