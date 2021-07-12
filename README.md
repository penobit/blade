# Blade

The standalone version of [Laravel's Blade templating engine](https://laravel.com/docs/5.8/blade) for use outside of Laravel.

## Installation

Install using composer:

```bash
composer require penobit/blade
```

## Usage

Create a Blade instance by passing it the folder(s) where your view files are located, and a cache folder. Render a template by calling the `make` method. More information about the Blade templating engine can be found on [original laravel's blade documentation](http://laravel.com/docs/5.8/blade.)

```php
use Penobit\Blade\Blade;

$blade = new Blade('viewsDirectory', 'cacheDirectory');

echo $blade->make('homepage', ['author' => 'Penobit', 'variable2' => 'variable value'])->render();
```

Alternatively you can use the shorthand method `render`:

```php
echo $blade->render('homepage', ['author' => 'Penobit', 'variable2' => 'variable value']);
```

You can also extend Blade using the `directive()` function:

```php
$blade->directive('datetime', function ($expression) {
    return "<?php echo date('Y-m-d H:i', {$expression}); ?>";
});
```

Which allows you to use the following in your blade template:

```blade
Current date: @datetime($date)
```

The Blade instances passes all methods to the internal view factory. So methods such as `exists`, `file`, `share`, `composer`, `auth`, `creator`, etc are available as well. Check out the [original documentation](https://laravel.com/docs/5.8/views) for more information.
