---
title: Traits
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Traits

Each trait should go on its own line, and the use keyword should be used for each of them.  (PSR-12 rule)

Having each trait on a new line, will give you cleaner diffs when reviewing code

```php
// 👎🏻
class MyClass {
    use TraitA, TraitB;
}


// 👎🏻
class MyClass {
    use TraitA, 
        TraitB;
}


// ✅
class MyClass {
    use TraitA;
    use TraitB;
}
```
