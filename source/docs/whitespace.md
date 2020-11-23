---
title: Comments
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# WhiteSpace

Statements should be allowed to breathe. In general always add blank lines between statements, unless they're a sequence of single-line equivalent operations. This isn't something enforceable, it's a matter of what looks best in its context.

```php
// 👎🏻 Everything is cramped together
public function getPage($url)
{
    $page = $this->pages()->where('slug', $url)->first();
    if (! $page) {
        return null;
    }
    if ($page['private'] && ! Auth::check()) {
        return null;
    }
    return $page;
}
```

```php
// ✅

public function getPage($url)
{
    $page = $this->pages()->where('slug', $url)->first();

    if (! $page) {
        return null;
    }

    if ($page['private'] && ! Auth::check()) {
        return null;
    }

    return $page;
}
```

```php
// ✅ A sequence of single-line equivalent operations.

public function up()
{
    Schema::create('users', function (Blueprint $table) {
        $table->increments('id');
        $table->string('name');
        $table->string('email')->unique();
        $table->string('password');
        $table->rememberToken();
        $table->timestamps();
    });
}
```

Don't add any extra empty lines between {} brackets.

```php
// 👎🏻
if ($foo) {

    $this->foo = $foo;

}


// ✅
if ($foo) {
    $this->foo = $foo;
}
```
