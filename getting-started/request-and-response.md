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

## Cookies

CodefyPHP Cookies is a fork of FIG Cookies and manages cookies for PSR-7 Requests and Responses.

CodefyPHP Cookies tackles two problems, managing __Cookie__ *Request* headers and managing __Set-Cookie__ *Response* headers. 
It does this by way of introducing a `Cookies` class to manage collections of `Cookie` instances and a `SetCookies` class to 
manage collections of `SetCookie` instances.

    <?php

    // Get a collection representing the cookies in the Cookie headers
    // of a PSR-7 Request.
    $cookies = Qubus\Http\Cookies\Cookies::fromRequest($request);
    
    // Get a collection representing the cookies in the Set-Cookie headers
    // of a PSR-7 Response
    $setCookies = Qubus\Http\Cookies\SetCookies::fromResponse($response);

After modifying these collections in some way, they are rendered into a PSR-7 Request or PSR-7 Response like this:

    <?php
    
    // Render the Cookie headers and add them to the headers of a
    // PSR-7 Request.
    $request = $cookies->renderIntoCookieHeader($request);
    
    // Render the Set-Cookie headers and add them to the headers of a
    // PSR-7 Response.
    $response = $setCookies->renderIntoSetCookieHeader($response);

Like PSR-7 Messages, `CookieCollection`, `Cookies`, `SetCookieCollection`, and `SetCookies` are all represented as 
immutable value objects and all mutators will return new instances of the original with the requested changes.

### Request Cookies

Requests include cookie information in the __Cookie__ request header. The cookies in this header are represented by 
the CookieCollection class.

    <?php
    
    use Qubus\Http\Cookies\CookieCollection;
    
    $cookie = CookieCollection::create('username', 'davidspade');

To easily work with request cookies, use the `CookiesRequest` facade.

#### Retrieve A Request Cookie

The `get` method will return a `CookieCollection` instance. If no cookie by the specified name exists, the 
returned `CookieCollection` instance will have a `null` value.

The optional third parameter to `get` sets a default value that should be used if a cookie does not exist.

    <?php

    use Qubus\Http\Cookies\CookiesRequest;
    
    $cookie = CookiesRequest::get($request, 'userId');
    //or with a default value
    $cookie = CookiesRequest::get($request, 'userId', '01HDYTTNRME1KRZQJCGTRRH2HV');

#### Set A Cookie Request

The `set` method will either add a cookie or replace an existing cookie.

The `CookieCollection` primitive is used as the second argument.

    <?php
    
    use Qubus\Http\Cookies\CookiesRequest;
    
    $request = CookiesRequest::set($request, CookieCollection::create('userId', '01HDYV2CNCE0F8RCSY8HADMS0M'));

#### Modify A Cookie Request

The `modify` method allows for replacing the contents of a cookie based on the current cookie with the specified name. 
The third argument is a `callable` that takes a `CookieCollection` instance as its first argument and is expected to 
return a `CookieCollection` instance.

If no cookie by the specified name exists, a new Cookie instance with a null value will be passed to the callable.

    <?php
    
    use Qubus\Http\Cookies\CookieCollection;
    use Qubus\Http\Cookies\CookiesRequest;
    
    $modify = function (CookieCollection $cookie) {
    $value = $cookie->getValue();
    
        // ... inspect current $value and determine if $value should
        // change or if it can stay the same. In all cases, a cookie
        // should be returned from this callback...
    
        return $cookie->withValue($value);
    }
    
    $request = CookiesRequest::modify($request, 'userId', $modify);

#### Remove A Request Cookie

The `remove` method removes a cookie from the request headers if it exists.

    <?php
    
    use Qubus\Http\Cookies\CookiesRequest;
    
    $request = CookiesRequest::remove($request, 'userId');

> Note that this does not cause the client to remove the cookie. Take a look at the `SetCookie` class' `expire()` 
> method to do that.

### Response Cookies

Responses include cookie information in the `Set-Cookie` response header. The cookies in these headers are represented 
by the `SetCookieCollection` class.

    <?php
    
    use Qubus\Http\Cookies\SameSite;
    use Qubus\Http\Cookies\SetCookieCollection;
    
    $setCookie = SetCookieCollection::create('userId')
        ->withValue('Rg3vHJZnehYLjVg7qi3bZjzg')
        ->withExpires('Mon, 15-Jan-2024 21:47:38 GMT')
        ->withMaxAge(500)
        ->rememberForever()
        ->withPath('/')
        ->withDomain('.example.com')
        ->withSecure(true)
        ->withHttpOnly(true)
        ->withSameSite(SameSite::lax());

> To easily work with response cookies, use the `CookiesResponse` facade.

#### Retrieve A Response Cookie

The `get` method will return a `SetCookieCollection` instance. If no cookie by the specified name exists, the returned 
`SetCookieCollection` instance will have a `null` value.

The optional third parameter to `get` sets a default value that should be used if a cookie does not exist.

    <?php
    
    use Qubus\Http\Cookies\CookiesResponse;
    
    $setCookie = CookiesResponse::get($response, 'userId');
    $setCookie = CookiesResponse::get($response, 'userId', '01HDYTTNRME1KRZQJCGTRRH2HV');

#### Set A Response Cookie

The `set` method will either add a cookie or replace an existing cookie.

The `SetCookieCollection` primitive is used as the second argument.

    <?php
    
    use Qubus\Http\Cookies\CookiesResponse;
    use Qubus\Http\Cookies\SetCookieCollection;
    
    $response = CookiesResponse::set(
        $response,
        SetCookieCollection::create('token')
            ->withValue('a9s87dfz978a9')
            ->withDomain('example.com')
            ->withPath('/')
    );

#### Modify A Response Cookie

The `modify` method allows for replacing the contents of a cookie based on the current cookie with the specified name. 
The third argument is a `callable` that takes a `SetCookieCollection` instance as its first argument and is expected 
to return a `SetCookieCollection` instance.

If no cookie by the specified name exists, a new `SetCookieCollection` instance with a `null` value will be passed to 
the `callable`.

    <?php
    
    use Qubus\Http\Cookies\CookiesResponse;
    use Qubus\Http\Cookies\SetCookieCollection;

    $modify = function (SetCookieCollection $setCookie) {
        $value = $setCookie->getValue();
    
        // ... inspect current $value and determine if $value should
        // change or if it can stay the same. In all cases, a cookie
        // should be returned from this callback...
    
        return $setCookie
            ->withValue($newValue)
            ->withExpires($newExpires);
    }
    
    $response = CookiesResponse::modify($response, 'userId', $modify);

#### Remove A Response Cookie

The `remove` method removes a cookie from the response if it exists.

    <?php
    
    use Qubus\Http\Cookies\CookiesResponse;
    
    $response = CookiesResponse::remove($response, 'userId');

#### Expire A Response Cookie

The `expire` method sets a cookie with an expiry date in the far past. This causes the client to remove the cookie.

Note that in order to expire a cookie, you need to configure its `Set-Cookie` header just like when you initially 
wrote the cookie (i.e. same domain/path). The easiest way to do this is to re-use the same code for configuring the 
header when setting as well as expiring the cookie:

    <?php
    
    use Qubus\Http\Cookies\CookiesResponse;
    use Qubus\Http\Cookies\SetCookieCollection;
    
    $setCookie = SetCookieCollection::create('token')
        ->withValue('UQdfdafpJJ23k111m')
        ->withPath('/')
        ->withDomain('.example.com');
    
    CookiesResponse::set($response, $setCookie->expire());

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.