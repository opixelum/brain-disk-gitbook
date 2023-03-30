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
        public string $firstName
        public string $lastName
        public readonly string $birthDate // can be set only in constructor
        private string $password // can be set only in class
        public ?string $email = null // optional attribute
    ) {}
}
 ```

## Objects

- Object name in ***camelCase***.
- When instantiating an object, **named parameters** is useful for changing the
order of the parameters.

*index.php:*

```php
<?php

require_once('./User.php');

$john = new User
(
    "John",
    "Doe",
    password: "A_c0mp|ex_p@s5wOrd", // unordered parameter
    "1990-01-01",
    "jdoe@email.com"
);
```
