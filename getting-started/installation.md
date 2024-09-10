The easiest way to install CodefyPHP is to use composer by creating a new project using the current stable branch of 
the [skeleton app starter](https://github.com/codefyphp/skeleton). Make sure to substitute `project-name` for the name of 
your specific project.

    composer create-project codefyphp/skeleton:2.x project-name

The architecture is pretty simple. The PSR-4 namespace is `App`, and under that namespace you can set the architecture 
as you see fit. Below is a tree of the starter skeleton app:

    ├── App
    │   ├── Application
    │   │   └── Console
    │   │       └── Kernel.php
    │   ├── Domain
    │   │   └── User
    │   │       ├── Command
    │   │       │   ├── CreateUserCommandHandler.php
    │   │       │   ├── CreateUserCommand.php
    │   │       │   ├── UpdateUserCommandHandler.php
    │   │       │   └── UpdateUserCommand.php
    │   │       ├── Error
    │   │       ├── Event
    │   │       │   ├── EmailAddressWasChanged.php
    │   │       │   ├── NameWasChanged.php
    │   │       │   ├── PasswordWasChanged.php
    │   │       │   └── UserWasCreated.php
    │   │       ├── Query
    │   │       │   ├── FindUserByIdQueryHandler.php
    │   │       │   ├── FindUserByIdQuery.php
    │   │       │   ├── FindUserQueryHandler.php
    │   │       │   └── FindUserQuery.php
    │   │       ├── Repository
    │   │       │   └── UserRepository.php
    │   │       ├── Services
    │   │       │   ├── DatabaseUserProjection.php
    │   │       │   ├── UserAuth.php
    │   │       │   └── UserSession.php
    │   │       ├── User.php
    │   │       ├── UserProjection.php
    │   │       └── ValueObject
    │   │           ├── UserId.php
    │   │           └── UserToken.php
    │   ├── Event
    │   ├── Infrastructure
    │   │   ├── Errors
    │   │   ├── Http
    │   │   │   ├── Controllers
    │   │   │   │   ├── AdminController.php
    │   │   │   │   └── HomeController.php
    │   │   │   ├── Middleware
    │   │   │   │   ├── CorsMiddleware.php
    │   │   │   │   ├── Csrf
    │   │   │   │   │   ├── CsrfProtectionMiddleware.php
    │   │   │   │   │   ├── CsrfSession.php
    │   │   │   │   │   ├── CsrfTokenMiddleware.php
    │   │   │   │   │   ├── helpers.php
    │   │   │   │   │   └── Traits
    │   │   │   │   │       └── CsrfTokenAware.php
    │   │   │   │   ├── HoneyPotMiddleware.php
    │   │   │   │   ├── LoggingMiddleware.php
    │   │   │   │   ├── SecureHeaders
    │   │   │   │   │   ├── ContentSecurityPolicyMiddleware.php
    │   │   │   │   │   └── SecureHeaders.php
    │   │   │   │   └── UserSessionMiddleware.php
    │   │   │   └── Routes
    │   │   ├── Persistence
    │   │   │   ├── OrmTransactionalEventStore.php
    │   │   │   └── Repository
    │   │   └── Providers
    │   │       ├── ApiRouteServiceProvider.php
    │   │       ├── AppServiceProvider.php
    │   │       ├── MiddlewareServiceProvider.php
    │   │       ├── Psr16ServiceProvider.php
    │   │       └── WebRouteServiceProvider.php
    │   └── Shared
    │       ├── Http
    │       │   └── RequestMethod.php
    │       └── ValueObject
    │           ├── TransactionUlid.php
    │           ├── UlidIdentity.php
    │           └── UuidIdentity.php
    ├── bootstrap
    │   ├── app.php
    │   └── phpmig.php
    ├── codex
    ├── composer.json
    ├── composer.lock
    ├── config
    │   ├── app.php
    │   ├── auth.php
    │   ├── cache.php
    │   ├── commandbus.php
    │   ├── cookies.php
    │   ├── cors.php
    │   ├── csrf.php
    │   ├── database.php
    │   ├── filesystem.php
    │   ├── headers.php
    │   ├── mailer.php
    │   ├── routes.php
    │   ├── session.php
    │   └── view.php
    ├── database
    │   └── migrations
    │       ├── 20220925064056_CreateUsersTable.php
    │       └── 20230901025725_CreateEventStoreTable.php
    ├── locale
    ├── phpcs.xml
    ├── phpunit.xml
    ├── public
    │   ├── assets
    │   │   ├── css
    │   │   │   ├── admin.css
    │   │   │   ├── authforms.css
    │   │   │   ├── bootstrap.min.css
    │   │   │   ├── bootstrap.min.css.map
    │   │   │   ├── bootstrap.rtl.min.css
    │   │   │   ├── bootstrap.rtl.min.css.map
    │   │   │   └── cover.css
    │   │   ├── images
    │   │   │   └── codefyphp-cover.png
    │   │   └── js
    │   │       ├── admin.js
    │   │       ├── bootstrap.bundle.min.js
    │   │       ├── bootstrap.bundle.min.js.map
    │   │       ├── color-modes.js
    │   │       └── modes.js
    │   ├── favicon.png
    │   ├── frontend
    │   │   └── assets
    │   │       ├── css
    │   │       │   ├── layout.css
    │   │       │   ├── nucleus.css
    │   │       │   ├── pure.min.css
    │   │       │   └── slidebars.min.css
    │   │       ├── images
    │   │       │   └── email_campaign_smtp_issue.png
    │   │       └── js
    │   │           ├── frontpage-nav.min.js
    │   │           ├── scrolling.js
    │   │           └── slidebars.min.js
    │   └── index.php
    ├── README.md
    ├── resources
    │   └── views
    │       ├── backend
    │       │   ├── admin-layout.phtml
    │       │   ├── auth-layout.phtml
    │       │   ├── index.phtml
    │       │   ├── login.phtml
    │       │   ├── profile.phtml
    │       │   └── register.phtml
    │       ├── cache
    │       ├── frontend
    │       ├── home.phtml
    │       └── layout.phtml
    ├── storage
    │   ├── app
    │   │   └── public
    │   ├── email
    │   ├── framework
    │   │   ├── cache
    │   │   ├── cookies
    │   │   ├── media
    │   │   ├── sessions
    │   │   └── views
    │   └── logs
    └── tests
        ├── ExampleTest.php
        └── Pest.php

Apache
------

If you are using an Apache server for development, you need to set up your virtual host. Follow this example:

    <VirtualHost *:80>
        DocumentRoot "/opt/lampp/htdocs/myproject/public"
        ServerName   codefy.local
        ErrorLog     "/opt/lampp/htdocs/myproject/storage/logs/error_log"
        CustomLog    "/opt/lampp/htdocs/myproject/storage/logs/access_log" common
    
        <Directory "/opt/lampp/htdocs/myproject/public">
            AllowOverride All
            Require all granted
        </Directory>
    </VirtualHost>

The `public` folder under `myproject` is the root of you project where the .htaccess file is located.

Nginx
-----

If you are using an Nginx server for development, you need to set you virtualhost config similar to this example:

    server {
        listen 80;
    
        server_name codefy.local;
    
        root  /opt/lampp/htdocs/myproject/public;
        index index.php index.html index.htm;
    
        location / {
            try_files $uri /index.php;
        }
    
        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
    
            # With php-fpm:
            fastcgi_pass unix:/run/php/php8.2-fpm.sock;
            # With php-cgi:
            # fastcgi_pass 127.0.0.1:9000;
        }
    
        error_page 404 /index.php;
    
        # deny access to hidden files such as .htaccess
        location ~ /\. {
            deny all;
        }
    }

Once you make the server configuration changes, restart the server. Then, in a browser, visit the url `http://codefy.local` and 
you should see a successful installation.

Next start your database server, create a database, and then follow these steps:

1. rename `.env.example` to `.env` and change the variables to match your dev environment
2. next, open `config/auth.php` to change the url's to match your install
3. then run the command `php codex migrate` to run the database migrations
4. visit the url http://codefy.local/admin/register/ to register your first account
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPRegisterScreen.png" width="660" alt="Register Screen">
</h3>
5. then visit http://codefy.local/admin/login/ to login with the new credentials, and you will be redirected to the backend's dashboard.
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPLoginScreen.png" width="660" alt="Login Screen">
</h3>
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPDashboard.png" width="660" alt="Dashboard">
</h3>
6. the profile page is where you can update your profile.
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPProfileScreen.png" width="660" alt="Profile Screen">
</h3>

This is a very simple app to get you started. Check out the code in the App directory which makes up the majority of the admin backend, 
event store, and domain functionality.

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.