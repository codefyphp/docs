---
title: Autoloading
sidebar_title: Autoloading
summary: Configure Composer autoloading for CodefyPHP and follow modern PHP conventions for namespaces, class names, properties, methods, functions, and strict types.
keywords: php-autoloading,composer-psr-4,php-coding-standards
weight: 3
---

CodefyPHP follows PSR-4 for autoloading libraries and packages through composer that you need to run and enhance your 
development environment. You need to require the autoloader file in a front controller (usually index.php).

### Basic Example

```php
require 'vendor/autoload.php';
```

## Namespaces

The default namespaces are `Application`, `Domain`, `Database\Seeders`, and `Infrastructure`

For example, if you have a controller named `DashboardController.php` located in the `src/Application/Http/Controller` 
directory, then the namespace would be `Application\Http\Controller\DashboardController`.

## Class Names

Class names should follow PSR-1, and should be written in StudlyCaps (i.e. `DashboardController`).

## Class Properties

Based on the coding standards followed by the framework, property names should follow camelCase (i.e. `$serverRequest`).

## Class Methods

Based on PSR-1, method names should follow camelCase (i.e. `public function setRequestHandler()`).

## Function Names

Based on the coding standards followed by the framework, function names should follow under_score case 
(i.e. `current_user_can()`).

## Strict Typing

The CodefyPHP framework follows a strict type principle, although not perfectly. Explicit typing of properties, methods 
and return values are strongly recommended which can help eliminate ambiguity regarding what a function, property, 
parameter or method expects to receive and/or return. You can enable strict mode in any PHP file, you will need to add 
the declare statement after the opening php tag:

```php
<?php

declare(strict_types=1);
```
