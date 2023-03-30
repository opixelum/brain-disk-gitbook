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
        public ?string $email = null // optional attribute
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
