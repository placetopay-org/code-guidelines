---
title: Strings
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# If statements

## Bracket position

Always use curly brackets.

Always put expressions in a new line

```php
// 👎🏻
if ($condition) runSomething();


// 👎🏻
if ($condition) {runSomething();}


// 👎🏻
if ($condition) 
    runSomething();


// ✅
if ($condition) {
    runSomething();
}
```

## Happy Path

Generally a function should have its unhappy path first and its happy path last.

In most cases this will cause the happy path being in an unindented part of the function which makes it more readable.

Unhappy paths should happen as soon as possible.

```php
// 👎🏻
if ($everythingIsOK) {
    keepWorking();
}

throw new Exception;
```

```php
// ✅
if ($somethingIsWrong) {
    throw new Exception;
}

keepWorking();
```

## Do you need `else` ?

In general, `else` should be avoided because it makes code less readable. In most cases it can be refactored using early returns. This will also cause the happy path to go last, which is desirable.

```php
// 👎🏻
if (!$conditionA) {
   return;
} else {
   keepWorking();
}
```

```php
// ✅
if (!$conditionA) {
    return;
}

keepWorking();
```

## Compound Ifs

In general, separate if statements should be preferred over a compound condition. This makes debugging code easier.

```php
// 👎🏻

if ($conditionA && $conditionB && $conditionC) {
  keepWorking();
}

return;
```

```php
// ✅

if (! $conditionA) {
   return;
}

if (! $conditionB) {
   return;
}

if (! $conditionC) {
   return;
}

keepWorking();
```

## Ternary operation

If the expression is very short, use a one line

```php
// 👎🏻
$color = $isBlack 
		? 'Black' 
		: 'Yellow';


// ✅
$color = $isBlack ? 'Black' : 'Yellow';
```

If the expression is a bit longer, use multiple lines

```php
// 👎🏻
return $this->type->value === TransactionStatus::PENDING_PAYMENT ? $this->type->name : 'Unknown';


// ✅
return $this->type->value === TransactionStatus::PENDING_PAYMENT
    ? $this->type->name
    : 'Unknown';
```

Avoid nesting ternary operations. They are trickier to reason about and don't necessarily execute in the order you expect.
