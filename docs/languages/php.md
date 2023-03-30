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
        public ?string $email = null // optional attribute
        private string $password // can be set only in class
    ) {}
}
 ```

## Objects

- Object name in ***camelCase***.

*index.php:*

```php
<?php

require_once('./User.php');

$john = new User("John", "Doe");
```
