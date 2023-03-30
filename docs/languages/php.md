# PHP

## Types

| Type     | Description           |
|----------|-----------------------|
| `int`    | Integer               |
| `float`  | Floating point number |
| `string` | String                |
| `bool`   | Boolean               |

## Visibility

- **Public**: Visible everywhere;
- **Protected:** Visible only in class and in classes that extend it;
- **Private:** Visible only in class.

## Classes

- Class name in ***PascalCase***.
- Class name should be ***singular***.

*User.php:*

```php
<?php
class User {
    public function __construct(
        public string $firstName,
        public string $lastName,
        public readonly string $birthDate, // can be set only in constructor
        private string $password, // can be set only in class or in constructor
        public ?string $email = null // optional attribute
    ) {}
}
 ```

## Objects

- Object name in ***camelCase***.
- Object parameters should be ***ordered***.
- For unordered parameters, use named parameters. Every parameter after the
first named one must be named too.

*index.php:*

```php
<?php

require_once "./User.php";

$john = new User(
    "John",
    "Doe",
    password: "A_c0mp|ex_p@s5wOrd", // unordered parameter
    birthDate: "1990-01-01",
    email: "jdoe@email.com"
);
```

## Inheritance

- `extends` keyword for inheriting from a class.
- `parent` keyword for calling parent class methods.
- `self` keyword for calling current class methods.
- `static` keyword for calling child class methods.

*Vehicle.php:*

```php
<?php

class Vehicle {
    public function __construct(
        public string $brand,
        public string $color
    ) {}
}
```

*Car.php:*

```php
<?php

require_once "./Vehicle.php";

class Car extends Vehicle {
    public function __construct(
        string $brand,
        string $color,
        public int $numberOfSeats
    ) {
        parent::__construct(brand: $brand, color: $color);
    }
}
```

Note that we can omit the visibility of the attributes inherited for the
constructor parameters.
