---
title: Routing
sidebar_title: Routing
weight: 15
---

## Installation

```shell
composer require qubus/router
```

## Introduction

The framework uses [qubus/router](https://github.com/qubusphp/router). This section gives you a nice rundown of the router 
and how it works. If you use the [skeleton](https://github.com/codefyphp/skeleton) package, the router will be injected 
throughout the application via the`RouterServiceProvider`. Any place in the application where `Qubus\Routing\Router` or 
`Qubus\Routing\Psr7Router` is the dependency, the Container will resolve the dependency.

## Basic Routing

Below is a basic example of setting up a route. The route's first parameter is the uri, and the second parameter is a 
closure or callback.

```php
<?php

declare(strict_types=1);

/**
* Step 1: Require autoloader and import a few needed classes.
*/

require('vendor/autoload.php');

use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ResponseFactoryInterface;
use Qubus\Http\Request;
use Qubus\Http\Response;
use Qubus\Injector\Config\Factory;
use Qubus\Injector\Psr11\Container;
use Qubus\Routing\Route\RouteCollector;
use Qubus\Routing\Router;

$container = new Container(Factory::create([
    Container::STANDARD_ALIASES => [
        RequestInterface::class => Request::class,
        ResponseInterface::class => Response::class,
        ResponseFactoryInterface::class => Laminas\Diactoros\ResponseFactory::class
    ]
]));

/**
* Step 2: Instantiate the Router.
*/

$router = new Router(new RouteCollector(), $container);
//$router->setBasePath('/'); If the router is installed in a directory, then you need to set the base path.

/**
* Step 3: Include the routes needed
*/

// Prints `Hello world!`.
$router->get('/hello-world/', function () {
    return 'Hello world!';
});
```

### Route Closure

In passing a closure as a route handler, you need to pass in two arguments: `Psr\Http\Message\ServerRequestInterface` 
and `Psr\Http\Message\ResponseInterface`. You can use `Qubus\Http\ServerRequest` and `Qubus\Http\Response` which 
satisfies both `Psr` contracts:

```php
<?php

declare(strict_types=1);

/**
* Step 1: Require autoloader and import a few needed classes.
*/

require('vendor/autoload.php');

use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ResponseFactoryInterface;
use Qubus\Http\Request;
use Qubus\Http\Response;
use Qubus\Http\ServerRequest;
use Qubus\Injector\Config\Factory;
use Qubus\Injector\Psr11\Container;
use Qubus\Routing\Route\RouteCollector;
use Qubus\Routing\Router;

$container = new Container(Factory::create([
    Container::STANDARD_ALIASES => [
        RequestInterface::class => Request::class,
        ResponseInterface::class => Response::class,
        ResponseFactoryInterface::class => Laminas\Diactoros\ResponseFactory::class
    ]
]));

/**
* Step 2: Instantiate the Router.
*/

$router = new Router(new RouteCollector(), $container);
//$router->setBasePath('/'); If the router is installed in a directory, then you need to set the base path.

/**
* Step 3: Include the routes needed
*/

// Get hello-world route.
$router->get('/hello-world/', function (ServerRequest $serverRequest, Response $response) {
    $response->getBody()->write('Hello World!');
    return $response;
});
```

## Route Setup

There are several different ways in which you can load your routes in Codefy and the [Injector](../dependency-injection.md) 
takes care of supplying the dependencies:

### File Routing

File based routing is the default way in which routes are loaded:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

use Application\Http\Middleware\AddHeaderMiddleware;

return function (\Qubus\Routing\Psr7Router $router) {
    $router->get('/', 'HomeController@index')->middleware(AddHeaderMiddleware::class);
};
```

Then you can add the route file(s) to the `withRouting` method of the application:

```php title="./bootstrap/app.php"
<?php

declare(strict_types=1);

use Application\Provider\DatabaseServiceProvider;
use Application\Provider\ViewServiceProvider;
use Codefy\Framework\Application as CodefyApp;
use Qubus\Exception\Data\TypeException;

use function Codefy\Framework\Helpers\env;

try {
    $app = CodefyApp::create(
        config: [
            'basePath' => env(key: 'APP_BASE_PATH', default: dirname(path: __DIR__))
        ]
    )
    ->withProviders([
        DatabaseServiceProvider::class,
        ViewServiceProvider::class,
    ])
    ->withSingletons([
        //
    ])
    ->withRouting(
        web: __DIR__ . '/../routes/web/web.php',
        api: __DIR__ . '/../routes/api/rest.php',
    )->return();

    $app->share(nameOrInstance: $app);

    return $app::getInstance();
} catch (TypeException $e) {
    return $e->getMessage();
}
```

### Service Provider Routing

Instead of adding your routes to `routes/web/web.php`, you can instead add them to 
`Application\Provider\WebRouteServiceProvider` using the boot method:

```php title="./src/Application/Provider/WebRouteServiceProvider.php"
<?php

declare(strict_types=1);

namespace Application\Provider;

use Application\Http\Middleware\AddHeaderMiddleware;
use Codefy\Framework\Support\CodefyServiceProvider;
use Qubus\Exception\Data\TypeException;
use Qubus\Routing\Router;

use function Codefy\Framework\Helpers\config;

final class WebRouteServiceProvider extends CodefyServiceProvider
{
    /**
     * @throws TypeException
     */
    public function boot(): void
    {
        if ($this->codefy->isRunningInConsole()) {
            return;
        }

        /** @var Router $router */
        $router = $this->codefy->make(name: 'router');

        $router->get('/', 'HomeController@index')->middleware(AddHeaderMiddleware::class);
    }
}
```

Then you can add the service provider to the `withProviders` method of the application:

```php title="./bootstrap/app.php"
<?php

declare(strict_types=1);

use Application\Provider\DatabaseServiceProvider;
use Application\Provider\ViewServiceProvider;
use Application\Provider\WebRouteServiceProvider;
use Codefy\Framework\Application as CodefyApp;
use Qubus\Exception\Data\TypeException;

use function Codefy\Framework\Helpers\env;

try {
    $app = CodefyApp::create(
        config: [
            'basePath' => env(key: 'APP_BASE_PATH', default: dirname(path: __DIR__))
        ]
    )
    ->withProviders([
        DatabaseServiceProvider::class,
        ViewServiceProvider::class,
        WebRouteServiceProvider::class,
    ])
    ->withSingletons([
        //
    ])->return();

    $app->share(nameOrInstance: $app);

    return $app::getInstance();
} catch (TypeException $e) {
    return $e->getMessage();
}
```

### Class Routing

One last method you can use to add routes is by creating route classes:

```php title="./src/Application/Http/Route/WebRoute.php"
<?php

declare(strict_types=1);

namespace Application\Http\Route;

use Application\Http\Middleware\AddHeaderMiddleware;
use Qubus\Routing\Psr7Router;

readonly class WebRoute
{
    public function __construct(public Psr7Router $router)
    {
    }

    public function handle(): void
    {
        $this->router->get('/', 'HomeController@index')->middleware(AddHeaderMiddleware::class);
    }
}
```

Or you can bypass adding a constructor and instead add the Router dependency to the `handle` method:

```php title="./src/Application/Http/Route/WebRoute.php"
<?php

declare(strict_types=1);

namespace Application\Http\Route;

use Application\Http\Middleware\AddHeaderMiddleware;
use Qubus\Routing\Psr7Router;

readonly class WebRoute
{ 
    public function handle(Psr7Router $router): void
    {
        $this->router->get('/', 'HomeController@index')->middleware(AddHeaderMiddleware::class);
    }
}
```

Then you can add the route class to the `withRouting` method of the application:

```php title="./bootstrap/app.php"
<?php

declare(strict_types=1);

use Application\Http\Route\WebRoute;
use Application\Provider\DatabaseServiceProvider;
use Application\Provider\ViewServiceProvider;
use Codefy\Framework\Application as CodefyApp;
use Qubus\Exception\Data\TypeException;

use function Codefy\Framework\Helpers\env;

try {
    $app = CodefyApp::create(
        config: [
            'basePath' => env(key: 'APP_BASE_PATH', default: dirname(path: __DIR__))
        ]
    )
    ->withProviders([
        DatabaseServiceProvider::class,
        ViewServiceProvider::class,
    ])
    ->withSingletons([
        //
    ])
    ->withRouting(
        class: [
            WebRoute::class,
        ],
    )->return();

    $app->share(nameOrInstance: $app);

    return $app::getInstance();
} catch (TypeException $e) {
    return $e->getMessage();
}
```

## Route Request

The example below shows how you can catch the request object.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

use Qubus\Http\Factories\JsonResponseFactory;

return function (\Qubus\Routing\Psr7Router $router) {
    $router->get('/', function (ServerRequest $serverRequest) {
        return JsonResponseFactory::create([
            'method'            => $serverRequest->getMethod(),
            'uri'               => $serverRequest->getUri(),
            'body'              => $serverRequest->getBody(),
            'parsedBody'        => $serverRequest->getParsedBody(),
            'headers'           => $serverRequest->getHeaders(),
            'queryParameters'   => $serverRequest->getQueryParams(),
            'attributes'        => $serverRequest->getAttributes()
        ]);
    });
};
```

## Route Response

The Router supports the following responses.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

use Qubus\Http\Factories\EmptyResponseFactory;
use Qubus\Http\Factories\HtmlResponseFactory;
use Qubus\Http\Factories\JsonResponseFactory;
use Qubus\Http\Factories\TextResponseFactory;
use Qubus\Http\Factories\XmlResponseFactory;

return function (\Qubus\Routing\Psr7Router $router) {
    $router->get('/empty', function () {
        return EmptyResponseFactory::create();
    });
    
    $router->get('/html/1', function () {
        return '<html>This is an HTML response.</html>';
    });

    $router->get('/html/2', function () {
        return HtmlResponseFactory::create(
            '<html>This is another HTML response.</html>',
            200,
            ['Content-Type' => ['application/xhtml+xml']]
        );
    });

    $router->get('/json', function () {
        return JsonResponseFactory::create(
            'This is a JSON response.',
            200,
            ['Content-Type' => ['application/hal+json']]
        );
    });

    $router->get('/text', function () {
        return TextResponseFactory::create(
            'This is a text response.',
            200,
            ['Content-Type' => ['text/csv']]
        );
    });

    $router->get('/xml', function () {
        return XmlResponseFactory::create(
            'This is an xml response.',
            200,
            ['Content-Type' => ['application/hal+xml']]
        );
    });
};
```

## Http Methods

Sometimes you might need to create a route that accepts multiple HTTP verbs. For this you can use the `map` method. 
However, If you need to match all HTTP verbs, you can use the `any` method.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->map(['GET', 'POST'], '/', function() {
        // ...
    });

    $router->any('test', function() {
        // ...
    });
};
```

### Http Verb Shortcuts

In most typical cases, you will only need to use one HTTP verb. The following can be used in those cases:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->get('test/route', function () {});
    $router->head('test/route', function () {});
    $router->post('test/route', function () {});
    $router->put('test/route', function () {});
    $router->patch('test/route', function () {});
    $router->delete('test/route', function () {});
    $router->options('test/route', function () {});
    $router->trace('test/route', function () {});
    $router->connect('test/route', function () {});
    $router->any('test/route', function () {});
};
```

## Route Parameters

Parameters can be defined on routes using the `{keyName}` syntax. When a route matches a contained parameter, 
an instance of the `RouteParams` object is passed to the action.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->map(['GET'], 'posts/{id}', function($id) {
        return $id;
    });
};
```

If you need to add constraints to a parameter, you can pass a regular expression pattern to the `where()` method of the 
defined Route:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    // the regex for 'id' is for ULID's
    $router->map(['GET'], 'post/{id}/comment/{commentKey}', function ($id, $commentKey) {
        return $id;
    })
    ->where(['id', '[0123456789ABCDEFGHJKMNPQRSTVWXYZ{26}$]+'])
    ->where(['commentKey', '[a-zA-Z]+']);
};
```

### Optional Route Parameters

Sometimes you may want to use optional route parameters. To achieve this, you can add a `?` after the parameter name:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->map(['GET'], 'posts/{id?}', function($id) {
        if (isset($id)) {
            // Parameter is set.
        } else {
            // Parameter is not set.
        }
    });
};
```

## Named Routes

Routes can be named so that their URL can be generated programmatically:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->map(['GET'], 'post/all', function () {})->name('posts.index');
};
```

```php title="./src/Application/Http/Controller/PostController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Http\BaseController;
use Psr\Http\Message\ResponseInterface;
use Qubus\Routing\Interfaces\ResourceController;

use function Codefy\Framework\Helpers\trans;
use function Codefy\Framework\Helpers\view;

class PostController extends BaseController implements ResourceController
{
    public function index(): ?ResponseInterface
    {
        return view(
            template: 'framework::post/index',
            data: [
                'title' => trans('Posts'),
                'url' => $this->router->url(name: 'posts.index'),
            ]
        );
    }

    ```
}
```

If the route requires parameters, you can pass an associative array as a second parameter:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->map(['GET'], 'post/{id}', function () {})->name('posts.show');
};
```

```php title="./src/Application/Http/Controller/PostController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Http\BaseController;
use Psr\Http\Message\ResponseInterface;
use Qubus\Routing\Interfaces\ResourceController;

use function Codefy\Framework\Helpers\trans;
use function Codefy\Framework\Helpers\view;

class PostController extends BaseController implements ResourceController
{
    public function show(string $id): ResponseInterface
    {
        return view(
            template: 'framework::post/index',
            data: [
                'title' => trans('Posts'),
                'url' => $this->router->url(name: 'posts.show', ['id' => $id]),
            ]
        );
    }

    ```
}
```

If a parameter fails the regex constraint applied, a `RouteParamFailedConstraintException` will be thrown.

## Route Groups

It is common to group similar routes behind a common prefix. This can be achieved using `RouteGroup`:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->group(['prefix' => 'page'], function (\Qubus\Routing\Route\RouteGroup $group) {
        $group->map(['GET'], '/route1/', function () {}); // `/page/route1/`
        $group->map(['GET'], '/route2/', function () {}); // `/page/route2/`
    });
};
```

### Namespaces

Another common use-case for route groups is assigning the same PHP namespace to a group of controllers using the 
`namespace` parameter in the group array:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->group(['namespace' => '\Mvc\App\MyControllers'], function (\Qubus\Routing\Route\RouteGroup $group) {
        // Controllers Within The "\Mvc\App\MyControllers" Namespace
    });
};
```

### Route Prefixes

The prefix group attribute may be used to prefix each route in the group with a given url. For example, you may want to 
prefix all route urls within the group with `admin`:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->group(['prefix' => 'admin'], function (\Qubus\Routing\Route\RouteGroup $group) {
        $group->get('/users/', function () {
            // Matches The "/admin/users/" URL
        });
    });
};
```

## Routing Middleware

PSR-7/15 Middleware can be added to both routes and groups.

### Adding Middleware to a route

At it's simplest, adding Middleware to a route can be done by passing an object to the `middleware()` method:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $middleware = new \Application\Http\Middleware\AddHeaderMiddleware('X-Key1', 'abc');

    $router->get('hello-world', '\Application\Http\Controller\HelloWorldController@sayHello')->middleware($middleware);
};
```

Multiple middleware can be added by passing more parameters to the `middleware()` method:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $header = new \Application\Http\Middleware\AddHeaderMiddleware('X-Key1', 'abc');
    $auth = new \Application\Http\Middleware\AuthMiddleware();
    
    $router->get('auth', '\Application\Http\Controller\TestController@testMethod')->middleware($header, $auth);
};
```

Or alternatively, you can also pass an array of middleware:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $header = new \Application\Http\Middleware\AddHeaderMiddleware('X-Key1', 'abc');
    $auth = new \Application\Http\Middleware\AuthMiddleware();
    
    $router->get('auth', '\Application\Http\Controller\TestController@testMethod')->middleware([$header, $auth]);
};
```

### Adding Middleware to all routes

If you would like to add a middleware that is going to affect all routes, then use the `setBaseMiddleware` method.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->setBaseMiddleware([
        new \Application\Http\Middleware\AddHeaderMiddleware('X-Key', 'abc'),
    ]);
};
```

Since all your routes may not be in one file, the alternative and recommended way of setting base middlewares is by 
setting them in the app config:

```php title="./config/app.php"
<?php

//....

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
],

//....
```

### Adding Middleware to a group

Middleware can also be added to a group. To do so you need to pass an array as the first parameter of the `group()` 
function instead of a string.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $header = new \Application\Http\Middleware\AddHeaderMiddleware('X-Key1', 'abc');

    $router->group(['prefix' => 'my-prefix', 'middleware' => $header]), function (\Qubus\Routing\Route\RouteGroup $group) {
        $group->map(['GET'], 'route1', function () {}); // `/my-prefix/route1`
        $group->map(['GET'], 'route2', function () {}); // `/my-prefix/route2`
    });
};
```

You can also pass an array of middleware if you need more than one:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $header = new \Application\Http\Middleware\AddHeaderMiddleware('X-Key1', 'abc');
    $auth = new \Application\Http\Middleware\AuthMiddleware();

    $router->group(['prefix' => 'my-prefix', 'middleware' => [$header, $auth]]), function (\Qubus\Routing\Route\RouteGroup $group) {
        $group->map(['GET'], 'route1', function () {}); // `/my-prefix/route1`
        $group->map(['GET'], 'route2', function () {}); // `/my-prefix/route2`
    });
};
```

### Defining Middleware on Controllers

You can also apply Middleware to Controllers. In order to do this your Controller must extend 
`Codefy\Framework\Http\BaseController`.

Middleware is added by calling the `middleware()` method in your Controller's `__constructor()`.

```php title="./src/Application/Http/Controller/DashboardController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Application\Http\Middleware\AddHeaderMiddleware;
use Application\Http\Middleware\AuthMiddleware;
use Codefy\Framework\Http\BaseController;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

class DashboardController extends BaseController
{
    public function __construct(
        SessionService $sessionService,
        Router $router,
        Renderer $view
    ) {
        // Add one at a time
        $this->middleware(new AddHeaderMiddleware('X-Key1', 'abc'));
        $this->middleware(new AuthMiddleware());

        // Add multiple with one method call
        $this->middleware([
            new AddHeaderMiddleware('X-Key1', 'abc'),
            new AuthMiddleware(),
        ]);
        
        parent::__construct($sessionService, $router, $view);
    }
}
```

By default, all Middlewares added via a Controller will affect all methods on that class. To limit what methods a 
Middleware should be applied to, you can use `only()` and `except()`:

```php title="./src/Application/Http/Controller/DashboardController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Application\Http\Middleware\AddHeaderMiddleware;
use Application\Http\Middleware\AuthMiddleware;
use Codefy\Framework\Http\BaseController;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

class DashboardController extends BaseController
{
    public function __construct(
        SessionService $sessionService,
        Router $router,
        Renderer $view
    ) {
        // Only apply to `send()` method
        $this->middleware(new AddHeaderMiddleware('X-Key1', 'abc'))->only('send');
    
        // Apply to all methods except `show()` method
        $this->middleware(new AuthMiddleware())->except('show');

        // Multiple methods can be provided in an array to both methods
        $this->middleware(new AuthMiddleware())->except(['send', 'show']);
        
        parent::__construct($sessionService, $router, $view);
    }
}
```

## Dispatching the Router

You can dispatch a router by using [Laminas SapiEmitter](https://github.com/laminas/laminas-httphandlerrunner/blob/master/src/Emitter/SapiEmitter.php) in combination with `ServerRequest` or use `ServerRequest` in 
combination with `HttpPublisher`.

```php
<?php

declare(strict_types=1);

/**
* Step 4: Dispath the router.
*/

use Qubus\Http\ServerRequest;
use Laminas\HttpHandlerRunner\Emitter\SapiEmitter as EmitResponse;

return (new EmitResponse)->emit(
    $router->match(
        ServerRequest::fromGlobals(
            $_SERVER,
            $_GET,
            $_POST,
            $_COOKIE,
            $_FILES
        )
    )
);

/**
* Or you can use the HttpPublisher:
*/

use Qubus\Http\ServerRequest;
use Qubus\Http\HttpPublisher;

return (new HttpPublisher)->publish(
    $router->match(
        ServerRequest::fromGlobals(
            $_SERVER,
            $_GET,
            $_POST,
            $_COOKIE,
            $_FILES
        )
    ),
    null
);
```

!!! note "Important"
    If you are using the [skeleton](https://github.com/codefyphp/skeleton) app, the dispatching of the router 
    is handled automatically.

## Dependency Injection Container

The router can also be used with a PSR-11 compatible Container (included with the framework) of your choosing. 
This allows you to type hint dependencies in your route closures or Controller methods.

To make use of a container, simply pass it as a parameter to the Router's constructor:

```php
<?php

declare(strict_types=1);

use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ResponseFactoryInterface;
use Qubus\Http\Request;
use Qubus\Http\Response;
use Qubus\Injector\Config\Factory;
use Qubus\Injector\Psr11\Container;
use Qubus\Routing\Route\RouteCollector;
use Qubus\Routing\Router;

$container = new Container(Factory::create([
    Container::STANDARD_ALIASES => [
        RequestInterface::class => Request::class,
        ResponseInterface::class => Response::class,
        ResponseFactoryInterface::class => Laminas\Diactoros\ResponseFactory::class
    ]
]));

$router = new Router(new RouteCollector(), $container);
```

After which, your route closures and Controller methods will be automatically type hinted:

```php
<?php

declare(strict_types=1);

$container = new Container(Factory::create([
    Container::STANDARD_ALIASES => [
        RequestInterface::class => Request::class,
        ResponseInterface::class => Response::class,
        ResponseFactoryInterface::class => Laminas\Diactoros\ResponseFactory::class
    ]


$testServiceInstance = new TestService();
$container->alias(TestService::class, $testServiceInstance);

$router = new Router(new RouteCollector(), $container);

$router->get('/my/route', function (TestService $service) {
    // $service is now the same object as $testServiceInstance
});
```

## Events

This section will help you understand how to register your own callbacks to events in the router. It will also cover 
the basics of event-handlers; how to use the handlers provided with the router and how to create your own custom 
event-handlers.

### Available Events

This section contains all available events that can be registered using the `RoutingEventHandler`.

All event callbacks will retrieve a `RoutingEventArgument` object as parameter. This object contains easy access to 
event-name, router- and request instance and any special event-arguments related to the given event. You can see what 
special event arguments each event returns in the list below.

| Name                       | Special arguments               | Description                                                                                                                       | 
|----------------------------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------| 
| `EVENT_ALL`                | -                               | Fires when a event is triggered.                                                                                                  |
| `EVENT_INIT`               | -                               | Fires when router is initializing and before routes <br/>are loaded.                                                              |
| `EVENT_LOAD`               | `loadedRoutes`                  | Fires when all routes have been loaded and rendered, <br/>just before the output is returned.                                     |
| `EVENT_ADD_ROUTE`          | `route`                         | Fires when route is added to the router.                                                                                          |
| `EVENT_BOOT`               | `bootmanagers`                  | Fires when the router is booting. This happens just <br/>before boot-managers are rendered and before any routes has been loaded. |
| `EVENT_RENDER_BOOTMANAGER` | `bootmanagers`<br>`bootmanager` | Fires before a boot-manager is rendered.                                                                                          |
| `EVENT_LOAD_ROUTES`        | `routes`                        | Fires when the router is about to load all routes.                                                                                |
| `EVENT_FIND_ROUTE`         | `name`                          | Fires whenever the `has` method is used.                                                                                          |
| `EVENT_GET_URL`            | `name`<br>`params`              | Fires whenever the `Router::url` method is called <br/>and the router tries to find the route.                                    |
| `EVENT_MATCH_ROUTE`        | `route`                         | Fires when a route is matched and valid <br/>(correct request-type etc). and before the route is rendered.                        |
| `EVENT_RENDER_MIDDLEWARES` | `route`<br>`middlewares`        | Fires before middlewares for a route is rendered.                                                                                 |

To register a new event you need to create a new instance of `Qubus\Routing\Events\RoutingEventHandler` object. You can 
add as many callbacks as you like by calling the `registerEvent` method.

When you've registered events, make sure to add it to your routes file by calling the `addEventHandler` method from the 
router. It's recommend that you add your event-handlers within `routes/web/web.php`.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

use Qubus\Routing\Events\RoutingEventHandler;
use Qubus\Routing\Events\RoutingEventArgument;

return (function(\Qubus\Routing\Psr7Router $router) {
    // --- your routes go here ---

    $eventHandler = new RoutingEventHandler();
    
    // Add event that fires when a route is rendered
    $eventHandler->register(RoutingEventHandler::EVENT_ADD_ROUTE, function(RoutingEventArgument $argument) {
    
        // Get the route by using the special argument for this event.
        $route = $argument->route;
        
        // DO STUFF...
    
    });
    
    $router->addEventHandler($eventHandler);
});
```

### Custom EventHandlers

`Qubus\Routing\Events\RoutingEventHandler` is the class that manages events and must inherit from the 
`Qubus\Routing\Events\EventHandler` contract. The handler knows how to handle events for the given handler type.

Most of the time the basic `Qubus\Routing\Events\RoutingEventHandler` class will be more than enough for most people as 
you simply register an event which fires when triggered.

Let's go over how to create your very own event handler class.

Below is a basic example of a custom event-handler called `DatabaseDebugHandler`. The idea of the example below is to 
log all events to the database when triggered. Hopefully this is enough to give you an idea of how event handlers work.

```php title="./src/Infrastructure/Service/DatabaseDebugHandler.php"
<?php

declare(strict_types=1);

namespace Infrastructure\Service;

use Qubus\Routing\Events\EventHandler;
use Qubus\Routing\Events\RoutingEventArgument;
use Qubus\Routing\Psr7Router;

class DatabaseDebugHandler implements EventHandler
{
    /**
     * Debug callback
     * @var \Closure
     */
    protected $callback;

    public function __construct()
    {
        $this->callback = function (RoutingEventArgument $argument) {
            // todo: store log in database
        };
    }

    /**
     * Get events.
     *
     * @param string|null $name Filter events by name.
     * @return array
     */
    public function getEvents(?string $name): array
    {
        return [
            $name => [
                $this->callback,
            ],
        ];
    }

    /**
     * Fires any events registered with given event name
     *
     * @param Router $router Router instance
     * @param string $name Event name
     * @param array ...$eventArgs Event arguments
     */
    public function fireEvents(Psr7Router $router, string $name, ...$eventArgs): void
    {
        $callback = $this->callback;
        $callback(new RoutingEventArgument($router, $eventArgs));
    }

    /**
     * Set debug callback
     *
     * @param \Closure $event
     */
    public function setCallback(\Closure $event): void
    {
        $this->callback = $event;
    }
}
```

## BootManager with URL Rewriting

Sometimes you might find it necessary to store urls in a database, file or similar. In this example, we want the 
url `/router/article/view/1/` to load the route `/router/hello-world/` which the router knows, because it's defined 
in the routing file (i.e. `routes/web/web.php`). Please note that the `/router` part of the url is an example of when 
the route is installed in a subdirectory. For this example, the route is installed in a subdirectory named `router`.

To interfere with the router, we create a class that implements the `Qubus\Routing\Interfaces\BootManager` interface. 
This class will be loaded before any other rules in `routes/web/web.php` and allow us to "change" the current route, 
if any of our criteria are fulfilled (like coming from the url `/router/article/view/1/`).

```php title="./src/Infrastructure/Service/CustomRouterRules.php"
<?php

declare(strict_types=1);

namespace Infrastructure\Service;

use Psr\Http\Message\RequestInterface;
use Qubus\Routing\Interfaces\BootManager;
use Qubus\Routing\Psr7Router;

class CustomRouterRules implements BootManager
{
    /**
     * Called when router is booting and before the routes are loaded.
     *
     * @param \Qubus\Routing\Psr7Router $router
     * @param \Psr\Http\Message\RequestInterface $request
     */
    public function boot(Psr7Router $router, RequestInterface $request): void
    {
        $rewriteRules = [
            '/router/article/view/1/' => '/router/hello-world/'
        ];

        foreach ($rewriteRules as $url => $rule) {
            /**
             * If the current url matches the rewrite url, we use our custom route.
             */
            if ($request->getUrl()->getPath() === $url) {
                $request->setRewriteUrl($rule);
            }
        }
    }
}
```

The last thing you need to do, is to add your custom boot-manager to the `routes/web/web.php` file. You can create as 
many bootmanagers as you like and easily add them in your `routes/web/web.php` file.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

use Qubus\Routing\Events\RoutingEventHandler;
use Qubus\Routing\Events\RoutingEventArgument;

return (function(\Qubus\Routing\Psr7Router $router) {
    // --- your routes go here ---
    
    $router->addBootManager(new \App\Infrastructure\Services\CustomRouterRules());
});
```

## Misc.

If you return an instance of `Response` from your closure it will be sent back un-touched. If however you return 
something else, it will be wrapped in an instance of `Response` with your return value as the content.

### Responsable objects

If you return an object from your closure that implements the `Responsable` interface, it's `toResponse()` object will 
be automatically called for you.

```php title="./src/Infrastructure/Service/HelloWorldObject.php"
<?php

declare(strict_types=1);

namespace Infrastructure\Service;

use Laminas\Diactoros\Response\TextResponse;
use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;
use Qubus\Routing\Interfaces\Responsable;

class HelloWorldObject implements Responsable
{
    public function toResponse(RequestInterface $request): ResponseInterface
    {
        return new TextResponse('Hello World!');
    }
}
```

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return (function(\Qubus\Routing\Psr7Router $router) {
    $router->get('hello-world', function () {
        return new HelloWorldObject();
    });
});
```

### 404

If no route matches the request, a `Response` object will be returned with its status code set to `404`;

### Accessing Current Route

The currently matched `Route` can be retrieved by calling:

```php
<?php

$route = $router->currentRoute();
```

If no route matches or `match()` has not been called, `null` will be returned.

You can also access the name of the currently matched `Route` by calling:

```php
<?php

$name = $router->currentRouteName();
```

If no route matches or `match()` has not been called or the matched route has no name, `null` will be returned.

