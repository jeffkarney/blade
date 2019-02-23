Blade
=====

[![Latest Stable Version](http://img.shields.io/github/release/jeffkarney/blade.svg)](https://packagist.org/packages/jeffkarney/blade) [![Build Status](http://img.shields.io/travis/jeffkarney/blade.svg)](https://travis-ci.org/jeffkarney/blade) [![Coverage Status](http://img.shields.io/coveralls/jeffkarney/blade.svg)](https://coveralls.io/r/jeffkarney/blade)

The standalone version of [Laravel's Blade templating engine](http://laravel.com/docs/5.4/blade) for use outside of Laravel.

Installation
------------

Install using composer:

```bash
composer require jeffkarney/blade
```

Usage
-----

Create a Blade instance by passing it the folder(s) where your view files are located, and a cache folder. Render a template by calling the `make` method. More information about the Blade templating engine can be found on http://laravel.com/docs/5.4/blade.

```php
use JeffKarney\Blade\Blade;

$blade = new Blade('views', 'cache');

echo $blade->make('homepage', ['name' => 'John Doe']);
```

Now you can easily create a directive by calling the ``compiler()`` function

```php
$blade->compiler()->directive('datetime', function ($expression) {
    return "<?php echo with({$expression})->format('F d, Y g:i a'); ?>";
});

{{-- In your Blade Template --}}
<?php $dateObj = new DateTime('2017-01-01 23:59:59') ?>
@datetime($dateObj)
```

The Blade instances passes all methods to the internal view factory. So methods such as `exists`, `file`, `share`, `composer` and `creator` are available as well. Check out the [original documentation](http://laravel.com/docs/5.4/views) for more information.

License
-----

This is a fork of [jenssegers/blade](https://github.com/jenssegers/blade) authored by Jens Segers and released under the MIT license.

