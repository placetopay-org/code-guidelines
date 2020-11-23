---
title: Docblocks
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Docblocks

If the method is fully type hinted, docblocks are **optional**.

Docblocks can help to keep spacing and consistency between other methods.

```php
// ✅
class Gateway
{
	private function charge(User $user): Charge
	{
    	...
	}
}


// ✅
class Gateway
{
    /**
     * @param \App\User $user
     * @return \PlacetoPay\Gateway\Charge
     */
    private function charge(User $user): Charge
    {
        ...
    }
}
```

If the method is not fully type hinted, docblocks **should** be used.

Docblocks help you and IDE's to better understand the code and find errors.

```php
// 👎🏻
class Gateway
{
    private function charge($credit)
    {
        ...
    }
}


// ✅
class Gateway
{
    /**
     * @param int|\App\Credit $credit
     * @return \App\User|int
     */
    private function charge($credit)
    {
        ...
    }
}
```

If you need at least one docblock annotation or a description in the method, you should add any other needed annotations, even those that are already typed.

```php
// 👎🏻
class Gateway
{
    /**
     * @param int|\App\Credit $credit
     */
    private function charge(User $user, $credit)
    {
		...
    }
}


// ✅
class Gateway
{
    /**
     * @param \App\User $user
     * @param int|\App\Credit $credit
     * @return \App\User|int
     */
    private function charge(User $user, $credit)
    {
        ...
    }
}
```

If you are using docblocks, use them the right way.

Wrong or mismatched docblocks are worst than no docblocks

```php
// 👎🏻
class Gateway
{
    /**
     * @param \Http\Request $user
     */
    private function charge(User $user)
    {
        ...
    }
}


// ✅
class Gateway
{
    /**
     * @param \App\User $user
     */
    private function charge(User $user)
    {
        ...
    }
}
```

Always use fully qualified class names in docblocks.

```php
// 👎🏻
/**
 * @param \App\User $user
 * @param int|Credit $credit
 */


// ✅
/**
 * @param \App\User $user
 * @param int|\App\Credit $credit
 */
```

If a variable has multiple types, the most common occurring type should be first.

```php
// 👎🏻
/**
 * @param null|\App\Credit $credit
 */


// ✅
/**
 * @param \App\Credit|null $credit
 */
```
