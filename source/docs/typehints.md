---
title: Typehints
description: Typehints
extends: _layouts.documentation
section: content
---

# TypeHints

Use typehints whenever you can, that's it!

## Class Properties

```php
// 👎🏻
class Customer
{
    public $name;
}


// ✅ Properties can be typehinted.
class Customer
{
    public string $name;
}
```

## Method Parameters

```php
// 👎🏻
private function charge($user, $credit)
{
	...
}


// ✅ Parameters can be typehinted
private function charge(User $user, Credit $credit)
{
	...
}
```

## Method Return Types

If you know the type of argument this function should return, use a typehint, even if a funcion returns nothing, use `void`

```php
// 👎🏻
private function charge()
{
	...
}


// ✅ void is a valid return type
private function charge(): void
{
	...
}


// ✅ Charge is a know return type
private function charge(): Charge
{
	...
}
```
