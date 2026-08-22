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

Qubus Router is a PSR-7 and PSR-15 router with dependency-injected handlers, route and controller middleware, 
named routes, route groups, resource routes, domain and scheme matching, events, URL rewriting, and a 
Laravel-style route cache.

The package depends on PSR interfaces and provides integrations for 
[Qubus HTTP Component](../../digging-deeper/http/index.md) and 
[Qubus Injector](../dependency-injection.md). `match()` accepts any PSR-7 server request. The built-in response 
conversion and concrete request injection use the Qubus HTTP/Laminas implementations shipped with the package.

## Core concepts

A router application has four main pieces:

1. A `Qubus\Routing\Route\RouteCollector`, which performs the compiled route matching.
2. A PSR-11 `Psr\Container\ContainerInterface`, which resolves controller and handler dependencies.
3. A `Qubus\Routing\Router`, which registers routes and dispatches PSR-7 server requests.
4. Optionally, a PSR-17 `ResponseFactoryInterface`, which is required by redirect routes.

Routes are registered before the first call to `match()` or `url()`. Once routes have been compiled, attempts to add another route throw `TooLateToAddNewRouteException`.

Routes are evaluated in registration order. If more than one route can match the same method, host, scheme, and path, the first match wins.

Both trailing-slash and non-trailing-slash forms of a registered URI are accepted. Named-route generation uses the canonical trailing-slash form.

## Quick start

```php
<?php

declare(strict_types=1);

require __DIR__ . '/vendor/autoload.php';

use Laminas\Diactoros\ResponseFactory;
use Qubus\Http\ServerRequest;
use Qubus\Injector\Config\InjectorFactory;
use Qubus\Injector\Psr11\Container;
use Qubus\Routing\Route\RouteCollector;
use Qubus\Routing\Router;

$container = new Container(InjectorFactory::create());

$router = new Router(
    routeCollector: new RouteCollector(),
    container: $container,
    responseFactory: new ResponseFactory(),
);

$router->get('/hello-world', static function (): string {
    return 'Hello world!';
});

$request = new ServerRequest([], [], 'https://example.com/hello-world', 'GET');
$response = $router->match($request);
```

The `ResponseFactory` argument is optional unless the application uses `redirect()` or `permanentRedirect()`.

## Framework integration

When Qubus Router is used through the Codefy skeleton, the framework normally creates and shares the router through its router service provider. Dependencies typed as `Qubus\Routing\Router` can then be resolved by the application container.

The exact bootstrap API belongs to the Codefy framework rather than this package. A typical file-based configuration looks like this:

```php title="./bootstrap/app.php"
<?php

declare(strict_types=1);

use Application\Provider\DatabaseServiceProvider;
use Application\Provider\ViewServiceProvider;
use Codefy\Framework\Application as CodefyApp;

$app = CodefyApp::create(config: [
    'basePath' => dirname(__DIR__),
])
    ->withProviders([
        DatabaseServiceProvider::class,
        ViewServiceProvider::class,
    ])
    ->withRouting(
        web: __DIR__ . '/../routes/web/web.php',
        api: __DIR__ . '/../routes/api/rest.php',
    )
    ->return();

return $app;
```

Consult the Codefy's [configuration](../configuration.md) documentation if its bootstrap method signatures differ.

### Routes in a service provider

A Codefy application may register routes from a service provider instead of `withRouting()`. Resolve the concrete router during `boot()` and register all routes before the application dispatches a request:

```php title="./src/Application/Provider/WebRouteServiceProvider.php"
<?php

declare(strict_types=1);

namespace Application\Provider;

use Application\Http\Controller\HomeController;
use Application\Http\Middleware\AddHeaderMiddleware;
use Codefy\Framework\Support\CodefyServiceProvider;
use Qubus\Routing\Router;

final class WebRouteServiceProvider extends CodefyServiceProvider
{
    public function boot(): void
    {
        if ($this->codefy->isRunningInConsole()) {
            return;
        }

        /** @var Router $router */
        $router = $this->codefy->make(name: 'router');

        $router->get('/', [HomeController::class, 'index'])
            ->middleware(AddHeaderMiddleware::class);
    }
}
```

Add that provider to the application's provider list. Do not also register the same route file unless duplicate routes are intentional.

### Routes in a class

Applications that organize routes as classes can inject the router through the constructor:

```php title="./src/Application/Http/Route/WebRoutes.php"
<?php

declare(strict_types=1);

namespace Application\Http\Route;

use Application\Http\Controller\HomeController;
use Qubus\Routing\Router;

final readonly class WebRoutes
{
    public function __construct(private Router $router)
    {
    }

    public function handle(): void
    {
        $this->router->get('/', [HomeController::class, 'index']);
    }
}
```

Also invoking `handle()` through its container, method injection is also possible:

```php
final readonly class WebRoutes
{
    public function handle(Router $router): void
    {
        $router->get('/', [HomeController::class, 'index']);
    }
}
```

A supporting Codefy version can receive the class through `withRouting()`:

```php
->withRouting(class: [
    WebRoutes::class,
])
```

## Registering routes

Every route registration method returns a `Qubus\Routing\Interfaces\Routable`, implemented by `Qubus\Routing\Route\Route`. The returned route can be configured fluently with a name, middleware, constraints, a namespace, a domain, a subdomain, or an allowed scheme.

```php
$router->get('/users/{id}', 'UserController@show')
    ->name('users.show')
    ->where('id', '[0-9]+')
    ->middleware('auth');
```

Leading slashes are optional when registering a route:

```php
$router->get('/users', $handler);
$router->get('users', $handler);
```

Both declarations target the same path.

### Supported handler forms

Handlers may be closures, callable functions, controller strings, controller arrays, callable objects, or invokable controller class names.

```php
use Application\Http\Controller\HealthController;
use Application\Http\Controller\UserController;

// Closure.
$router->get('/closure', static fn (): string => 'ok');

// Callable function name.
$router->get('/upper/{string}', 'strtoupper');

// Controller string.
$router->get('/users/{id}', UserController::class . '@show');

// Controller class and non-static method.
$router->get('/users/{id}/edit', [UserController::class, 'edit']);

// Callable object.
$router->post('/webhook', new WebhookHandler());

// An invokable controller resolved from the container.
$router->get('/health', HealthController::class);
```

Controller objects are created lazily. Controller strings, non-static controller arrays, and invokable controller class names are resolved through the router's PSR-11 container when the route is dispatched.

The following invokable controller can therefore receive constructor dependencies:

```php title="./src/Application/Http/Controller/HealthController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

final readonly class HealthController
{
    public function __construct(private HealthService $health)
    {
    }

    public function __invoke(): string
    {
        return $this->health->isHealthy() ? 'ok' : 'unhealthy';
    }
}
```

### Default controller namespace

Set a default namespace when controller strings should use short class names:

```php
$router->setDefaultNamespace('Application\\Http\\Controller');

$router->get('/users/{id}', 'UserController@show');
```

Fully qualified class names continue to work when a default namespace is configured.

## HTTP methods

The router provides shortcuts for common and extended HTTP methods:

```php
$router->get('/items', $handler);
$router->head('/items', $handler);
$router->post('/items', $handler);
$router->put('/items/{id}', $handler);
$router->patch('/items/{id}', $handler);
$router->delete('/items/{id}', $handler);
$router->options('/items', $handler);
$router->trace('/diagnostics', $handler);
$router->connect('/tunnel', $handler);
```

Use `map()` for more than one method:

```php
$router->map(['PUT', 'PATCH'], '/items/{id}', [ItemController::class, 'update']);
```

Method names are normalized to uppercase and matched exactly.

`HEAD` does not automatically fall back to a `GET` route. Register a `HEAD` route explicitly, or include both methods with `map()`, when clients need it.

Use `any()` to register all methods known to the router: `GET`, `HEAD`, `POST`, `PUT`, `PATCH`, `DELETE`, `OPTIONS`, `CONNECT`, and `TRACE`.

```php
$router->any('/diagnostics', DiagnosticsController::class);
```

### HTTP method override

A `POST` request may override its method with either the `X-HTTP-Method-Override` header or a string `_method` value in the parsed body. The header takes precedence.

```http
POST /items/42 HTTP/1.1
X-HTTP-Method-Override: DELETE
```

```php
// For an HTML form body parsed by the PSR-7 request implementation:
['_method' => 'PATCH']
```

Only syntactically valid HTTP method tokens are accepted. Non-string body values are ignored. Method overriding is applied only to incoming `POST` requests.

## Route parameters

Define a route parameter with `{name}`. Parameter names must contain letters or digits.

```php
$router->get('/posts/{postId}/comments/{commentId}',
    static function (int $postId, int $commentId): string {
        return "Post {$postId}, comment {$commentId}";
    }
);
```

Matched parameters are passed to handlers by name. Handler argument order does not have to match URI parameter order:

```php
$router->get('/posts/{postId}/comments/{commentId}',
    static function (int $commentId, int $postId): string {
        return "{$postId}:{$commentId}";
    }
);
```

Scalar type declarations are honored by the underlying invoker where conversion is possible.

### Parameter constraints

Call `where()` with a parameter name and regular-expression fragment:

```php
$router->get('/posts/{id}', [PostController::class, 'show'])
    ->where('id', '[0-9]+');
```

Use an associative array to add several constraints at once:

```php
$router->get('/posts/{postId}/comments/{commentKey}', $handler)
    ->where([
        'postId' => '[0-9]+',
        'commentKey' => '[A-Za-z]+',
    ]);
```

Pass only the regular-expression body. Do not include delimiters such as `/.../`.

When generating a URL, a supplied value that fails its route constraint causes `RouteParamFailedConstraintException`.

### ULID example

```php
$router->get('/posts/{id}', [PostController::class, 'show'])
    ->where('id', '[0-9A-HJKMNP-TV-Z]{26}');
```

### Optional parameters

Append `?` to the parameter name and give the corresponding handler argument a default value:

```php
$router->get('/posts/{id?}',
    static function (?string $id = null): string {
        return $id === null ? 'All posts' : "Post {$id}";
    }
);
```

Optional segments work best at the end of a route.

### Catch-all and raw regular-expression routes

Use `*` as a catch-all path and register it after more specific routes:

```php
$router->any('*', NotFoundController::class);
```

An advanced route URI beginning with `@` is treated as a raw regular expression:

```php
$router->get('@^legacy/(?P<slug>[a-z0-9-]+)$',
    static fn (string $slug): string => $slug
);
```

Raw patterns are placed between the collector's delimiters and are not automatically anchored. Supply `^` and `$` when a full-path match is required. Prefer `{parameter}` plus `where()` for ordinary application routes because it is easier to read, reverse, and cache safely.

### Accessing all parameters

The matched `RouteParams` object is attached to the request. It is iterable, supports property-style lookup, and can be converted to an array:

```php
use Qubus\Http\ServerRequest;
use Qubus\Routing\Route\RouteAttributes;
use Qubus\Routing\Route\RouteParams;

$router->get('/posts/{id}',
    static function (ServerRequest $request, string $id): string {
        /** @var RouteParams $params */
        $params = $request->getAttribute(RouteAttributes::PARAMS);

        return $params->id . ':' . $params->toArray()['id'];
    }
);
```

## Dependency injection

The router creates an invoker around the PSR-11 container passed to its constructor. Route parameters, the active PSR-7 server request, and container services can be combined in the same closure or controller method.

```php
use Qubus\Http\ServerRequest;

$router->get('/posts/{id}',
    static function (
        ServerRequest $request,
        PostRepository $posts,
        int $id,
    ): string {
        return $posts->find($id)->title;
    }
);
```

Constructor injection works for controller handlers:

```php
final readonly class PostController
{
    public function __construct(private PostRepository $posts)
    {
    }

    public function show(int $id): string
    {
        return $this->posts->find($id)->title;
    }
}

$router->get('/posts/{id}', [PostController::class, 'show']);
```

The request resolver can also supply a custom request subtype if it can be constructed from the current request.

### Configuring Qubus Injector

Use `InjectorFactory` and constants from `Qubus\Injector\Injector`; older examples that use `Qubus\Injector\Config\Factory` or constants on `Container` are obsolete.

```php
use Laminas\Diactoros\ResponseFactory;
use Psr\Http\Message\ResponseFactoryInterface;
use Qubus\Injector\Config\InjectorFactory;
use Qubus\Injector\Injector;
use Qubus\Injector\Psr11\Container;

$container = new Container(InjectorFactory::create([
    Injector::STANDARD_ALIASES => [
        ResponseFactoryInterface::class => ResponseFactory::class,
    ],
    Injector::ARGUMENT_DEFINITIONS => [
        Mailer::class => [
            ':dsn' => 'smtp://localhost',
        ],
    ],
]));
```

Use the container's `define()`, `share()`, and alias APIs when application services require more detailed configuration.

## Requests and route attributes

A handler may type-hint the concrete `Qubus\Http\ServerRequest` class to receive the current request data. This includes attributes added by the router:

```php
use Qubus\Http\Factories\JsonResponseFactory;
use Qubus\Http\ServerRequest;

$router->get('/request', static function (ServerRequest $request) {
    return JsonResponseFactory::create([
        'method' => $request->getMethod(),
        'uri' => (string) $request->getUri(),
        'headers' => $request->getHeaders(),
        'query' => $request->getQueryParams(),
        'parsedBody' => $request->getParsedBody(),
        'attributes' => $request->getAttributes(),
    ]);
});
```

Before the handler and route middleware run, the router adds these attributes:

| Constant                   | Attribute key          | Value                        |
|----------------------------|------------------------|------------------------------|
| `RouteAttributes::ROUTE`   | `routing.route`        | Matched `Route` object       |
| `RouteAttributes::PARAMS`  | `routing.params`       | Matched `RouteParams` object |
| `RouteAttributes::URI`     | `routing.uri`          | Registered route URI         |
| `RouteAttributes::METHODS` | `routing.methods`      | Allowed method array         |
| `RouteAttributes::NAME`    | `routing.route_name`   | Route name or `null`         |
| `Router::class`            | `Qubus\Routing\Router` | Matched `Route` object       |

```php
use Qubus\Http\ServerRequest;
use Qubus\Routing\Route\Route;
use Qubus\Routing\Route\RouteAttributes;

$router->get('/account', static function (ServerRequest $request): string {
    /** @var Route $route */
    $route = $request->getAttribute(RouteAttributes::ROUTE);

    return $route->getActionName();
});
```

## Handler return values and responses

A route handler may return:

- a `Psr\Http\Message\ResponseInterface`, returned unchanged;
- a `Psr\Http\Message\StreamInterface`;
- a string, wrapped in an HTML response;
- an object implementing `Qubus\Routing\Interfaces\Responsable`;
- `null`, an empty string, or the string `"0"`, converted to an empty `204` response.

```php
use Laminas\Diactoros\Response\JsonResponse;
use Laminas\Diactoros\Response\TextResponse;

$router->get('/text', static fn () => new TextResponse('Hello'));
$router->get('/json', static fn () => new JsonResponse(['status' => 'ok']));
$router->delete('/items/{id}', static function (): void {
    // A void/null return becomes a 204 response.
});
```

Returning an unsupported type, such as an arbitrary array or integer, is not automatically converted. Return a PSR-7 response or encode the value explicitly.

### Responsable objects

```php title="./src/Application/Http/Response/PostResponse.php"
<?php

declare(strict_types=1);

namespace Application\Http\Response;

use Laminas\Diactoros\Response\JsonResponse;
use Psr\Http\Message\RequestInterface;
use Psr\Http\Message\ResponseInterface;
use Qubus\Routing\Interfaces\Responsable;

final readonly class PostResponse implements Responsable
{
    public function __construct(private array $post)
    {
    }

    public function toResponse(RequestInterface $request): ResponseInterface
    {
        return new JsonResponse($this->post);
    }
}
```

```php
$router->get('/posts/{id}',
    static fn (PostRepository $posts, int $id) => new PostResponse($posts->find($id))
);
```

## Named routes and URL generation

Assign a unique route name with `name()`:

```php
$router->get('/posts/{id}', [PostController::class, 'show'])
    ->name('posts.show')
    ->where('id', '[0-9]+');
```

Generate its canonical URL with `url()`:

```php
$url = $router->url('posts.show', ['id' => 42]);
// /posts/42/
```

Use `has()` to check whether a route name has been registered:

```php
if ($router->has('posts.show')) {
    // ...
}
```

Important behavior:

- A route may be named only once. Renaming it throws `RouteNameRedefinedException`.
- Names must be unique in the compiled route collection.
- Unknown names throw `NamedRouteNotFoundException`.
- Values supplied to `url()` are checked against `where()` constraints.
- Calling `url()` compiles the route collection. Register all routes before generating URLs.

## Base paths

Use a base path when the application is mounted below the host root:

```php
$router->setBasePath('/my-application');
$router->get('/dashboard', DashboardController::class);
```

The route matches `/my-application/dashboard`, not `/dashboard` or an unrelated prefix. `prependUrl()` is an alias-style entry point that updates the same router base path.

```php
echo $router->getBasePath(); // /my-application/
```

Changing the base path after a match resets and recompiles the route collector.

## Domains, subdomains, and schemes

Restrict a route to a host with `domain()`:

```php
$router->get('/billing', BillingController::class)
    ->domain('accounts.example.com');
```

Combine a base domain and subdomain:

```php
$router->get('/dashboard', TenantDashboardController::class)
    ->domain('example.com')
    ->subDomain('tenant');
```

This route matches `tenant.example.com`.

Restrict the URI scheme with `setScheme()`:

```php
$router->post('/payments', PaymentController::class)
    ->setScheme('https');
```

Several schemes may be supplied:

```php
$route->setScheme('http', 'https');
```

Including a scheme in `domain()` records both restrictions:

```php
$router->get('/account', AccountController::class)
    ->domain('https://secure.example.com')
    ->name('account');

echo $router->url('account');
// https://secure.example.com/account/
```

Domain and scheme rules are enforced per route, so the same path may safely be registered for different hosts.

## Redirect routes

Redirect routes require a PSR-17 response factory in the router constructor.

```php
use Laminas\Diactoros\ResponseFactory;

$router = new Router(
    new RouteCollector(),
    $container,
    new ResponseFactory(),
);

$router->redirect('/old', '/new');        // 302
$router->redirect('/old-temp', '/new', 307);
$router->permanentRedirect('/legacy', '/new'); // 301
```

The destination is written to the response's `Location` header.

## Route groups

Groups apply a prefix, middleware, namespace, domain, and/or subdomain to several routes.

```php
use Qubus\Routing\Route\RouteGroup;

$router->group([
    'prefix' => 'admin',
    'namespace' => 'Application\\Http\\Controller\\Admin',
    'middleware' => ['auth', 'role:admin'],
    'domain' => 'example.com',
    'subdomain' => 'control',
], static function (RouteGroup $group): void {
    $group->get('/users', 'UserController@index')->name('admin.users.index');
    $group->get('/users/{id}', 'UserController@show')->name('admin.users.show');
});
```

The first route above matches `control.example.com/admin/users`.

A string group argument is shorthand for a prefix:

```php
$router->group('admin', static function (RouteGroup $group): void {
    $group->get('/dashboard', DashboardController::class);
});
```

### Nested groups

Groups can be nested. Prefixes are inherited and combined:

```php
$router->group(['prefix' => 'api'], static function (RouteGroup $api): void {
    $api->group(['prefix' => 'v1'], static function (RouteGroup $v1): void {
        $v1->get('/users', [UserController::class, 'index']);
        // /api/v1/users
    });
});
```

If a nested array group omits `prefix`, it retains the outer prefix.

Only prefixes are inherited automatically by nested groups. Repeat outer `middleware`, `namespace`, `domain`, and `subdomain` values in the nested group when those rules must continue to apply.

## Middleware

The router uses Relay to execute PSR-15 middleware. Middleware is executed in this order:

1. Router-wide base middleware.
2. Middleware assigned directly to the route, in registration order.
3. Middleware supplied by the matched controller.
4. The route handler.

Middleware may be a callable, a PSR-15 middleware instance, a class name, or a container alias understood by the configured `MiddlewareResolver`.

### Route middleware

```php
$router->get('/account', AccountController::class)
    ->middleware(new AddHeaderMiddleware('X-Route', 'account'));
```

Pass more than one value:

```php
$router->get('/account', AccountController::class)
    ->middleware($authentication, $authorization);
```

Or pass an array:

```php
$router->get('/account', AccountController::class)
    ->middleware([$authentication, $authorization]);
```

Repeated calls append middleware rather than replacing earlier entries.

### Base middleware

`Router` currently exposes base middleware through its `baseMiddleware` property:

```php
$router->baseMiddleware = [
    'request-id',
    'security-headers',
];
```

There is no `setBaseMiddleware()` method in the standalone router API. Framework integrations may offer their own configuration helper, such as a `base_middlewares` configuration key.

### Group middleware

```php
$router->group([
    'prefix' => 'admin',
    'middleware' => ['auth', 'role:admin'],
], static function (RouteGroup $group): void {
    $group->get('/dashboard', DashboardController::class);
});
```

The `middleware` value can be one definition or an array of definitions.

### Middleware aliases and arguments

The default `InjectorMiddlewareResolver` resolves aliases through the PSR-11 container. A definition can include comma-separated positional arguments after `:`:

```php
$route->middleware('throttle:60,1');
```

If the middleware exposes `withArguments()`, the resolver passes positional arguments to it.

Named options are also supported:

```php
$route->middleware('roles:role=admin,redirect=/forbidden');
```

If the middleware exposes `withOptions()`, it receives the parsed associative options. Commas separate entries, so option values themselves should not contain an unescaped comma.

For an alias to work, `ContainerInterface::has($alias)` must return `true`, and `get($alias)` must return a `MiddlewareInterface`.

!!! note "Middleware class names"
A direct middleware class-name string is instantiated with `new ClassName()` by the default resolver. Use a container alias when middleware needs constructor dependencies.

### Controller middleware

Standalone controllers can extend `Qubus\Routing\Controller\Controller` to provide middleware:

```php title="./src/Application/Http/Controller/DashboardController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Qubus\Routing\Controller\Controller;

final class DashboardController extends Controller
{
    public function __construct()
    {
        $this->middleware('auth');
        $this->middleware('audit')->only('update');
        $this->middleware('read-only')->except(['store', 'update', 'destroy']);
    }

    public function index(): string
    {
        return 'Dashboard';
    }

    public function update(): string
    {
        return 'Updated';
    }
}
```

`only()` and `except()` accept a method name or an array of method names. Middleware without either option applies to every routed method on the controller.

Framework base controllers may already implement `ControllerMiddlewareDelegate`; use their middleware API when applicable.

## Resource routes

`resource()` registers the conventional seven controller actions.

```php
$router->resource('posts', PostController::class);
```

The default route set is:

| Method         | URI                   | Controller action | Route name      |
|----------------|-----------------------|-------------------|-----------------|
| `GET`          | `/posts`              | `index`           | `posts.index`   |
| `GET`          | `/posts/create`       | `create`          | `posts.create`  |
| `POST`         | `/posts`              | `store`           | `posts.store`   |
| `GET`          | `/posts/{posts}`      | `show`            | `posts.show`    |
| `GET`          | `/posts/{posts}/edit` | `edit`            | `posts.edit`    |
| `PUT`, `PATCH` | `/posts/{posts}`      | `update`          | `posts.update`  |
| `DELETE`       | `/posts/{posts}`      | `destroy`         | `posts.destroy` |

The default parameter name is derived from the resource name. Override it when a singular parameter is preferred:

```php
$router->resource('posts', PostController::class, [
    'parameters' => ['posts' => 'post'],
]);
```

### Limiting resource actions

```php
$router->resource('posts', PostController::class, [
    'only' => ['index', 'show'],
]);

$router->resource('comments', CommentController::class, [
    'except' => ['create', 'edit'],
]);
```

### Resource options

Supported options include:

| Option        | Purpose                                            |
|---------------|----------------------------------------------------|
| `only`        | Register only the listed actions.                  |
| `except`      | Exclude the listed actions.                        |
| `parameters`  | Map resource names to parameter names.             |
| `names`       | Replace all or selected generated route names.     |
| `alias`       | Prefix generated route names.                      |
| `namespace`   | Apply a controller namespace.                      |
| `middlewares` | Apply middleware to generated routes.              |
| `domain`      | Restrict generated routes to a domain.             |
| `subdomain`   | Restrict generated routes to a subdomain.          |
| `shallow`     | Use shallow naming/URIs for nested member actions. |

```php
$router->resource('admin/posts', 'PostController', [
    'namespace' => 'Application\\Http\\Controller\\Admin',
    'middlewares' => ['auth', 'role:admin'],
    'parameters' => ['posts' => 'post'],
    'alias' => 'control',
]);
```

A slash in the resource name creates a URI prefix. Dot-separated names are used by the resource builder for nested resources.

Register several resources with shared options:

```php
$router->resources([
    'posts' => PostController::class,
    'comments' => CommentController::class,
], [
    'middlewares' => ['auth'],
]);
```

### API resources

`apiResource()` omits the HTML-oriented `create` and `edit` routes:

```php
$router->apiResource('posts', PostApiController::class);
```

It registers `index`, `show`, `store`, `update`, and `destroy`. Use `apiResources()` to register a map of API resources.

The package provides `ResourceController` and `ApiResourceController` interfaces as optional controller contracts.

### Global resource customization

```php
use Qubus\Routing\Route\RouteResource;

RouteResource::setParameters([
    'people' => 'person',
]);

RouteResource::methodActionNames([
    'create' => 'new',
    'edit' => 'change',
]);
```

These settings are static and affect resource routes registered afterward.

## Loading route sources

`RoutingRegistrar` can load PHP files, JSON files, callables, or an array containing any of those sources.

```php
use Qubus\Routing\Route\RoutingRegistrar;

$routes = new RoutingRegistrar($router);
$routes->load([
    __DIR__ . '/routes/web.php',
    __DIR__ . '/routes/api.json',
    static function (Router $router): void {
        $router->get('/health', HealthController::class);
    },
]);
```

It can also apply a prefix and middleware while loading sources:

```php
$routes->group(
    sources: __DIR__ . '/routes/admin.php',
    middleware: ['auth', 'role:admin'],
    prefix: 'admin',
);
```

### PHP route files

A PHP route file should always return a callable:

```php title="./routes/web.php"
<?php

declare(strict_types=1);

use Application\Http\Controller\HomeController;
use Qubus\Routing\Router;

return static function (Router $router): void {
    $router->get('/', [HomeController::class, 'index']);
};
```

The registrar requires the file and invokes its returned callable with the concrete `Router` instance.

### JSON route files

JSON route files require a top-level `routes` array:

```json
{
  "routes": [
    {
      "path": "/posts/{id}",
      "method": ["GET"],
      "callback": "Application\\Http\\Controller\\PostController@show",
      "name": "posts.show",
      "middlewares": ["auth"],
      "where": [
        {"id": "[0-9]+"}
      ]
    }
  ]
}
```

Supported route keys are `path`, `method`, `callback`, `name`, `middlewares`, `domain`, `subdomain`, `namespace`, and `where`. Set the router's default namespace before loading JSON when `callback` uses a short controller name; controller classes are validated as the route is created.

For a single constraint, `where` may alternatively be `['id', '[0-9]+']` in PHP array terms, represented in JSON as:

```json
"where": ["id", "[0-9]+"]
```

Nested JSON groups use a `group.routes` array:

```json
{
  "routes": [
    {
      "group": {
        "routes": [
          {
            "path": "/health",
            "method": ["GET"],
            "callback": "Application\\Http\\Controller\\HealthController@show"
          }
        ]
      }
    }
  ]
}
```

Malformed JSON throws `JsonException`. A readable JSON file without a top-level `routes` array throws `RuntimeException`.

## Route caching

Route caching is designed to behave like Laravel's route cache: once a current cache exists, cached definitions replace route definitions registered during normal bootstrap. Runtime-only services are reconstructed from the current application container.

Enable caching before the first `match()` or `url()` call:

```php
$router->enableRouteCache(__DIR__ . '/storage/cache/routes.php');
```

On the first dispatch, the router:

1. boots and compiles the registered routes;
2. exports a versioned definition for each route;
3. writes the PHP cache file atomically;
4. continues using the already-built in-memory collection.

On later processes, the router:

1. reads the cache file;
2. validates its format version;
3. reconstructs `Route` objects using the current invoker, container, and middleware resolver;
4. ignores newly registered bootstrap definitions in favor of the cache.

This avoids serializing the router's DI container, reflection cache, invoker, middleware resolver, and controller instances. Only route metadata plus action and middleware definitions are cached; values explicitly captured by an action closure remain part of that action.

### Cached route data

The cache preserves:

- HTTP methods and URI;
- the original route action;
- route name;
- domain, subdomain, and schemes;
- parameter constraints;
- effective controller namespace;
- route middleware.

Closures and closure middleware are encoded with `opis/closure`. Controller strings, controller arrays, invokable classes, and alias-based middleware are generally the most deployment-friendly definitions.

!!! warning "Closure captures"
Do not capture open resources, live database connections, service containers, reflection objects, or other non-portable runtime state in cached closures. Resolve services through handler parameters or the controller constructor instead.

### Cache lifecycle API

```php
$router->hasRouteCache();       // Is caching enabled on this Router instance?
$router->routeIsCached();       // Does the configured cache file currently exist?
$router->getRouteCachePath();   // Configured path, or null when disabled.
$router->clearRouteCache();     // Delete the configured cache file.
$router->disableRouteCache();   // Stop using caching on this Router instance.
```

Clear the cache during deployment whenever route files, handler definitions, middleware, names, constraints, domains, or group settings change:

```php
$router->enableRouteCache($cachePath);
$router->clearRouteCache();
```

The next application process rebuilds it. Old cache-format versions are rebuilt automatically, but a current-format cache is intentionally not invalidated by route-file timestamps.

`match()` and `url()` initialize the cached collection. `has()` only inspects the router's currently loaded definitions, so call it after cache initialization when an application skips normal route registration on cache hits.

The cache directory is created when necessary. Cache writes use a temporary file, an exclusive write lock, an atomic rename, and `0644` file permissions. The PHP process must have permission to create the directory and replace the cache file.

Keep the cache directory outside any user-upload area and do not allow untrusted users to write cache files: cache files are executable PHP loaded with `require`.

## Dispatching

### Direct dispatch

Pass a PSR-7 `ServerRequestInterface` to `match()`:

```php
use Qubus\Http\ServerRequestFactory;

$request = ServerRequestFactory::fromGlobals(
    server: $_SERVER,
    query: $_GET,
    body: $_POST,
    cookies: $_COOKIE,
    files: $_FILES,
);

$response = $router->match($request);
```

When no route matches, `match()` returns a JSON response with status `404`.

### Emitting the response

With Laminas HTTP Handler Runner:

```php
use Qubus\Http\Emitter\SapiEmitter;

$response = $router->match($request);
new SapiEmitter()->emit($response);
```

Or with Qubus HTTP Publisher:

```php
use Qubus\Http\HttpPublisher;

new HttpPublisher()->publish($router->match($request), null);
```

Codefy skeleton applications normally dispatch and emit the response automatically.

### PSR-15 middleware mode

`Router` implements `Psr\Http\Server\MiddlewareInterface`:

```php
$response = $router->process($request, $nextHandler);
```

If a route matches, its response is returned. If no route matches, the router delegates to `$nextHandler` and attaches the string `Not Found` under the `Router::class` request attribute.

## Current route

After a successful match:

```php
use Qubus\Routing\Route\Route;

/** @var Route|null $route */
$route = $router->currentRoute();
$name = $router->currentRouteName();
```

Both methods return `null` before matching. They also return `null` after an unsuccessful match; a failed match clears any route left from a previous dispatch. `currentRouteName()` additionally returns `null` when the matched route is unnamed.

The route object exposes useful inspection methods:

```php
$route->uri;
$route->methods;
$route->name;
$route->paramConstraints;
$route->getActionName();
$route->getDomain();
$route->getSubDomain();
$route->getSchemes();
$route->getNamespace();
$route->gatherMiddlewares();
```

## Events

Register event callbacks with `RoutingEventHandler`, then attach the handler with `setEventHandlers()`:

```php
use Qubus\Routing\Events\RoutingEventArgument;
use Qubus\Routing\Events\RoutingEventHandler;

$events = new RoutingEventHandler();

$events->register(
    RoutingEventHandler::EVENT_MATCH_ROUTE,
    static function (RoutingEventArgument $event): void {
        $route = $event->route;
        $router = $event->router;
        $request = $event->getRequest();
    }
);

$router->setEventHandlers($events);
```

`setEventHandlers()` appends a handler; it does not replace previously registered handlers. Use `getEventHandlers()` to inspect them.

### Available events

| Constant                   | Value                 | Special arguments                     | Timing                                                    |
|----------------------------|-----------------------|---------------------------------------|-----------------------------------------------------------|
| `EVENT_ALL`                | `*`                   | Depends on the event                  | Invoked for every fired event.                            |
| `EVENT_INIT`               | `onInit`              | none                                  | At the beginning of each `match()`.                       |
| `EVENT_BOOT`               | `onBoot`              | `bootmanagers`                        | Before boot managers execute during route compilation.    |
| `EVENT_RENDER_BOOTMANAGER` | `onRenderBootManager` | `bootmanagers`, `bootmanager`         | Immediately before each boot manager.                     |
| `EVENT_LOAD_ROUTES`        | `onLoadRoutes`        | `routes`                              | Before routes are registered with the collector.          |
| `EVENT_LOAD`               | `onLoad`              | `loadedRoutes` or `loadedCacheRoutes` | After normal routes or cached routes are loaded.          |
| `EVENT_ADD_ROUTE`          | `onAddRoute`          | `route`                               | When a route is hydrated into the router.                 |
| `EVENT_FIND_ROUTE`         | `onFindRoute`         | `name`                                | Whenever `has()` is called.                               |
| `EVENT_GET_URL`            | `onGetUrl`            | `name`, `parameters`                  | Before named URL generation.                              |
| `EVENT_MATCH_ROUTE`        | `onMatchRoute`        | `route`                               | After a route matches and before its middleware executes. |
| `EVENT_RENDER_MIDDLEWARES` | `onRenderMiddlewares` | `route`, `middlewares`                | Before the middleware pipeline executes.                  |

Special arguments are available as read-only dynamic properties and through `$event->arguments`:

```php
$events->register(RoutingEventHandler::EVENT_GET_URL,
    static function (RoutingEventArgument $event): void {
        $name = $event->name;
        $parameters = $event->parameters;
    }
);
```

Register an `EVENT_ALL` callback to observe every event. Its `$event->eventName` property identifies the actual event.

### Custom event handlers

A custom handler implements `Qubus\Routing\Events\EventHandler`:

```php
<?php

declare(strict_types=1);

namespace Infrastructure\Routing;

use Qubus\Routing\Events\EventHandler;
use Qubus\Routing\Events\RoutingEventArgument;
use Qubus\Routing\Router;

final class DatabaseDebugHandler implements EventHandler
{
    public function getEvents(?string $name = null): array
    {
        return [];
    }

    public function fireEvents(Router $router, string $name, array $eventArgs = []): void
    {
        $event = new RoutingEventArgument(
            eventName: $name,
            router: $router,
            arguments: $eventArgs,
        );

        // Persist the event name and selected arguments.
    }
}
```

## Boot managers and URL rewriting

A boot manager runs once while an uncached route collection is being built. It can add routes or set a rewrite URL on the router's Qubus request object.

```php title="./src/Infrastructure/Routing/LegacyUrlBootManager.php"
<?php

declare(strict_types=1);

namespace Infrastructure\Routing;

use Psr\Http\Message\RequestInterface;
use Qubus\Http\Request;
use Qubus\Routing\Interfaces\BootManager;
use Qubus\Routing\Router;

final class LegacyUrlBootManager implements BootManager
{
    public function boot(Router $router, RequestInterface $request): void
    {
        if (! $request instanceof Request) {
            return;
        }

        if ($request->getUrl()->getPath() === '/legacy/article/1') {
            $request->setRewriteUrl('/articles/1');
        }
    }
}
```

```php
$router->addBootManager(new LegacyUrlBootManager());
```

The router checks `getRewriteUrl()` before using the incoming PSR-7 request path.

!!! note "Boot managers and route cache"
Boot managers run when the route collection is built. A current route cache is imported directly, so boot managers are not rerun on a cache hit. Clear and rebuild the cache when a boot manager changes route definitions.

## Adding prebuilt routes

Advanced integrations can construct a `Route` and add it through `hydrateRoute()`:

```php
use Qubus\Routing\Route\Route;

$route = new Route(
    methods: ['GET'],
    uri: '/custom',
    action: static fn (): string => 'custom',
);

$router->hydrateRoute($route);
```

Prefer `get()`, `post()`, or `map()` in normal application code because they attach the router's invoker and middleware resolver automatically.

## Extending routing classes

`Router`, `Route`, and `RouteGroup` use Qubus Inheritance's `MacroAware` support. Applications can add project-specific fluent helpers without subclassing:

```php
use Qubus\Routing\Route\Route;

Route::macro('whereUlid', function (string $parameter = 'id'): Route {
    return $this->where($parameter, '[0-9A-HJKMNP-TV-Z]{26}');
});

$router->get('/posts/{id}', [PostController::class, 'show'])
    ->whereUlid();
```

Macros are static process state. Register them during application bootstrap before route files use them. The underlying macro package also supports mixin objects through `Route::mixin()`, `RouteGroup::mixin()`, and `Router::mixin()`.

## Errors and exceptions

Common routing exceptions include:

| Exception                             | Cause                                                          |
|---------------------------------------|----------------------------------------------------------------|
| `TooLateToAddNewRouteException`       | A route was added after compilation.                           |
| `RouteNameRedefinedException`         | `name()` was called twice on one route.                        |
| `NamedRouteNotFoundException`         | `url()` could not find the requested name.                     |
| `RouteParamFailedConstraintException` | A generated URL value failed `where()`.                        |
| `RouteParseException`                 | A controller string could not be parsed.                       |
| `RouteControllerNotFoundException`    | A controller class does not exist.                             |
| `RouteMethodNotFoundException`        | A controller method does not exist.                            |
| `TypeException`                       | Middleware or route configuration has an invalid type.         |
| `RuntimeException`                    | A route source or route-cache file is invalid or inaccessible. |

## Practical guidance

- Register specific static routes before broad parameter or wildcard routes.
- Give optional handler arguments default values.
- Prefer controller class names, controller arrays, invokable controllers, and middleware aliases in cached production applications.
- Resolve services through the container instead of capturing them in closures.
- Use `where()` to constrain identifiers and prevent broad routes from shadowing later routes.
- Name routes and generate URLs instead of hard-coding internal links.
- Clear the route cache as part of every deployment that changes routing behavior.
- Use a full request URI when testing domain or scheme restrictions.
- Use the concrete `Router` type when code needs registration, caching, events, resources, or inspection APIs not declared by the narrower `Psr7Router` interface.

