---
title: Artisan Commands
description: Know PlacetoPay's guidelines to writing code.
extends: _layouts.documentation
section: content
---

# Artisan Commands

## Naming

The names given to artisan commands should all be kebab-cased.

```php
// 👎🏻
php artisan deleteOldRecords


// ✅
php artisan delete-old-records
```

## Feedback

A command should always give some feedback on what the result is. Minimally you should let the handle method spit out a comment at the end indicating that all went well.

```php
// ✅ Inside a Command
public function handle()
{
    // do something
    $this->comment('All ok!');
}
```

When the main function of a result is processing items, consider adding output inside of the loop, so progress can be tracked. Put the output before the actual process. If something goes wrong, this makes it easy to know which item caused the error.

At the end of the command, provide a summary on how much processing was done.

Add a progress bar if you want to

```php
// ✅ Inside a Command
public function handle()
    {
    $this->comment("Start processing items...");

    // do some work
    $items->each(function(Item $item) {
        $this->info("Processing item id `{$item-id}`...");

        $this->processItem($item);
    });

    $this->comment("Processed {$item->count()} items.");
}
```


## Parameters
When you need to add arguments or options to the command you should use snake case to named these arguments
```php
// 👎🏻
{--redirectUri= : The URI to redirect to after authorization }
{--redirect-uri= : The URI to redirect to after authorization }
{--RedirectUri= : The URI to redirect to after authorization }


// ✅
{--redirect_uri= : The URI to redirect to after authorization }
```