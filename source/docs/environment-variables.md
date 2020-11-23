---
title: Environment variables
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Environment Variables

## names

Use all caps and underscore to name your variables.

```php
PLACETOPAY_LOGIN="12345"
```

Don't be afraid of using long names if this helps to better understand what your variable does.

```dotenv
# 👎🏻
PP_EXPIRATION=128


# ✅
PASSPORT_TOKES_EXPIRATION=128
```

You can use comments to better explain what these variables are for

```dotenv
# ✅

# PAYMENT GATEWAY CREDENTIALS
PLACETOPAY_LOGIN=login
PLACETOPAY_TRANKEY=tranKey

# CORE SERVICES
PLACETOPAY_CORE_LOGIN=restLogin
PLACETOPAY_CORE_TRANKEY=restTrankey
```

Every new environment variable that is added and is needed per environment, 
should be added to the existing `env.example`, `env.testing` or `env.pipelines` files. 
