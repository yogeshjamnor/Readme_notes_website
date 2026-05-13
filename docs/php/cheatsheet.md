# PHP Cheatsheet

Quick reference for modern PHP syntax (PHP 8+).

## Types and basics

```php
<?php
declare(strict_types=1);

$name = "World";
$count = 3;
$isOk = true;
```
## Arrays

```php
$list = [1, 2, 3];
$map = ["a" => 1, "b" => 2];

$list[] = 4;
$keys = array_keys($map);
```
## Functions

```php
function add(int $a, int $b): int {
  return $a + $b;
}

$sum = add(2, 3);
```
## Classes

```php
final class User {
  public function __construct(
    public string $id,
    public string $email,
  ) {}
}

$u = new User("1", "a@example.com");
```
## Code Examples

### Nullsafe operator + null coalescing
```php
$city = $user?->address?->city ?? "NA";
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
