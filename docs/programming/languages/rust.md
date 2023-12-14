# Rust

## `String` vs `str`

- `String` is a **mutable**, **growable** heap-allocated string, implemented by
  a struct wrapping a `Vec<u8>`.
- `str` is an **immutable**, **fixed length** string slice.

## Traits

- Collection of methods;
- Contains functions declarations & default definitions;
- Can be implemented by any type.
