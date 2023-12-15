# Rust

## Derive

- Derive is an [attribute](#attribute);
- Automatically implements some traits for a type, saving us from writing
  boilerplate code.

```rust
#[derive(PartialEq)]
struct Foo<T> {
    a: i32,
    b: T,
}
```

This is equivalent to:

```rust
impl<T: PartialEq> PartialEq for Foo<T> {
    fn eq(&self, other: &Foo<T>) -> bool {
        self.a == other.a && self.b == other.b
    }
}
```

## `enum` vs `struct`

- Enums are types that always result in one of a few variants (like an `OR`);
- Structs are types that each instance can have different properties (like an
  `AND`);
- Enums are useful for match statements, structs are useful for storing data.

```rust
enum MessageStatus {
    Read,
    Unread,
    Deleted,
}

struct Message {
    status: MessageStatus,
    content: String,
}

fn main() {
    // `message` = `Message` struct instance containing multiple properties
    let message = Message {
        // `status` is either `Read` or `Unread`
        status: MessageStatus::Unread,
        content: String::from("Hello, world!"),
    };
    
    // Every variant of an enum should be evaluated in a match statement
    match message.status {
        MessageStatus::Read => println!("Message read"),
        MessageStatus::Unread => println!("Message unread"),
        MessageStatus::Deleted => println!("Message deleted"),
    }
    
    // A catch-all match statement can be used to ignore some variants
    match message.status {
        MessageStatus::Read => println!("Message read"),
        // Ignore `Unread` & `Deleted` variants
        _ => println!("Unknown behavior"),
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

## Lifetime

- Lifetime is the scope for which a variable is valid;
- A single quote (`'`) is used to specify the lifetime of a variable;
- Can be generic (declared like a generic type);
- If not explicitly declared, the compiler infers the lifetime of a variable
  (implicit).

```rust
// `plate` cannot live longer than `car` (explicit)
struct Car<'a> {
    plate: &'a str,
    max_speed: u32,
}

fn main() {
    let car = Car { plate: "ABC123", max_speed: 200 };
    println!("{}", car.plate);
    
    // `message` is valid for the entire scope of the `main` function (implicit)
    let message = String::from("Hello, world!");
    println!("{}", message);

    // `name` is valid for the entire program (explicit)
    let name: &'static str = "John";
    println!("{}", name);
}
```

## `String` vs `str`

- `String` is a **mutable**, **growable** heap-allocated string, implemented by
  a struct wrapping a `Vec<u8>`;
- `str` is an **immutable**, **fixed length** string slice.

## `trait`

- Collection of methods;
- Contains functions declarations & default implementations;
- Can be implemented by any type.

```rust
trait Animal<'a> {
    // Method declarations
    fn new(name: &'a str) -> Self;
    
    // Method definitions with default implementation
    fn move(&self, destination: &'a str) {
        println!("{} moves to {}", self.name, destination);
    }
}

struct Horse<'a> {
    name: &'a str,
}

impl<'a> Animal<'a> for Horse<'a> {
    // Define the methods declared in the trait
    fn new(name: &'a str) -> Horse<'a> {
        Horse { name: name }
    }
    
    // Override the default implementation
    fn move(&self, destination: &'a str) {
        println!("{} gallops to {}", self.name, destination);
    }
}
```
