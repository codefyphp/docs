---
title: Authentication
sidebar_title: Authentication
weight: 200
---

CodefyPHP helps take away the complexity of authentication by providing a way for your users to authenticate with your 
application. An authentication configuration file is located at `./config/auth.php`. There are several options you can 
tweak according to your application's setup.

## Protecting Routes

CodefyPHP ships with a `user.authorization` middleware, which is a middleware alias for
`Codefy\Framework\Http\Middleware\Auth\UserAuthorizationMiddleware`. All you need to do is use the alias to attach 
the middleware to your route:

    <?php
    
    declare(strict_types=1);
    
    return function (\Qubus\Routing\Psr7Router $router) {
        $router->get('/admin/dashboard', 'AdminController@dashboard')->middleware('user.authorization');
    };

## Is Authenticated

To determine if the user making the incoming HTTP request is authenticated, you may use the `user.authorization` 
middleware on your routes and/or controllers.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->get('/admin/dashboard', 'AdminController@dashboard')->middleware('user.authorization');
};
```

```php title="./App/Infrastructure/Http/Controllers/AdminController.php"
<?php

declare(strict_types=1);

namespace App\Infrastructure\Http\Controllers;

use App\Infrastructure\Services\UserAuth;
use Codefy\Framework\Http\BaseController;
use Qubus\Http\Factories\HtmlResponseFactory;
use Qubus\Http\ServerRequest;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

use function Codefy\Framework\Helpers\site_url;

final class AdminController extends BaseController
{
    public function __construct(
        protected SessionService $sessionService,
        protected Router $router,
        protected UserAuth $user,
        protected Renderer $view
    ) {
        parent::__construct($sessionService, $router, $view);
    }

    public function dashboard(ServerRequest $request): ResponseInterface
    {
        return HtmlResponseFactory::create(
            $this->view->render(template: 'framework::backend/index', data: ['title' => 'Dashboard'])
        );
    }
}
```

### Retrieve Authenticated User

While handling an incoming request, you may access the authenticated user via the `UserAuth` class's `current()` method:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Http\Controllers;
    
    use App\Infrastructure\Services\UserAuth;
    use Codefy\Framework\Http\BaseController;
    use Qubus\Http\Factories\HtmlResponseFactory;
    use Qubus\Http\ServerRequest;
    use Qubus\Http\Session\SessionService;
    use Qubus\Routing\Router;
    use Qubus\View\Renderer;
    
    final class AdminController extends BaseController
    {
        public function __construct(
            protected SessionService $sessionService,
            protected Router $router,
            protected UserAuth $user,
            protected Renderer $view
        ) {
            parent::__construct($sessionService, $router, $view);
        }
    
        public function dashboard(ServerRequest $request): ResponseInterface
        {
            return HtmlResponseFactory::create(
                $this->view->render(
                    template: 'framework::backend/index',
                    data: [
                        'title' => 'Dashboard',
                        'user'  => $this->user->current(),
                    ]
                )
            );
        }
    }

### Redirecting Unauthenticated Users

When the `user.authorization` middleware detects an unauthenticated user, it will redirect a user to the 
`redirect_guests_to` uri set in your `./config/auth.php` file.

## Login Throttling

To use the throttling middleware for rate limiting, check out the [Rate Limiting](../../digging-deeper/throttle.md) section.

## Remembering Users

The `user.session` middleware automatically looks for a `rememberme` request. If you would like to provider 
`remember me` functionality to your application, you need to add an html field to your login form similar to below:

```html
<input type="checkbox" name="rememberme" value="yes" id="remember" class="custom-control-input">
```

!!! note "Input Value"
    Make sure the input value for your `rememberme` checkbox element is `yes`.

## Logging Out

To log users out of your application, you can use the `user.session.expire` middleware on your logout route. The 
middleware will invalidate and remove the authentication information from the user's session so that subsequent 
requests are not authenticated.

```php title="./routes/web/web.php"
<?php

declare(strict_types=1);

return function (\Qubus\Routing\Psr7Router $router) {
    $router->get('/admin/logout', 'AdminController@logout')->middleware('user.session.expire');
};
```

```php title="./App/Infrastructure/Http/Controllers/AdminController.php"
<?php

declare(strict_types=1);

namespace App\Infrastructure\Http\Controllers;

use App\Infrastructure\Services\UserAuth;
use Codefy\Framework\Http\BaseController;
use Qubus\Http\Factories\HtmlResponseFactory;
use Qubus\Http\ServerRequest;
use Qubus\Http\Session\SessionService;
use Qubus\Routing\Router;
use Qubus\View\Renderer;

use function Codefy\Framework\Helpers\site_url;

final class AdminController extends BaseController
{
    public function __construct(
        protected SessionService $sessionService,
        protected Router $router,
        protected UserAuth $user,
        protected Renderer $view
    ) {
        parent::__construct($sessionService, $router, $view);
    }

    public function logout(): ResponseInterface
    {
        // Redirect users to the login screen on logout.
        return $this->redirect(url: site_url(path: $this->router->url(name: 'admin.login')));
    }
}
```

## Defining Permissions

Codefy comes with a `./config/rbac.php` configuration file for defining roles and permissions. Check out the 
[RBAC Config](../basics/rbac.md#rbac-config) section under [Role Based Access Control](../basics/rbac.md) for more 
details.

## Password Rehashing

When your hashing algorithm has been updated, passwords will need to be rehashed using the new algorithm. This function 
should be performed during login:

Check out the 
[Password Rehashing](../security/passwords.md#password-rehashing) section under [Passwords](../security/passwords.md) 
for more details.



