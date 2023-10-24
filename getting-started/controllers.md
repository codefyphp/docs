An alternative way of defining request logic in a route is by organizing it by utilizing `Controllers`. In this article 
you will learn about basic controllers, resource controllers and restful controllers. As a defined default in 
`Codefy\Framework\Application.php`, all controllers go into `App/Infrastructure/Http/Controllers` directory.

## Basic Controller

You can easily create a new controller by running the `stub:make` command:

    ❯ php codex stub:make Home_controller

Here is a simple example of a basic controller with an index method which responds to an incoming request.

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Http\Controllers;

    use Codefy\Framework\Http\BaseController;
    use Psr\Http\Message\ResponseInterface;
    use Psr\Http\Message\ServerRequestInterface;
    use Qubus\Http\Session\SessionService;
    use Qubus\Routing\Router;
    use Qubus\View\Native\Exception\InvalidTemplateNameException;
    use Qubus\View\Native\Exception\ViewException;
    use Qubus\View\Renderer;
    
    final class HomeController extends BaseController
    {
        public function __construct(
            SessionService $sessionService,
            ServerRequestInterface $request,
            ResponseInterface $response,
            Router $router,
            ?Renderer $view = null
        ) {
            parent::__construct($sessionService, $request, $response, $router, $view);
        }

        /**
         * @throws ViewException
         * @throws InvalidTemplateNameException
         */
        public function index(): ?string
        {
            return $this->view->render('framework::home', ['title' => 'CodefyPHP Framework']);
        }
    }

Now, we can define a route to the controller's method `index`. This route example is defined in our 
`WebRouteServiceProvider` found in `App/Infrastructure/Providers`:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use Codefy\Framework\Support\CodefyServiceProvider;
    use Qubus\Exception\Data\TypeException;
    use Qubus\Routing\Router;
    
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
    
            $router->get('/', 'HomeController@index');
        }
    }

When an incoming request matches a route's uri, the index method in the `HomeController` will be invoked.

> Please note that controllers do not have to extend Codefy's `BaseController`, but doing so gives you access to 
> the native template engine, the router, and the `middleware` method.

## Resource Controller

You can create controllers that automatically handle all the route/CRUD requests. When creating a resource 
controller, you can implement the resource controller interface: `Qubus\Routing\Interfaces\ResourceController`, 
but you don't have to. You can extend the interface to override some of the methods and their parameters or 
create your own interface based on the specifications of your project/application.

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

If you want to use middleware in your resource controller, then your controller should extend the abstract controller 
class: `Codefy\Framework\Http\BaseController`.

    declare(strict_types=1);
    
    namespace App\Infrastructure\Http\Controllers;

    use App\Infrastructure\Http\Middleware\AddHeaderMiddleware;
    use Codefy\Framework\Http\BaseController;
    use Psr\Http\Message\ResponseInterface;
    use Psr\Http\Message\ServerRequestInterface;
    use Qubus\Http\Session\SessionService;
    use Qubus\Routing\Interfaces\ResourceController;
    use Qubus\Routing\Router;
    use Qubus\View\Renderer;
    
    class PostController extends BaseController implements ResourceController
    {
        public function __construct(
            SessionService $sessionService,
            ServerRequestInterface $request,
            ResponseInterface $response,
            Router $router,
            ?Renderer $view = null
        ) {
            $this->middleware(AddHeaderMiddleware::class);

            parent::__construct($sessionService, $request, $response, $router, $view);
        }
    
        public function index(): string
        {
            return 'Index of post controller.';
        }
    
        ```
    }

Register a resourceful route to the controller:

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
    
            $router->resource('posts', 'PostController');
        }
    }

You can register multiple resource controllers by passing in an array in the `resource` method:

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
    
            $router->resources([
                'posts' => 'PostController',
                'users' => 'UserController'
            ]);
        }
    }

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
    
            $router->apiResource('users', 'UserRestController');
        }
    }

You can register several api resources by passing in an array to the `apiResources` method:

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
    
            $router->apiResources([
                'posts' => 'PostRestController',
                'users' => 'UserRestController'
            ]);
        }
    }

## Controller Middleware

A middleware can be defined on your routes or in your controllers:

    use App\Infrastructure\Http\Middleware\AuthMiddleware:

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
    
            $router->resource('posts', 'PostController')->middleware(new AuthMiddleware());
        }
    }

Alternatively, you can use `middleware` method in your Controller's constructor:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Http\Controllers;
    
    use App\Infrastructure\Http\Middleware\AuthMiddleware;
    use Codefy\Framework\Http\BaseController;
    use Psr\Http\Message\ResponseInterface;
    use Psr\Http\Message\ServerRequestInterface;
    use Qubus\Http\Session\SessionService;
    use Qubus\Routing\Router;
    use Qubus\View\Renderer;

    class PostController extends BaseController implements ResourceController
    {
        public function __construct(
            SessionService $sessionService,
            ServerRequestInterface $request,
            ResponseInterface $response,
            Router $router,
            ?Renderer $view = null
        ) {
            $this->middleware(AuthMiddleware::class);

            parent::__construct($sessionService, $request, $response, $router, $view);
        }
    
        ```
    }

This is just a brief introduction to using middleware. Check out the 
[Middleware](https://codefyphp.com/knowledgebase/middleware/) page for more details.