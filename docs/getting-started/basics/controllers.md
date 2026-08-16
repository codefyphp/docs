---
title: Controllers
sidebar_title: Controllers
weight: 9
---

An alternative way of defining request logic in a route is by organizing it by utilizing `Controllers`. In this section 
you will learn about basic controllers, resource controllers and restful controllers.

As a defined default in `Codefy\Framework\Application`, all controllers should fall under the 
`App\Infrastructure\Http\Controllers` namespace.

If you are using the skeleton app (v3.1+), they fall under the 
`Application\Http\Controller` namespace in the `src/Application/Http/Controller` directory. However, you can put your 
controllers where it best fits for your application and update the `controller_namespace` key in `./config/app.php`.

## Basic Controller

Here is a simple example of a basic controller with an index method which responds to an incoming request.

```php title="./src/Application/Http/Controller/HomeController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Http\BaseController;
use Psr\Http\Message\ResponseInterface;

use function Codefy\Framework\Helpers\trans;
use function Codefy\Framework\Helpers\view;

final class HomeController extends BaseController
{
    public function index(): ResponseInterface
    {
        return view(
            template: 'framework::home',
            data: ['title' => trans('CodefyPHP Framework')]
        );
    }
}
```

!!! note "Return Response"
    As much as it is possible, always return a response (**highly recommended**) in your controllers. In the above 
    example, the view is passed into the `create()` method of `HtmlResponseFactory`. For a list of other response 
    factories, check out the [Route Response](routing.md#route-response) section.

Now, we can define a route to the controller's method `index`. This route example can be defined in the 
`routes/web/web.php` file:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return (function(\Qubus\Routing\Psr7Router $router) {
    $router->get('/', 'HomeController@index');
});
```

When an incoming request matches a route's uri, the index method in the `HomeController` will be invoked.

!!! note
    Please note that controllers do not have to extend Codefy's `BaseController`, but doing so gives you access to 
    a Renderer engine, the router, and the `middleware` method.

## Resource Controller

You can create controllers that automatically handle all the route/CRUD requests. When creating a resource 
controller, you can implement the resource controller interface: `Qubus\Routing\Interfaces\ResourceController`, 
but you don't have to. You can extend the interface to override some of the methods and their parameters or 
create your own interface based on the specifications of your project/application.

    <?php

    declare(strict_types=1);

    namespace Qubus\Routing\Interfaces;
    
    use Psr\Http\Message\RequestInterface;
    use Psr\Http\Message\ResponseInterface;
    
    interface ResourceController
    {
        /**
         * Display a listing of the resource.
         */
        public function index();
    
        /**
         * Display the specified resource.
         */
        public function show(int|string $id): ResponseInterface;
    
        /**
         * Store a newly created resource in storage.
         */
        public function store(RequestInterface $request): ResponseInterface;
    
        /**
         * Show the form for creating a new resource.
         */
        public function create(): ResponseInterface;
    
        /**
         * Show the form/view for editing the specified resource.
         */
        public function edit(int|string $id): ResponseInterface;
    
        /**
         * Update the specified resource in storage.
         */
        public function update(RequestInterface $request): ResponseInterface;
    
        /**
         * Remove the specified resource from storage.
         */
        public function destroy(int|string $id): ResponseInterface;
    }

If you want to use middleware in your resource controller, then your controller should extend the base controller 
class: `Codefy\Framework\Http\BaseController`.

```php title="./src/Application/Http/Controller/PostController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Application\Http\Middleware\AddHeaderMiddleware;
use Codefy\Framework\Http\BaseController;
use Psr\Http\Message\ResponseInterface;
use Qubus\Http\Factories\HtmlResponseFactory;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Interfaces\ResourceController;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

class PostController extends BaseController implements ResourceController
{
    protected array $middlewares = [AddHeaderMiddleware::class];

    public function index(): ResponseInterface
    {
        return HtmlResponseFactory::create('Index of post controller.');
    }

    ```
}
```

Register a resourceful route to the controller:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return (function(\Qubus\Routing\Psr7Router $router) {
    $router->resource('posts', 'PostController');
});
```

You can register multiple resource controllers by passing in an array in the `resource` method:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function(\Qubus\Routing\Psr7Router $router) {
    $router->resources([
        'posts' => 'PostController',
        'users' => 'UserController'
    ]);
};
```

**Actions handled by Resource Controller:**

| Verb      | Uri                 | Action  | Route Name    |
|-----------|---------------------|---------|---------------|
| GET       | /posts              | index   | posts.index   |
| GET       | /posts/create       | create  | posts.create  |
| POST      | /posts/store        | store   | posts.store   |
| GET       | /posts/{posts}      | show    | posts.show    |
| GET       | /posts/{posts}/edit | edit    | posts.edit    |
| PUT/PATCH | /posts/{posts}      | update  | posts.update  |
| DELETE    | /posts/{posts}      | destroy | posts.destroy |

## RESTful Controller

You can conveniently create controllers that will be consumed by an api by using the `apiResource` method:

```php title="./routes/api/rest.php"
<?php

declare(strict_types=1);

return function(\Qubus\Routing\Psr7Router $router) {
    $router->apiResource('users', 'UserRestController');
};
```

You can register several api resources by passing in an array to the `apiResources` method:

```php title="./routes/api/rest.php"
<?php

declare(strict_types=1);

return function(\Qubus\Routing\Psr7Router $router) {
    $router->apiResources([
        'posts' => 'PostRestController',
        'users' => 'UserRestController'
    ]);
};
```

## Controller Middleware

A middleware can be defined on your routes or in your controllers:

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

use Application\Http\Middleware\AuthMiddleware;

return function(\Qubus\Routing\Psr7Router $router) {
    $router->resource('posts', 'PostController')->middleware(new AuthMiddleware());
};
```

Alternatively, you can use the `middleware` property in your Controller:

```php title="./src/Application/Http/Controller/PostController.php"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Application\Http\Middleware\AuthMiddleware;
use Codefy\Framework\Http\BaseController;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

class PostController extends BaseController implements ResourceController
{
    protected array $middlewares = [AuthMiddleware::class];
    
    ```
}
```

This is just a brief introduction to using middleware. Check out the 
[Middleware](middleware.md) section for more details.

