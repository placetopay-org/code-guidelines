---
title: Configuration
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Configuration

## File names

Configuration file names must use kebab-case.

```php
config/pdf-generator.php
```

## Config keys

Configuration keys must use snake_case.

```php
// inside config/pdf-generator.php
return [
    'chrome_path' => env('CHROME_PATH'),
];
```

Avoid using the `env()` helper outside of configuration files. Create a configuration file or key from the env variable

```php
// 👎🏻
$useMock = env('PLACETOPAY_USE_MOCK');


// ✅
$useMock = config('placetopay.use_mock');
```
