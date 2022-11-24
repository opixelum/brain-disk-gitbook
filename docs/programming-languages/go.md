# Go

## Objectives

Built by Google engineers, the objectives are:

- Easy to write, similar to a scripting language;
- Easy to learn from another language such as C, Python, ...
- Compiled language for fast execution;
- Modern language, supporting concurrency, designed for the web of tomorrow.

## Variables declaration

Go is a typed language. You can specified the type of a variable, or let the
compiler decide for you:

```go
var a int 
a = 1

var b int = 2

// var keyword is optional only if you use the := syntax
c := 3
```

A variable can't change its type in its scope.

## Functions

### Functions declaration

```go
func functionName(parameterName type) returnType {
    // code
}
```

Example:

```go
func add(a int, b int) int {
    return a + b
}
```

If parameters have the same type, you can write it only once:

```go
func add(a, b int) int {
    return a + b
}
```

For public functions, you must start the name with a capital letter.
Example: *fmt.**P**rintln()*.

### Functions return

A function can return multiple values:

```go
func swap(a, b int) (int, int) {
    return b, a
}
```

### Anonymous functions

Anonymous functions are functions without a name. They are also called function
literals. They are useful for:

- Inline function declarations:

```go
func main() {
    func() {
        fmt.Println("Hello")
    }()
    // Output: Hello
}
```

- Assigning a function to a variable:

```go
func main() {
    f := func() {
        fmt.Println("Hello")
    }
    f()
    // Output: Hello
}
```

- Passing a function as a parameter to another function:

```go
func main() {
    f := func() {
        fmt.Println("Hello")
    }
    func(f func()) {
        f()
    }(f)
    // Output: Hello
}
```

- Closures:

```go
// Returns a function that returns an int
func fibonacci() func() int {
    first := 0
    second := 1

    f := func() int {
        sum := first + second
        first, second = second, sum
        return sum
    }

    return f
}

func main() {
    f := fibonacci()

    for i := 0; i < 10; i++ {
        fmt.Println(f())
    }
}
```

## Iterations

- There is no `while` loop in Go. You can only use `for` loops:

```go
for i := 0; i < 10; i++ {
    // code
}
```

- For an infinite loop:

```go
for {
    // code
}
```

## Conditions

- No parenthesis around conditions:

```go
if condition {
    // code
} else if condition {
    // code
} else {
    // code
}
```

- We can also declare a variable in the condition:

```go
if a := 1; a == 1 {
    // code
}
```

- There is also a `switch` statement, with no `break` needed:

```go
switch a {
case 1:
    // code
case 2:

default:
    // code
}
```

- There is no ternary operator in Go (`condition ? true : false`). The reason is
that Go chose the simple approach, and the ternary operator is less readable
for beginners.

## Packages

In Go, our code is organized in packages. A package is a collection of files
that are compiled together. A package can be imported by another package.

The main package is the entry point of our program. It is the package that will
be executed when we run our program.

## References

- Stéphane Karraz, Go instructor at ESGI
- [Tour of Go](https://tour.golang.org/)
- [Closure in Golang](https://bluehive.medium.com/closure-in-golang-with-fibonacci-series-1cbced4f359d)
- [Anonymous function in Go Language](https://www.geeksforgeeks.org/anonymous-function-in-go-language/)
