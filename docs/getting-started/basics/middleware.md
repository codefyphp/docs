---
title: Middleware
sidebar_title: Middleware
weight: 17
---

A PSR-7/15 Middleware can be added to routes, groups, and controllers. To add a middleware to a route or controller, 
you must add it as a class string (`AddHeaderMiddleware::class`) or as an alias (`csrf.token`) as defined in 
`config/app.php`.

## Adding Middleware to Routes

At it's simplest, adding Middleware to a route can be done by passing the class string to the `middleware()` method:

```php title="./routes/web/web.php"
<?php

use Application\Http\Middleware\AddHeaderMiddleware;
use Qubus\Routing\Route\RouteGroup;

return function (\Qubus\Routing\Psr7Router $router) {
    $router->group(params: '', callback: function (RouteGroup $group) {
        $group
        ->get(uri: '/', callback: 'HomeController@index')
        ->middleware(AddHeaderMiddleware::class);
    });
};
```

Multiple middleware can be added by passing more parameters to the `middleware()` method:

```php title="./routes/web/web.php"
<?php

use Application\Http\Middleware\AddHeaderMiddleware;
use Application\Http\Middleware\AuthMiddleware;
use Qubus\Routing\Route\RouteGroup;

return function (\Qubus\Routing\Psr7Router $router) {
    $router->group(params: '', callback: function (RouteGroup $group) {
        $group
        ->get(uri: '/', callback: 'HomeController@index')
        ->middleware(
            AddHeaderMiddleware::class,
            AuthMiddleware::class
        );
    });
};
```


Or alternatively, you can also pass an array of middleware:

```php title="./routes/web/web.php"
<?php

use Application\Http\Middleware\AddHeaderMiddleware;
use Application\Http\Middleware\AuthMiddleware;
use Qubus\Routing\Route\RouteGroup;

return function (\Qubus\Routing\Psr7Router $router) {
    $router->group(params: '', callback: function (RouteGroup $group) {
        $group
        ->get(uri: '/', callback: 'HomeController@index')
        ->middleware([
            AddHeaderMiddleware::class,
            AuthMiddleware::class
        ]);
    });
};
```

### Middleware Aliases

You may assign aliases to middleware in your application's `bootstrap/app.php` file using the `withMiddleware` method:

```php
<?php

declare(strict_types=1);

use Codefy\Framework\Application as CodefyApp;
use Codefy\Framework\Configuration\Middleware;
use Qubus\Exception\Data\TypeException;

use function Codefy\Framework\Helpers\env;

try {
    $app = CodefyApp::create(
        config: [
            'basePath' => env(key: 'APP_BASE_PATH', default: dirname(path: __DIR__))
        ]
    )
    ->withMiddleware(function (Middleware $middleware) {
        $middleware->alias(
            [
                'debugbar' => Codefy\Framework\Http\Middleware\DebugBarMiddleware::class
            ]
        );
    })->return();

    $app->share(nameOrInstance: $app);

    return $app::getInstance();
} catch (TypeException|ReflectionException $e) {
    return $e->getMessage();
}
```

Middleware aliases allow you to define a short alias for a given middleware class, which can be especially useful for 
middleware with long class names:

| Alias                     | Middleware                                                                              | 
|---------------------------|-----------------------------------------------------------------------------------------| 
| `api`                     | `Codefy\Framework\Http\Middleware\ApiMiddleware::class`                                 |
| `security.headers`        | `Codefy\Framework\Http\Middleware\SecureHeaders\ContentSecurityPolicyMiddleware::class` |
| `content.cache`           | `Codefy\Framework\Http\Middleware\ContentCacheMiddleware::class`.                       |
| `cors`                    | `Codefy\Framework\Http\Middleware\CorsMiddleware::class`                                |
| `csrf.token`              | `Codefy\Framework\Http\Middleware\Csrf\CsrfTokenMiddleware::class`                      |
| `csrf.protection`         | `Codefy\Framework\Http\Middleware\Csrf\CsrfProtectionMiddleware::class`                 |
| `css.minify`              | `Codefy\Framework\Http\Middleware\CssMinifierMiddleware::class`                         |
| `gate`                    | `Codefy\Framework\Http\Middleware\Auth\GateMiddleware::class`                           |
| `honeypot`                | `Codefy\Framework\Http\Middleware\Spam\HoneyPotMiddleware::class`                       |
| `html.minify`             | `Codefy\Framework\Http\Middleware\HtmlMinifierMiddleware::class`                        |
| `http.cache`              | `Codefy\Framework\Http\Middleware\Cache\CacheMiddleware::class`                         |
| `http.cache.clear.data`   | `Codefy\Framework\Http\Middleware\Cache\ClearSiteDataMiddleware::class`                 |
| `http.cache.expires`      | `Codefy\Framework\Http\Middleware\Cache\CacheExpiresMiddleware::class`                  |
| `http.cache.prevention`   | `Codefy\Framework\Http\Middleware\Cache\CachePreventionMiddleware::class`               |
| `js.minify`               | `Codefy\Framework\Http\Middleware\JsMinifierMiddleware::class`                          |
| `rate.limiter`            | `Codefy\Framework\Http\Middleware\ThrottleMiddleware::class`                            |
| `referrer.spam`           | `Codefy\Framework\Http\Middleware\Spam\ReferrerSpamMiddleware::class`                   |
| `user.authenticate`       | `Codefy\Framework\Http\Middleware\Auth\AuthenticationMiddleware::class`                 |
| `user.session`            | `Codefy\Framework\Http\Middleware\Auth\UserSessionMiddleware::class`                    |
| `user.authorization`      | `Codefy\Framework\Http\Middleware\Auth\UserAuthorizationMiddleware::class`              |
| `user.session.expire`     | `Codefy\Framework\Http\Middleware\Auth\ExpireUserSessionMiddleware::class`              |
| `php.debugbar`            | `Codefy\Framework\Http\Middleware\DebugBarMiddleware::class`                            |
| `http.exception`          | `Codefy\Framework\Http\Middleware\Exception\HttpExceptionMiddleware::class`             |
| `html.http.exception`     | `Codefy\Framework\Http\Middleware\Exception\HtmlHttpExceptionMiddleware::class`         |
| `json.http.exception`     | `Codefy\Framework\Http\Middleware\Exception\JsonHttpExceptionMiddleware::class`         |
| `redirect.http.exception` | `Codefy\Framework\Http\Middleware\Exception\RedirectionHttpExceptionMiddleware::class`  |
| `bind.request`            | `Codefy\Framework\Http\Middleware\BindRequestMiddleware::class`                         |
| `user.cookie.decrypt`     | `Codefy\Framework\Http\Middleware\Auth\UserCookieDecryptMiddleware::class`              |


## Base Middleware

If you would like to add a middleware that is going to affect all routes, then use `base_middlewares` array in your 
`config/app.php` file:

```php title="./config/app.php"
<?php
    //
    
    /*
    |--------------------------------------------------------------------------
    | Base Middlewares
    |--------------------------------------------------------------------------
    | Register middleware class strings or aliases to be applied to the entire
    | application.
    */
    'base_middlewares' => [
        'csrf.token',
        'csrf.protection',
        'http.cache.prevention',
        'user.cookie.decrypt',
        'bind.request',
        'debugbar',
        'http.exception',
    ],
    
    //
```

## Route Group

Middleware can also be added to a group. To do so you need to pass an array as the first parameter of the `group()` 
function instead of a string. You can add one middleware or an array of middleware.

```php title="./routes/web/web.php"
<?php

use Application\Http\Middleware\AddHeaderMiddleware;
use Qubus\Routing\Route\RouteGroup;

return function (\Qubus\Routing\Psr7Router $router) {
    $router->group(
        params: ['prefix' => 'my-prefix', 'middleware' => [AddHeaderMiddleware::class]],
        callback: function (RouteGroup $group) {
            $group->map(['GET'], 'route1', function () {}); // `/my-prefix/route1`
            $group->map(['GET'], 'route2', function () {}); // `/my-prefix/route2`
        }
    );
};
```

## Middleware on Controllers

You can also apply Middleware on a Controller class too. In order to do this your Controller must extend the 
`Codefy\Framework\Http\BaseController` abstract class.

Middleware is added by using the `middleware` property in your Controller.

```php title="./src/Application/Http/Controller/PostController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Application\Http\Middleware\AddHeaderMiddleware;
use Application\Http\Middleware\AuthMiddleware;
use Codefy\Framework\Http\BaseController;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

class PostController extends BaseController
{
    protected array $middlewares = [
        AddHeaderMiddleware::class,
        AuthMiddleware::class
    ];
}
```

### Partial Method Controllers

By default, all Middlewares added via a Controller will affect all methods on that class. To limit what methods a 
Middleware should be applied to, you can use the `only()` and `except()` methods when using the `middleware()` method 
instead of the `middleware` property:

```php title="./src/Application/Http/Controller/PostController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Application\Http\Middleware\AddHeaderMiddleware;
use Application\Http\Middleware\AuthMiddleware;
use Codefy\Framework\Http\BaseController;
use Psr\Http\Message\ResponseInterface;
use Qubus\Http\ServerRequest;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

class PostController extends BaseController
{
    public function __construct(
        SessionService $sessionService,
        Router $router,
        Renderer $view
    ) {
        // Only apply to `edit()` method
        $this->middleware(AddHeaderMiddleware::class)->only('edit');

        // Apply to all methods except `show()` method
        $this->middleware(AuthMiddleware::class)->except('show');

        // Multiple methods can be provided in an array to both methods
        $this->middleware(AuthMiddleware::class)->except(['edit', 'show']);

        parent::__construct($sessionService, $router, $view);
    }
    
    public function edit(ServerRequest $request): ResponseInterface
    {
    }
    
    public function show(): ResponseInterface
    {
    }
}
```

## Service Provider

Instead of adding your routes to `routes/web/web.php` (recommended), you can add them to 
`Application\Provider\WebRouteServiceProvider`

```php
<?php

declare(strict_types=1);

namespace Application\Provider;

use Application\Http\Middleware\AddHeaderMiddleware;
use Codefy\Framework\Support\CodefyServiceProvider;
use Qubus\Routing\Psr7Router;
use Qubus\Routing\Route\RouteGroup;
use Qubus\Routing\Router;

final class WebRouteServiceProvider extends CodefyServiceProvider
{
    public function register(): void
    {
        /** @var Router $router*/
        $router = $this->codefy->make(name: Psr7Router::class);
        
        $router->group(params: '', callback: function (RouteGroup $group) {
            $group
            ->get(uri: '/', callback: 'HomeController@index')
            ->middleware(AddHeaderMiddleware::class);
        });
    }
}

```

