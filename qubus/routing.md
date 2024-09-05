Basic Routing
-------------

Below is a basic example of setting up a route. The route’s first parameter is the uri, and the second parameter is a 
closure or callback.

    <?php

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

Closure Routing
---------------

In passing a closure as a route handler, you need to pass in two arguments: `Psr\Http\Message\ServerRequestInterface` 
and `Psr\Http\Message\ResponseInterface`. Qubus Router requires [Laminas/Diactoros](https://github.com/laminas/laminas-diactoros). 
This library includes two classes that implement the two needed interfaces.

    <?php

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

Route Request
-------------

The example below shows you how you can catch the request object.

    <?php

    use Qubus\Http\ServerRequest;
    use Qubus\Http\Factories\JsonResponseFactory;
    
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

Route Response
--------------

The Router supports the following responses.

    <?php

    use Qubus\Http\Factories\EmptyResponseFactory;
    use Qubus\Http\Factories\HtmlResponseFactory;
    use Qubus\Http\Factories\JsonResponseFactory;
    use Qubus\Http\Factories\TextResponseFactory;
    use Qubus\Http\Factories\XmlResponseFactory;
    
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

HTTP Methods
------------

Sometimes you might need to create a route that accepts multiple HTTP verbs. For this you can use the `map` method. 
However, If you need to match all HTTP verbs, you can use the `any` method.

    <?php

    $router->map(['GET', 'POST'], '/', function() {
      // ...
    });
    
    $router->any('test', function() {
      // ...
    });

### HTTP Verb Shortcuts

In most typical cases, you will only need to use one HTTP verb. The following can be used in those cases:

    <?php

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

Skeleton
------------

If you are using the skeleton app, then you can conveniently add your routes to `App/Infrastructure/Providers/WebRouteServiceProvider.php`:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Providers;
    
    use Codefy\Framework\Support\CodefyServiceProvider;
    
    final class WebRouteServiceProvider extends CodefyServiceProvider
    {
        public function boot(): void
        {
            if ($this->codefy->isRunningInConsole()) {
                return;
            }
    
            $router = $this->codefy->make(name: 'router');
    
            $router->get('/', 'HomeController@index');
        }
    }

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.