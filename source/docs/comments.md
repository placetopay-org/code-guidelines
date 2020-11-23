---
title: Comments
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Comments

Comments should be avoided as much as possible by writing expressive code. If you do need to use a comment, format it like this:

```php
// There should be a space before a single line comment.

/*
 * If you need to explain a lot you can use a comment block. Notice the
 * single * on the first line.
 */
```

A possible strategy to refactor away a comment is to create a function with name that describes the comment

```php
// 👎🏻

// Start calculation taxes
...
$code ...
$moreCode ....
$lotsOfCode ...
...
```

```php
// ✅

...
$taxes = $this->calculateTaxes();
...
```
