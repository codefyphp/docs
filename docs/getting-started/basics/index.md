---
title: Request
sidebar_title: Request
weight: 7
---

## Installation

```shell
composer require qubus/http
```

## Introduction

`Qubus\Http\Request`, `Qubus\Http\Response`, and `Qubus\Http\ServerRequest` are all wrappers for [laminas-diactoros](https://docs.laminas.dev/laminas-diactoros/v3/api/). 
Check out diactoros's documentation on its api and usage. Those classes provide an object-oriented way to interact with 
HTTP requests and responses.

## ServerRequest Scope

To get access to the server request, you can type-hint the `Qubus\Http\ServerRequest` on a controller's method or a route's 
closure. The incoming request will be automatically injected by the [Injector](../dependency-injection.md).

Controller:

```php title="./app/Infrastructure/Http/Controllers/HomeController.php"
<?php

declare(strict_types=1);

namespace App\Infrastructure\Http\Controllers;

use Codefy\Framework\Http\BaseController;
use Qubus\Http\ServerRequest;

final class HomeController
{
    public function index(ServerRequest $request): ?string
    {
        dd($request->getHeaders());
    }
}
```

Route:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

use dd;

return function(\Qubus\Routing\Psr7Router $router) {
    $router->get('/', function(\Qubus\Http\ServerRequest $request) {
        dd($request->getHeaders());
    });
};
```

## Request
`Qubus\Http\Request` is a wrapper around a [Psr\Http\Message\RequestInterface](https://github.com/php-fig/http-message/blob/master/src/ResponseInterface.php) implementation with some added methods 
to help pull out `header`, `$_GET` or `$_POST` parameters. Requests are immutable. Any methods that would change state — 
those prefixed with `with` and `without` — all return a new instance with the changes requested.

### Instantiate

    <?php

    declare(strict_types=1);
    
    use Qubus\Http\Request;
    
    $request = new Request();

### $_GET

You can access the `$_GET` array via the `get()` method through the`handler()` method which returns a `Qubus\Http\Input\Input` object:

    <?php
    
    $object = $request->handler()->get('id');  // Returns an InputItem object.
    $id     = $object->getValue(); // Returns the actual id.

### $_POST

You can access the `$_POST` array via the `post()` method through the`handler()` method which returns a `Qubus\Http\Input\Input` object:

    <?php
    
    $object = $request->handler()->post('id');
    $id     = $object->getValue();

The `Input` class includes these methods:

| Methods      | Description                                                                           |
|--------------|---------------------------------------------------------------------------------------|
| `getIndex()` | Returns the index/key of the input.                                                   |
| `setIndex()` | Set the index/key of the input.                                                       |
| `getName()`  | Returns a human friendly name for the input (`company_name` will be `Company Name`.). |
| `setName()`  | Sets a human friendly name for the input (`company_name` will be `Company Name`.).    |
| `getValue()` | Returns the value of the input.                                                       |
| `setValue()` | Sets the value of the input.                                                          |

### $_FILES

You can access `$_FILES` via the `file()` method through the`handler()` method which returns a `Qubus\Http\Input\File` object:

    <?php
    
    $object = $request->handler()->file('image');
    $image  = $object->getFilename();

`File` has the same methods as above along with some other file-specific methods like:

| Methods              | Description                                                               |
|----------------------|---------------------------------------------------------------------------|
| `getFilename`        | Get the filename.                                                         |
| `getTmpName()`       | Get file temporary name.                                                  |
| `getSize()`          | Get file size.                                                            |
| `move($destination)` | Move file to destination.                                                 |
| `getContents()`      | Get file content.                                                         |
| `getType()`          | Get mime-type for file.                                                   |
| `getError()`         | Get file upload error.                                                    |
| `hasError()`         | Returns bool if an error occurred while uploading (if getError is not 0). |
| `toArray()`          | Returns raw array                                                         |

### $_SERVER

There is a shortcut available to access the `$_SERVER` array via the `getServer()` method. When using this method, all 
`$_SERVER` indices are made lower case and all underscores (`_`) have been converted to dashes (`-`):

    <?php
    
    $host = $request->getServer('http-host');
    // or
    $host = $request->getHost();

#### Check if parameters exists

You can easily check if multiple items exists by using the exists method. It's similar to `value` as it can be used to 
filter on request-methods and supports both `string` and `array` as parameter value.

    <?php
    
    $input = $request->handler();
    
    if($input->exists(['fname', 'lname', 'email'])) {
        //do something
    }

    /* Similar to above */
    if($input->exists('fname') && $input->exists('lname') && $input->exists('email')) {
        //do something
    }

### Request Headers

You can access request headers using the `getHeader()` or `getHeaders()` method:

    <?php
    
    $auth = $request->getHeader('Authorization');
    // or
    $auth = $request->getHttpHeader(name: 'authorization', defaultValue: 'value');
    
    // If you need to grab all headers
    $headers = $request->getHeaders();
    // or
    $headers = $request->getHttpHeaders();

### Request Method

You can access the request method using the `getMethod()` method:

    <?php
    
    $method = $request->getMethod();

### Request URLs

There are a few helper methods to piece together parts of a URL for your convenience.

#### Original URL

```php title="https://codefy.ddev.site:33001/admin/login/"
<?php

return $request->getUrl()->getOriginalUrl();
```

#### Absolute URL

```php title="https://codefy.ddev.site:33001/admin/login/"
<?php

return $request->getUrl()->getAbsoluteUrl();
```

#### Relative Url

```php title="/admin/login/"
<?php

$url = $request->getUrl()->getRelativeUrl();
// or
$url = $request->getUri()->getPath();

return $url;
```

#### Other Uri Methods

```php title="codefy.ddev.site"
<?php

return $request->getUri()->getHost();
```

```php title="https"
<?php

return $request->getUri()->getScheme();
```

```php title="33001"
<?php

return $request->getUri()->getPort();
```

```php title="codefy.ddev.site:33001"
<?php

return $request->getUri()->getAuthority();
```

```php title="' '"
<?php

return $request->getUri()->getQuery();
```

