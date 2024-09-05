Codefy provides built in support for CSRF (Cross-Site Request Forgery). Since version 1.0.6, when you use the starter 
app, CSRF protection is enabled by default.

Codefy uses two middlewares working in tandem to provide CSRF protection. The `CsrfTokenMiddleware` (alias: `csrf.token`) 
stores CSRF tokens in a session and is validated via a cookie. `CsrfProtectionMiddleware` (alias: `csrf.protection`) 
verifies the authenticity of a CSRF token by a request header (default) or when a form is submitted by the user.

The application opens the session on every request. Each session based token is scoped to a specific user, and is only 
valid for as long as the session is valid.

Currently, CSRF protection is applied to the entire application. However, this can be disabled by removing the middleware 
aliases from the `base_middleware` array in `config/app.php` and instead apply both middleware to specific routes or 
controllers.

For optimum security, the CSRF token is supplied by a custom request header instead of a hidden form tag. 
Nevertheless, if you set `request_header` to `false`, `CsrfProtectionMiddleware` will validate against a hidden html 
form tag instead. You will need to add the `csrf_field()` function to your form:

    <form action="https://app.com/user/reset-password" method="POST">
        <?=csrf_field();?>
        <input name="password" type="password">
        // ...
        <button type="submit">Change password</button>
    </form>

## CSRF Middleware Options

You can set several options in the CsrfTokenMiddleware or in the middleware config found at `config/csrf.php`:

CsrfTokenMiddleware:

    <?php

    SessionService::$options = [
        'cookie-name' => 'CSRFSESSID',
        'cookie-lifetime' => (int) 3600,
    ];

config/csrf.php:

    <?php

    return [
        /*
        |--------------------------------------------------------------------------
        | Request header.
        |--------------------------------------------------------------------------
        */
        'header' => 'X-CSRF-Token',
    
        /*
        |--------------------------------------------------------------------------
        | Set to false, if you rather use an html form tag.
        |--------------------------------------------------------------------------
        */
        'request_header' => true,
    
        /*
        |--------------------------------------------------------------------------
        | HTML form attribute to check for.
        |--------------------------------------------------------------------------
        */
        'csrf_token' => '_token',
    
        /*
        |--------------------------------------------------------------------------
        | Default length of the CSRF token.
        |--------------------------------------------------------------------------
        */
        'csrf_token_length' => (int) 64,
    
        /*
        |--------------------------------------------------------------------------
        | Set a long unique string in .env.
        |--------------------------------------------------------------------------
        */
        'salt' => env(key: 'APP_SALT'),
    
        /*
        |--------------------------------------------------------------------------
        | Status code returned when token is missing or invalid.
        |--------------------------------------------------------------------------
        */
        'error_status_code' => 412,
    
        /*
        |--------------------------------------------------------------------------
        | Set the number of seconds. If null, it will be set for a day,
        | else it will be set to the default cookies setting.
        |--------------------------------------------------------------------------
        */
        'lifetime' => null,
    ];

## CSRF and Session Timeouts

The CSRF token is stored in a session. As soon as the session expires, the application will automatically generate a new 
session with a new token.

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.