⚠️ Laravel < 6.20.42 versions all [have security issues](https://packagist.org/packages/laravel/framework/advisories?version=1306238)
and are no longer supported for years. You MUST upgrade to a newer and safer version of Laravel if your still running an older version.

This package helps you upgrading Carbon first if needed but as Laravel >= 6.20.42 all embed Carbon 2, you won't need this package if
you can instead upgrade Laravel.

# laravel-carbon-2

Carbon 2 adapter for Laravel

To install Carbon 2 in your Laravel project, add the following dependencies to your **composer.json**:

```json
{
  ...
  "require": {
    ...
    "kylekatarnls/laravel-carbon-2": "^1.0.0",
    "nesbot/carbon": "2.27.0 as 1.39.0"
  }
  ...
}
```

Then run:
```
composer update
```

## Do I need this package?

Only if you're using Laravel < 6 as it requires Carbon version 1 (with various minimum and maximum minor versions).

So we need first to set the nesbot/carbon to 2.x version and add an alias so it won't conflict with the inner
Carbon version required by Laravel.

Then, Laravel extends the Carbon class to add JSON serialization and macros. The way macros are implemented is
not compatible with Carbon 2. And JSON serialization and macros are still there in Carbon since version 1.26.0
and work exactly the same way. That's why they could be safely removed when working with Carbon 2.

So we install **kylekatarnls/laravel-carbon-2** that basically "removes" the no longer needed overrides of Laravel
Carbon class by providing a replacement Illuminate\Support\Carbon class that comes with no overrides and have
the precedence over the Laravel's class.

## This package is not a long-term solution, just a temporary helper before proper upgrade

Laravel < 6 versions all [have security issues](https://packagist.org/packages/laravel/framework/advisories?version=1306238)
and are no longer supported for years. You MUST upgrade to a newer and safe version of Laravel:

Install and keep updated to get latest security fixes:
https://laravelversions.com/

You can also check seuciry issues for each version on:
https://packagist.org/packages/laravel/framework

Then because all those version use Carbon 2 by default, you no longer need this package once upgraded.
