---
title: Strings
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Strings

When possible prefer string interpolation above `sprintf` and the `.` operator.

```php
// 👎🏻
$quote = 'We are the ' . $champions . '.';


// ✅
$quote = "We are the {$champions}.";
```
