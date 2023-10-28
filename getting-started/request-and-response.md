`Qubus\Http\Request`, `Qubus\Http\Response`, and `Qubus\Http\ServerRequest` are all wrappers for [laminas-diactoros](https://docs.laminas.dev/laminas-diactoros/v3/api/). 
Check out diactoros's documentation on its api and usage. Those classes provide an object-oriented way to interact with 
HTTP requests and responses.

## Request Scope

To get access to the user request, you can type-hint the `Qubus\Http\ServerRequest` on a controller's method or a route's 
closure. The incoming request will be automatically injected by the Injector/Service Container.

Controller:

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

Route:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use Codefy\Framework\Support\CodefyServiceProvider;
    use Qubus\Http\ServerRequest;
    use Qubus\Routing\Exceptions\TooLateToAddNewRouteException;
    use Qubus\Routing\Router;
    
    final class WebRouteServiceProvider extends CodefyServiceProvider
    {
        /**
         * @throws TooLateToAddNewRouteException
         */
        public function boot(): void
        {
            if ($this->codefy->isRunningInConsole()) {
                return;
            }
    
            /** @var $router Router */
            $router = $this->codefy->make(name: 'router');
    
            $router->get('/', function(ServerRequest $request) {
                dd($request->getHeaders());
            });
        }
    }