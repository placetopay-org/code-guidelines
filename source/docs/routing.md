---
title: Configuration
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Routing

## RESTful routes

Your controller name should be related to a resource

Your controller name, when related to a resource should be plural.

Keep your controller "Cruddy by design"

> "Cruddy by Design" is a concept introduced by Adam Wathan in its [Laracon 2017 Talk](https://www.youtube.com/watch?v=MF0jFKvS4SI&t=14s&ab_channel=AdamWathan).

```php
// Payment Methods
PaymentMethodsController::class 

// Disabled Payment Methods
DisabledPaymentMethodsController::class

// Payment Methods of an user
UserPaymentMethodsController::class

// Disabled Payment Methods of an user
UserDisabledPaymentMethodsController::class
```

## Route declaration

Use the route tuple notation when possible.

```php
// 👎🏻
Route::get('payments', 'PaymentsController@index')->name(...);


// ✅
Route::get('payments', [PaymentsController::class, 'index'])->name(...);
```

Use the http verb first

```php
// 👎🏻
Route::name('payments.index')
    ->get('payments', [PaymentsController::class, 'index']);


// ✅
Route::get('payments', [PaymentsController::class, 'index'])
    ->name('payments.index');
```

Always name your routes

```php
// 👎🏻
Route::get('payments', [PaymentsController::class, 'index']);


// ✅
Route::get('payments', [PaymentsController::class, 'index'])
    ->name('payments.index');
```

### Url names

Urls must use kebab-case

If the route name relates to an resource, use plural.

```php
// 👎🏻
Route::get('payment_methods', ...);
Route::get('paymentMethods', ...);
Route::get('payment--methods', ...);


// ✅
Route::get('payment-methods', ...);
Route::get('enabled-payment-methods', ...);
```

### Route names

Route names must use kebab-case.

Route names must have a resource or domain followed by an action `{resource}.{action}` 

Resource name should be plural.

A resource in this example is:  `PaymentMethod -> payment-methods`

```php
// 👎🏻
Route::get('payment-methods', ...)->name('payment_methods.index');
Route::get('payment-methods', ...)->name('paymentMethods.index');
Route::get('payment-methods', ...)->name('payment.methods.index');


// ✅
Route::get('payment-methods', ...)->name('payment-methods.index');
```

Actions should be CRUD names `index, create, store, show, edit, update, destroy`

```php
// 👎🏻
Route::get('payment-methods', ...)->name('payment-methods');
Route::get('payment-methods', ...)->name('payment-methods-index');
Route::get('payment-methods', ...)->name('payment-methods.list');


// ✅
Route::get('payment-methods', ...)->name('payment-methods.index');
```

### Route names with relationships

Route names that work with relationships must use names in the same order as the url and separated by a dot `.`

```php
// 👎🏻
Route::get('users/{user}/payment-methods', ...)->name('user-payment-methods.index');
Route::get('users/{user}/payment-methods', ...)->name('payment-methods.user.index');
Route::get('users/{user}/payment-methods', ...)->name('payment-methods.index.user');


// ✅
Route::get('users/{user}/payment-methods', ...)->name('users.payment-methods.index');
```

### Route parameters

Route parameters should be related to a resource.

Route parameters should be singular.

Route parameters should use snake_case

```php
// 👎🏻
Route::get('payment-methods/{paymentMethod}', ...);
Route::get('payment-methods/{payment-method}', ...);
Route::get('payment-methods/{payment_methods}', ...);


// ✅
Route::get('payment-methods/{payment_method}', ...);
```

### Testing

When testing endpoints use the `route()` helper.

```php
// 👎🏻
$this->get('/payment-methods')->assertOk();


// ✅
$this->get(route('payment-methods.index'))->assertOk();
```
