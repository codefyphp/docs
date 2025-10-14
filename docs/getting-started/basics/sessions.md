---
title: Sessions
sidebar_title: Sessions
weight: 12
---

CodefyPHP comes with two ways to work with sessions. You can work with native PHP sessions or a session abstraction 
for PSR-7 with option of using a PSR-15 middleware backed by PSR-16 cache.

## Native PHP Session Configuration

Session configuration is defined in `File: ./config/session.php`. The available options are:

| Option             | Scalar Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|--------------------|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `use_cookies`      | `bool`      | Specifies whether the application will use cookies to store the session id on <br/>the client side.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `cookie_secure`    | `bool`      | Specifies whether cookies should only be sent over secure connections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `cookie_lifetime`  | `int`       | Specifies the lifetime of the cookie in seconds which is sent to the browser. <br/>The value `0` means "until the browser is closed."                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `cookie_path`      | `string`    | Specifies path to set in the session cookie.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `cookie_domain`    | `string`    | Specifies the domain to set in the session cookie.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `use_only_cookies` | `bool`      | Specifies whether the application will only use cookies to store the session <br/>id on the client side.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `cookie_httponly`  | `bool`      | Marks the cookie as accessible only through the HTTP protocol.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `use_strict_mode`  | `bool`      | Specifies whether the module will use strict session id mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `cache_limiter`    | `string`    | Specifies the cache control method used for session pages. It may be one of the <br/>following values: nocache, private, private_no_expire, or public.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `cache_expire`     | `int`       | Specifies time-to-live for cached session pages in minutes; this has no effect <br/>for nocache limiter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `cookie_samesite`  | `string`    | Allows servers to assert that a cookie ought not to be sent along with <br/>cross-site requests. This assertion allows user agents to mitigate the risk of <br/>cross-origin information leakage, and provides some protection against <br/>cross-site request forgery attacks. Note that this is not supported by all browsers. <br/>An empty value means that no SameSite cookie attribute will be set. <br/>`Lax` and `Strict` mean that the cookie will not be sent cross-domain for <br/>`POST` requests; `Lax` will send the cookie for cross-domain `GET` requests, <br/>while `Strict` will not. |

### Usage

    <?php
    
    use Codefy\Framework\Codefy;
    
    $session = Codefy::$PHP->session;
    
    $session->set('userId', '01HDYV2CNCE0F8RCSY8HADMS0M');

### Flash Messages

Store messages in session data until they are retrieved. Bootstrap compatible and sticky messages available.

    <?php 
    
    use Codefy\Framework\Codefy;
    
    $message = Codefy::$PHP->flash;
    
    // Add messages
    $message->info('This is an info message');
    $message->success('This is a success message');
    $message->warning('This is a warning message');
    $message->error('This is an error message');
    
    // If you need to check for errors (eg: when validating a form) you can:
    if ($message->hasErrors()) {
        // There ARE errors
    } else {
      // There are NO errors
    }
        
    // Wherever you want to display the messages simply call:
    $message->display();

#### Redirects

It's possible to redirect to a different URL before displaying a message. For example, redirecting back to a form 
(and displaying an error message) so a user can correct an error.

The preferred method of doing this is passing the URL as the 2nd parameter:

```php title="./app/Infrastructure/Http/Controllers/AdminController.php"
<?php

declare(strict_types=1);

namespace App\Infrastructure\Http\Controllers;

use App\Domain\User\Command\CreateUserCommand;
use App\Domain\User\Command\UpdateUserCommand;
use App\Domain\User\ValueObject\UserId;
use App\Domain\User\ValueObject\Username;
use App\Domain\User\ValueObject\UserToken;
use App\Infrastructure\Services\UserAuth;
use App\Shared\Services\Server;
use Qubus\Http\Factories\HtmlResponseFactory;
//...

use function Codefy\Framework\Helpers\config;

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

    /**
     * @throws RouteParamFailedConstraintException
     * @throws UnresolvableQueryHandlerException
     * @throws NamedRouteNotFoundException
     * @throws CommandPropertyNotFoundException
     * @throws ReflectionException
     * @throws SessionException
     * @throws TypeException
     */
    public function index(ServerRequest $request): ResponseInterface|string
    {
        if (false === $this->user->can(permissionName: 'admin:dashboard', request:  $request)) {
            Codefy::$PHP->flash->error(
                message: 'You must be logged in to access the admin area.'
                redirectUrl: Server::siteUrl($this->router->url(name: 'admin.login'));
            );
        }

        return HtmlResponseFactory::create(
            $this->view->render(template: 'framework::backend/index', data: ['title' => 'Dashboard'])
        );
    }
}
```

!!! note "Redirect Url Parameter"
    `Codefy::$PHP->flash` has the second parameter set for redirection in the `index()` method.

#### Sticky Messages

By default, all messages include a close button. The close button can be removed, thus making the message sticky. 
To make a message sticky pass `true` as the third parameter:

    <?php
    
    $message->error(
        message: "This is a sticky error message (it can't be closed)",
        redirectUrl: null,
        sticky: true
    );

## Session Abstraction

Session abstraction provides a simple interface for storing and receiving session data without the use of PHP's 
native session handling.

### Session Entities

When storing data in a session, you must first define your session entity. A session entity is a container/data 
transfer object (DTO).

Below is an example of a session entity where the user's `token` is stored in a session:

    <?php
    
    declare(strict_types=1);
    
    namespace Codefy\Framework\Auth;
    
    use Qubus\Http\Session\SessionEntity;
    
    class UserSession implements SessionEntity
    {
        public private(set) ?string $token = null;
    
        public function withToken(?string $token = null): self
        {
            $this->token = $token;
            return $this;
        }
    
        public function clear(): void
        {
            if (!empty($this->token)) {
                unset($this->token);
            }
        }
    
        public function isEmpty(): bool
        {
            return empty($this->token);
        }
    }


The entities should not be a huge catch-all. They should only be encapsulated to a certain domain and store only 
what is needed in the session.

The `SessionEntity` interface only requires that you implement the `isEmpty()` method. You must adhere to the following 
for your session entities:

- A `SessionEntity` must be able to be serialized and unserialized by native PHP serialization functions without the loss 
of data.
- A `SessionEntity` must **not** have a constructor with parameters.

The `isEmpty()` method should return true when a session entity's state is the same when it was first constructed. When 
serializing session entities, this is used for garbage collection, removing empty entities from storage. Therefore, 
if a `SessionEntity` is changed, any current session created before the change becomes invalid.

### HttpSession

The interface `HttpSession` defines a locator for your session entities. You retrieve session entities for the current 
session by calling the `get()` method.

The `get()` method returns a reference to the session entity. All changes made to the instance are stored at the end 
of the request.

    <?php 
    
    use Codefy\Framework\Auth\UserSession;
    use Qubus\Http\Session\SessionService;
    
    // makeSession() initializes a session.
    $session = (new SessionService($sessionStorage, $cookieFactory))->makeSession($request);
    
    $body = $request->getParsedBody();
    
    // Retrieve a reference to the UserSession entity.
    // All changes made to the instance are stored at
    // the end of the request.
    $user = $session->get(UserSession::class);
    
    // set the session data
    $user
        ->withToken($body['userToken']);
    
    // commitSession() commits the user data to the session.
    return $session->commitSession($response, $session);

The default cookie name used when sessions are created is `QSESSID`. Below is an updated version of the code above 
with a unique cookie name:

    <?php 
    
    use Codefy\Framework\Auth\UserSession;
    use Qubus\Http\Session\SessionService;

    SessionService::$options = [
        'cookie-name' => 'USERSESSID'
    ];
    
    $session = (new SessionService($sessionStorage, $cookieFactory))->makeSession($request);
    
    $body = $request->getParsedBody();
    
    // Retrieve a reference to the UserSession entity
    // All changes made to the instance are stored at
    // the end of the request.
    $user = $session->get(UserSession::class);
    
    // set the session data
    $user
        ->withToken($body['userToken']);
    
    // Commit the user data to the session.
    return $session->commitSession($response, $session);

!!! note
    Only one instance of a session entity is available per session, and it is always available. If an instance of the 
    session entity was not stored in cache, a new instance will be created and returned by `get()`.

#### Deleting A Session Entity

If your individual session entity can be "cleared", your entity must define what that means. For example, the session 
entity above supports a `clear()` method.

#### Clearing Session State

You can clear an entire session, typically in a log-out controller/action:

    <?php
    
    $session->clear();

Note that clearing the session will orphan any objects previously obtained via `get()`.

Clearing the session also implicitly renews the session, as described below.

#### Renewing Sessions

You can renew an existing session, typically in a log-in controller/action:

    <?php
    
    $session->renew();

Renewing a session will retain the current session state, but changes the Session ID, and destroys the session data 
associated with the old Session ID.

Note that periodic renewal of the Session ID is not recommended. Issuing a new Session ID should be done only after 
authentication (e.g. after successful validation of user-supplied login credentials over a secure connection).

### Middleware

`Codefy\Framework\Http\Middleware\Auth\UserSessionMiddleware` is a PSR-15 compliant middleware for easy integration of the 
`SessionService` class. This middleware is called during login, and `Codefy\Framework\Http\Middleware\Auth\ExpireUserSessionMiddleware` 
is called during logout.

