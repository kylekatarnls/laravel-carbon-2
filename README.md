# laravel-carbon-2

Carbon 2 adapter for Laravel

To install Carbon 2 in your Laravel project, add the following dependencies to your **composer.json**:

```json
{
  ...
  "require": {
    ...
    "kylekatarnls/laravel-carbon-2": "^1.0.0",
    "nesbot/carbon": "2.0.0-beta.2 as 1.25.0"
  }
  ...
}
```

Then run:
```
composer update
```

## Why do I need 2 more package?

Current stable versions of Laravel require Carbon version 1 (with various minimum and maximum minor versions).

So we need first to set the nesbot/carbon to 2.x version and add an alias so it won't conflict with the inner
Carbon version required by Laravel.

Then, Laravel extends the Carbon class to add JSON serialization and macros. The way macros are implemented is
not compatible with Carbon 2. And JSON serialization and macros are still there in Carbon since version 1.26.0
and work exactly the same way. That's why they could be safely removed when working with Carbon 2.

So we install **kylekatarnls/laravel-carbon-2** that basically "removes" the no longer needed overrides of Laravel
Carbon class by providing a replacement Illuminate\Support\Carbon class that comes with no overrides and have
the precedence over the Laravel's class.
