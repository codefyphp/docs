---
title: Installation
sidebar_title: Installation
weight: 2
---

The easiest way to install CodefyPHP is to use composer by creating a new project using the current stable branch of 
the [skeleton app starter](https://github.com/codefyphp/skeleton). Make sure to substitute `project-name` for the name of 
your specific project.

    composer create-project codefyphp/skeleton:3.x project-name

By using the command above, you will receive a kind of "rolling release" as new BC changes are pushed out. If you want 
to be on the safe side, use the following command instead:

    composer create-project codefyphp/skeleton project-name

The architecture is pretty simple. The PSR-4 namespace is `app`, and under that namespace you can set the architecture 
as you see fit. Below is a tree of the starter skeleton app:

    ├── app
    │   ├── Application
    │   │   └── Console
    │   │       ├── Commands
    │   │       │   └── GenerateEncryptionKeyCommand.php
    │   │       └── Kernel.php
    │   ├── Domain
    │   │   └── User
    │   │       ├── Command
    │   │       │   ├── CreateUserCommandHandler.php
    │   │       │   ├── CreateUserCommand.php
    │   │       │   ├── UpdateUserCommandHandler.php
    │   │       │   └── UpdateUserCommand.php
    │   │       ├── Error
    │   │       ├── Event
    │   │       │   ├── EmailAddressWasChanged.php
    │   │       │   ├── NameWasChanged.php
    │   │       │   ├── PasswordWasChanged.php
    │   │       │   ├── RoleWasChanged.php
    │   │       │   └── UserWasCreated.php
    │   │       ├── Query
    │   │       │   ├── FindUserByIdQueryHandler.php
    │   │       │   ├── FindUserByIdQuery.php
    │   │       │   ├── FindUserByTokenQueryHandler.php
    │   │       │   ├── FindUserByTokenQuery.php
    │   │       │   ├── FindUserQueryHandler.php
    │   │       │   └── FindUserQuery.php
    │   │       ├── Repository
    │   │       ├── Services
    │   │       │   └── UserProjection.php
    │   │       ├── User.php
    │   │       └── ValueObject
    │   │           ├── UserId.php
    │   │           ├── Username.php
    │   │           └── UserToken.php
    │   ├── Event
    │   ├── Infrastructure
    │   │   ├── Errors
    │   │   ├── Http
    │   │   │   ├── Controllers
    │   │   │   │   ├── AdminController.php
    │   │   │   │   └── HomeController.php
    │   │   │   ├── Middleware
    │   │   │   │   └── ApiMiddleware.php
    │   │   │   └── Routes
    │   │   ├── Persistence
    │   │   │   ├── OrmTransactionalEventStore.php
    │   │   │   └── Repository
    │   │   │       └── UserRepository.php
    │   │   ├── Providers
    │   │   │   ├── ApiRouteServiceProvider.php
    │   │   │   ├── AppServiceProvider.php
    │   │   │   ├── DatabaseServiceProvider.php
    │   │   │   ├── MiddlewareServiceProvider.php
    │   │   │   ├── Psr16ServiceProvider.php
    │   │   │   ├── RbacServiceProvider.php
    │   │   │   ├── ViewServiceProvider.php
    │   │   │   └── WebRouteServiceProvider.php
    │   │   └── Services
    │   │       ├── DatabaseService.php
    │   │       ├── DatabaseUserProjection.php
    │   │       ├── Paginator.php
    │   │       └── UserAuth.php
    │   └── Shared
    │       ├── Http
    │       ├── Services
    │       │   └── Server.php
    │       └── ValueObject
    │           ├── TransactionUlid.php
    │           ├── UlidIdentity.php
    │           └── UuidIdentity.php
    ├── bootstrap
    │   ├── app.php
    │   └── phpmig.php
    ├── codex
    ├── composer.json
    ├── config
    │   ├── app.php
    │   ├── auth.php
    │   ├── cache.php
    │   ├── commandbus.php
    │   ├── cookies.php
    │   ├── cors.php
    │   ├── csrf.php
    │   ├── database.php
    │   ├── filesystem.php
    │   ├── headers.php
    │   ├── http-cache.php
    │   ├── mailer.php
    │   ├── querybus.php
    │   ├── rbac.php
    │   ├── routes.php
    │   ├── session.php
    │   ├── throttle.php
    │   └── view.php
    ├── database
    │   └── migrations
    │       ├── 20220925064056_CreateUsersTable.php
    │       ├── 20230901025725_CreateEventStoreTable.php
    │       ├── 20240918213932_AddTokenField.php
    │       └── 20240919094937_AddRoleField.php
    ├── locale
    ├── phpcs.xml
    ├── phpunit.xml
    ├── public
    │   ├── assets
    │   │   ├── css
    │   │   │   ├── admin.css
    │   │   │   ├── authforms.css
    │   │   │   ├── bootstrap.min.css
    │   │   │   ├── bootstrap.min.css.map
    │   │   │   ├── bootstrap.rtl.min.css
    │   │   │   ├── bootstrap.rtl.min.css.map
    │   │   │   └── cover.css
    │   │   ├── images
    │   │   │   └── codefyphp-cover.png
    │   │   └── js
    │   │       ├── admin.js
    │   │       ├── bootstrap.bundle.min.js
    │   │       ├── bootstrap.bundle.min.js.map
    │   │       ├── color-modes.js
    │   │       └── modes.js
    │   ├── favicon.png
    │   ├── frontend
    │   │   └── assets
    │   │       ├── css
    │   │       │   ├── layout.css
    │   │       │   ├── nucleus.css
    │   │       │   ├── pure.min.css
    │   │       │   └── slidebars.min.css
    │   │       ├── images
    │   │       │   └── email_campaign_smtp_issue.png
    │   │       └── js
    │   │           ├── frontpage-nav.min.js
    │   │           ├── scrolling.js
    │   │           └── slidebars.min.js
    │   ├── index.php
    ├── resources
    │   └── views
    │       ├── backend
    │       │   ├── admin-layout.phtml
    │       │   ├── auth-layout.phtml
    │       │   ├── index.phtml
    │       │   ├── login.phtml
    │       │   ├── profile.phtml
    │       │   └── register.phtml
    │       ├── cache
    │       ├── frontend
    │       ├── home.phtml
    │       └── layout.phtml
    ├── routes
    │   ├── api
    │   │   └── rest.php
    │   └── web
    │       └── web.php
    ├── storage
    │   ├── app
    │   │   └── public
    │   ├── email
    │   ├── framework
    │   │   ├── cache
    │   │   ├── cookies
    │   │   ├── media
    │   │   ├── sessions
    │   │   └── views
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
            fastcgi_pass unix:/run/php/php8.4-fpm.sock;
            # With php-cgi:
            # fastcgi_pass 127.0.0.1:9000;
        }
    
        error_page 404 /index.php;
    
        # deny access to hidden files such as .htaccess
        location ~ /\. {
            deny all;
        }
    }

## Encryption Key

Before proceeding, you need to generate the encryption key file by running the following command on the terminal:

`php codex generate:key:file`

**Result:**

```text
Generating encryption key . . .
Generating encryption key file . . .
.enc.key created.
```

Next start your database server, create a database, and then follow these steps:

Once you make the server configuration changes, restart the server. Then, in a browser, visit the url `http://codefy.local` and
you should see a successful installation.

1. rename `.env.example` to `.env` and change the variables to match your dev environment

2. next, open `config/auth.php` to change the url's to match your install

3. then run the command `php codex migrate` to run the database migrations

4. visit the url http://codefy.local/admin/register/ to register your first account
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPRegisterScreen.png" width="660" alt="Register Screen">
</h3>

then visit http://codefy.local/admin/login/ to log in with the new credentials, and you will be redirected to the backend's dashboard.
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPLoginScreen.png" width="660" alt="Login Screen">
</h3>
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPDashboard.png" width="660" alt="Dashboard">
</h3>

the profile page is where you can update your profile.
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/CodefyPHPProfileScreen.png" width="660" alt="Profile Screen">
</h3>

This is a very simple app to get you started. Check out the code in the App directory which makes up the majority of the admin backend, 
event store, and domain functionality.

## DDEV

As an alternative to above, DDEV is an easy to use and manage tool for local web development. Check out the 
[Get Started with DDEV](https://docs.ddev.com/en/stable/) section on their website for a setup based on your operating 
system or setup. You will need to adapt the above settings to fit your DDEV setup.

Once you have DDEV installed and working, below are a few additions and/or changes you need to make if you are using 
an Apache setup.

### .ddev/config.yaml

    name: Codefy
    type: php
    docroot: public
    php_version: "8.4"
    webserver_type: apache-fpm
    xdebug_enabled: false
    additional_hostnames: []
    additional_fqdns: []
    database:
    type: mariadb
    version: "10.11"
    use_dns_when_possible: true
    composer_version: "2"
    web_environment: []
    corepack_enable: false

### .ddev/php/php.ini

    [PHP]
    max_execution_time = 240;
    
    apc.enabled=Off
    opcache.enable=0
    opcache.enable_cli=0
    opcache.validate_timestamps=1
    opcache.revalidate_freq=0

I have apc and opcache disabled, but you may enable it if it makes sense for your setup.

### .ddev/commands/web/codex

To use the `codex` command line, you will need to create a file in `.ddev/commands/web` and name it `codex`

    cd .ddev/commands/web && touch codex

Open the newly created `codex` and add the following to the file and save:

```shell
#!/bin/bash

php codex $@
```

Restart DDEV to apply changes:

    ddev restart

Now you should be able to run terminal commands like so:

    ddev codex migrate:status

### .ddev/php/php-cli.ini

If you run into deprecated messages appearing in the terminal when running `codex` commands, create a new `.ddev/php/php-cli.ini` 
file and add the following contents and then save.

```shell
; Only suppress deprecations for CLI
error_reporting = E_ALL & ~E_DEPRECATED & ~E_USER_DEPRECATED
```

### .ddev/web-build/codefy.cron

To run the scheduler, do the following:

```shell
touch .ddev/web-build/codefy.cron
```

Open `codefy.cron` and add the following:

```shell
* * * * * cd /var/www/html && php codex schedule:run >> /dev/null 2>&1
```

Restart DDEV to apply changes:

    ddev restart

