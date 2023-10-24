A PSR-7/15 Middleware can be added to both routes, groups and controllers.

## Adding Middleware to Route

At it's simplest, adding Middleware to a route can be done by passing an object to the `middleware()` method:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use App\Infrastructure\Http\Middleware\AddHeaderMiddleware;
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

Multiple middleware can be added by passing more parameters to the `middleware()` method:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use App\Infrastructure\Http\Middleware\AddHeaderMiddleware;
    use App\Infrastructure\Http\Middleware\AuthMiddleware;
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
    
            $router->get('/', 'HomeController@index')->middleware(
                AddHeaderMiddleware::class,
                AuthMiddleware::class
            );
        }
    }

Or alternatively, you can also pass an array of middleware:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use App\Infrastructure\Http\Middleware\AddHeaderMiddleware;
    use App\Infrastructure\Http\Middleware\AuthMiddleware;
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
    
            $router->get('/', 'HomeController@index')->middleware([
                AddHeaderMiddleware::class,
                AuthMiddleware::class
            ]);
        }
    }

## Base Middleware

If you would like to add a middleware that is going to affect all routes, then use the `setBaseMiddleware` method.

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use App\Infrastructure\Http\Middleware\AddHeaderMiddleware;
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
    
            $router->setBaseMiddleware([AddHeaderMiddleware::class]);
        }
    }

## Route Group

Middleware can also be added to a group. To do so you need to pass an array as the first parameter of the `group()` 
function instead of a string. You can add one middleware or an array of middleware.

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use App\Infrastructure\Http\Middleware\AddHeaderMiddleware;
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
    
            $router->group(['prefix' => 'my-prefix', 'middleware' => [AddHeaderMiddleware::class]], function ($group) {
                $group->map(['GET'], 'route1', function () {}); // `/my-prefix/route1`
                $group->map(['GET'], 'route2', function () {}); // `/my-prefix/route2`
            });
        }
    }

## Middleware on Controllers

You can also apply Middleware on a Controller class too. In order to do this your Controller must extend the 
`Codefy\Framework\Http\BaseController` abstract class.

Middleware is added by calling the `middleware()` method in your Controller's `__construct()` method.

    <?php

    declare(strict_types=1);

    namespace App\Infrastructure\Http\Controllers;
    
    use Codefy\Framework\Http\BaseController;
    use Psr\Http\Message\ResponseInterface;
    use Psr\Http\Message\ServerRequestInterface;
    use Qubus\Http\Session\SessionService;
    use Qubus\Routing\Router;
    use Qubus\View\Renderer;
    
    class PostController extends BaseController
    {
        public function __construct(
            SessionService $sessionService,
            ServerRequestInterface $request,
            ResponseInterface $response,
            Router $router,
            ?Renderer $view = null
        ) {
            // Add one at a time
            $this->middleware(AddHeaderMiddleware::class);
            $this->middleware(AuthMiddleware::class);
    
            // Add multiple with one method call
            $this->middleware([
                AddHeaderMiddleware::class,
                AuthMiddleware::class,
            ]);

            parent::__construct($sessionService, $request, $response, $router, $view);
        }
    }

By default, all Middlewares added via a Controller will affect all methods on that class. To limit what methods a 
Middleware should be applied to, you can use `only()` and `except()`:

    <?php

    declare(strict_types=1);

    namespace App\Infrastructure\Http\Controllers;
    
    use Codefy\Framework\Http\BaseController;
    use Psr\Http\Message\ResponseInterface;
    use Psr\Http\Message\ServerRequestInterface;
    use Qubus\Http\Session\SessionService;
    use Qubus\Routing\Router;
    use Qubus\View\Renderer;

    class PostController extends BaseController
    {
        public function __construct(
            SessionService $sessionService,
            ServerRequestInterface $request,
            ResponseInterface $response,
            Router $router,
            ?Renderer $view = null
        ) {
            // Only apply to `send()` method
            $this->middleware(AddHeaderMiddleware::class)->only('send');
    
            // Apply to all methods except `show()` method
            $this->middleware(AuthMiddleware::class)->except('show');
    
            // Multiple methods can be provided in an array to both methods
            $this->middleware(AuthMiddleware::class)->except(['send', 'show']);

            parent::__construct($sessionService, $request, $response, $router, $view);
        }
    }