# PHP

## Classes

- Class name in ***PascalCase***.
- Class name should be ***singular***.

*User.php:*

```php
<?php
class User
{
    public function __construct
    (
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

require_once("./User.php");

$john = new User
(
    "John",
    "Doe",
    password: "A_c0mp|ex_p@s5wOrd", // unordered parameter
    birthDate: "1990-01-01",
    email: "jdoe@email.com"
);
```
