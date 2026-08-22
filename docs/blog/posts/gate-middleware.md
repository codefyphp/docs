---
title: How to Create a Gate Middleware - Checking User Permissions
description: Build reusable CodefyPHP gate middleware that checks route permissions, integrates UserAuth, and redirects unauthorized users.
summary: Build reusable CodefyPHP gate middleware that checks route permissions, integrates UserAuth, and redirects unauthorized users.
keywords: gate-middleware,user-permissions,codefyphp-rbac
date:
  created: 2025-10-18 13:15:00
links: 
  - getting-started/basics/middleware.md
  - getting-started/basics/rbac.md
authors: [nomadicjosh]
---

# How to Create a Gate Middleware: Checking User Permissions

Protecting the admin or backend of an application is one of the most important features of any website. But sometimes 
it can be a bit cumbersome to write the same boilerplate code for each controller method. In this article, I will show 
you how to create a gate middleware for checking user permissions via your routes.

<!-- more -->

## Currently

Currently, in your CodefyPHP controllers, you probably have some code that looks like this:

```php
<?php

public function profile(ServerRequest $request): ResponseInterface
{
    if (false === $this->user->can(permissionName: 'admin:dashboard', request: $request)) {
        return $this->redirect(url: site_url(path: $this->router->url(name: 'admin.login')));
    }

    //
}
```

It can be quite cumbersome to write those `if` lines over and over again throughout all your controllers. But there is 
a much easier way to handle this. This tutorial will take your through step by step on creating a gate middleware.

## Middleware Boilerplate

Ok, first we will start off with a simple foundation for our gate middleware, and then fill it in as we advance through 
the tutorial.

```php title="file: App/Infrastructure/Http/Middleware/GateMiddleware.php"
<?php

declare(strict_types=1);

namespace App\Infrastructure\Http\Middleware;

use App\Infrastructure\Services\UserAuth;
use Exception;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;
use Psr\Http\Server\MiddlewareInterface;
use Psr\Http\Server\RequestHandlerInterface;
use Qubus\Exception\Data\TypeException;
use Qubus\Http\Factories\JsonResponseFactory;
use Qubus\Http\Factories\RedirectResponseFactory;

class GateMiddleware implements MiddlewareInterface
{
    protected ?string $permission = null;
    protected ?string $redirect = null;

    public function __construct(protected UserAuth $user)
    {
    }

    public function withArguments(?string $permission = null, ?string $redirect = null): static
    {
    }

    /**
     * @inheritDoc
     * @throws TypeException
     * @throws Exception
     */
    public function process(ServerRequestInterface $request, RequestHandlerInterface $handler): ResponseInterface
    {
        // TODO: Implement process() method.
    }
}
```

Ok, lets break down what we have so far. We have two properties `$this->permission` and `$this->redirect`. The permission 
property is the `permission` the gate will check for, and the `redirect` property is the `uri` the user should be forwarded to 
if the user doesn't have the stated permission.

As you can see, the `permission` and `redirect` properties are not injected into the constructor. That is because we want 
those properties to be somewhat dynamic. So, instead, they are parameters for the `withArguments()` method. We will pass 
in those arguments when we add the middleware to our route(s) and the middleware resolver will resolve those arguments 
automatically.

## UserAuth

We inject the `App\Infrastructure\Services\UserAuth` class so that we have access to the `can()` method which checks 
the user permission. The `UserAuth` class get resolved by the container.

## withArguments()

Now, lets work on filling in the `withArguments()` method:

```php
<?php

public function withArguments(?string $permission = null, ?string $redirect = null): static
{
    $clone = clone $this;
    $clone->permission = $permission;
    $clone->redirect = $redirect;
    
    return $clone;
}
```

We are cloning the object (`$this`) because we need the middleware to be immutable (one object) so that when we call our 
properties later on, they are filled with the information we need.

## process()

Next, we need to implement the `process()` method which fulfills the `Psr\Http\Server\MiddlewareInterface` contract.

First, we should check to see if the `permission` property is `null`. If it is, then we need to return a response with 
a proper message:

```php
<?php

/**
 * @inheritDoc
 * @throws TypeException
 * @throws Exception
 */
public function process(ServerRequestInterface $request, RequestHandlerInterface $handler): ResponseInterface
{
    if (null === $this->permission) {
        return JsonResponseFactory::create('Gate is not set properly.');
    }
}
```

!!! note
    If the permission is `null`, the user will be halted from continuing, and instead will see a message that states, 
    "Gate is not set properly." A user should not see this message, so please make sure that you `set` and `check` 
    your gates when you add them to your routes.

Next, we are going to call the `can()` method from the `UserAuth` class and set that to a variable, followed by an if 
statement checking for if the current user is logged in, and then checking to see if the logged-in user has the specified 
permission:

```php
<?php

///
$permission = $this->user->can(permissionName: $this->permission, request: $request);

if (false === $this->user->current() || false === $permission) {
    //
}
```

In regard to the if statement, we are checking to see if `$this->user->current()` method returns false. If it does, 
that means the user is not authenticated. Otherwise, the `current()` method would return an object. If it turns out that 
the user is authenticated, we also check to see if the user has the proper permission. If both checks are true, then the 
user can proceed forward. If both or one is false, then we need to redirect the user appropriately:

```php
<?php

if (false === $this->user->current() || false === $permission) {
    if (null !== $this->redirect) {
        return RedirectResponseFactory::create(uri: $this->redirect);
    } else {
        return JsonResponseFactory::create(data: 'Access denied.');
    }
}
```

In our second if/else statement, we check to see if the `$redirect` property is null, if it is not null, we will redirect 
the user to the given `uri`. It the `redirect` property is null, then a response will be returned with the given message: 
`Access denied.`

!!! note
    Please note that the `redirect` property should be set to a `uri` and **not** a full `URL`.

## Full Code

Now, when we put it all together, this should be your end result:

```php
<?php

declare(strict_types=1);

namespace App\Infrastructure\Http\Middleware;

use App\Infrastructure\Services\UserAuth;
use Exception;
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;
use Psr\Http\Server\MiddlewareInterface;
use Psr\Http\Server\RequestHandlerInterface;
use Qubus\Exception\Data\TypeException;
use Qubus\Http\Factories\JsonResponseFactory;
use Qubus\Http\Factories\RedirectResponseFactory;

class GateMiddleware implements MiddlewareInterface
{
    protected ?string $permission = null;
    protected ?string $redirect = null;

    public function __construct(protected UserAuth $user)
    {
    }

    public function withArguments(?string $permission = null, ?string $redirect = null): static
    {
        $clone = clone $this;
        $clone->permission = $permission;
        $clone->redirect = $redirect;

        return $clone;
    }

    /**
     * @inheritDoc
     * @throws TypeException
     * @throws Exception
     */
    public function process(ServerRequestInterface $request, RequestHandlerInterface $handler): ResponseInterface
    {
        if (null === $this->permission) {
            return JsonResponseFactory::create('Gate is not set properly.');
        }

        $permission = $this->user->can(permissionName: $this->permission, request: $request);

        if (false === $this->user->current() || false === $permission) {
            if (null !== $this->redirect) {
                return RedirectResponseFactory::create(uri: $this->redirect);
            } else {
                return JsonResponseFactory::create(data: 'Access denied.');
            }
        }

        return $handler->handle($request);
    }
}
```

## Usage

Now that we have our new middleware, how do we use it? Well, first we need to register our new middleware in 
`./config/app.php` under the `middlewares` key:

```php
<?php

    /*
    |--------------------------------------------------------------------------
    | Middleware Aliases
    |--------------------------------------------------------------------------
    | Middleware aliases are registered here, but to use a middleware, you
    | can add them to a route, a group of routes or controllers.
    */
    'middlewares' => [
        //
        'gate' => App\Infrastructure\Http\Middleware\GateMiddleware::class,
    ],
```

As you can see above, we used the alias `gate` for our middleware. This is what's used to register and resolve the 
middleware into or out of our injector/container.

Now, let's add our middleware to a route that we want to protect.

```php title="file: ./routes/web/web.php"
<?php

return function (\Qubus\Routing\Psr7Router $router) {
    $router
        ->get(uri: '/admin/dashboard/', callback: 'AdminController@dashboard')
        ->middleware(['gate:admin:profile, /admin/login/']);
};
```

On our `/admin/dashboard/` route, we use the `middleware()` method with the following parameters: 
`['gate:admin:profile, /admin/login/']`. In the array we have the following string: `gate:admin:profile, /admin/login/`. 

The middleware resolver will [explode](https://www.php.net/manual/en/function.explode.php) the string on the first colon (`:`). 
Then the first part of the string `gate` will be used to resolve `GateMiddleware`, then the rest of the string
(`admin:profile, /admin/login/`) will [explode](https://www.php.net/manual/en/function.explode.php) on the 
comma (`,`). This then creates an array that then gets turned into two positional arguments: `admin:profile` 
resolves to the `$permission` parameter, and `/admin/login/` resolves to the `$redirect` parameter of the 
`withArguments()` method of the `GateMiddleware`. Then the `GateMiddleware` will handle the rest by going through the 
`if` statement.

If you are logged out, and you were to visit the `/admin/dashboard/` route, you should get redirected to `/admin/login/`.

## Final Notes

If you need to create middlewares for your CodefyPHP application(s) in the future, and you need to pass arguments to 
them, here are a few things to keep in mind.

All of these are valid and are automatically supported:

```php
<?php

// Key-value syntax
$router->middleware('permission:permission=manage-users,redirect=/no-access');

// Array style values
$router->middleware(['roles:allowed=[admin,editor],redirect=/403']);
// or Array positional
$router->middleware(['roles:[admin,editor],/403']);

// Positional syntax
$router->middleware('permission:manage-users,/no-access');

// Single argument
$router->middleware('auth:admin');

// Multiple middlewares
$router->middleware(['auth', 'permission:edit-posts,/no-access']);
```

| Example Input                                                           | Behavior                                        |
|-------------------------------------------------------------------------|-------------------------------------------------|
| `'gate'`                                                                | Resolves via container alias                    |
| `'permission:admin:dashboard,/403'`                                     | Resolves alias with positional args             |
| `'permission:[admin:dashboard,admin:profile],/403'`                     | Resolves alias with positional args with arrays |
| `'permission:permission=admin:dashboard,redirect=/403'`                 | Resolves alias with key-value args              |
| `'permission:permission=[admin:dashboard,admin:profile],redirect=/403'` | Resolves alias with key-value args with arrays  |
| `GateMiddleware::class`                                                 | Instantiates directly                           |
| `new GateMiddleware()`                                                  | Uses given instance as-is                       |

## Need Help?

If you need further help, or have questions, you can always post questions or seek help on the 
[forums](https://forum.codefyphp.com/).
