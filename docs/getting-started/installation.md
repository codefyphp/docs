---
title: Installation
sidebar_title: Installation
weight: 2
---

## Composer Install

The easiest way to install CodefyPHP is to use the [application template](https://github.com/codefyphp/skeleton) 
via composer:

    composer create-project codefyphp/skeleton project-name

This will install the latest stable version of the CodefyPHP application template in a directory named `project-name`. 
You can choose a different directory name if you want.

## App Architecture

The architecture is pretty simple:


    ├── bootstrap
    │   ├── app.php
    │   ├── phpmig.php
    │   └── providers.php
    ├── codex
    ├── composer.json
    ├── config
    │   ├── app.php
    │   ├── assets.php
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
    │   ├── stubs.php
    │   ├── throttle.php
    │   └── view.php
    ├── database
    │   ├── codefy.sqlite
    │   ├── migrations
    │   │   ├── 20220925064056_CreateUsersTable.php
    │   │   ├── 20230901025725_CreateEventStoreTable.php
    │   │   ├── 20240918213932_AddTokenField.php
    │   │   └── 20240919094937_AddRoleField.php
    │   └── seeders
    │       ├── DatabaseSeeder.php
    │       └── UserSeeder.php
    ├── locale
    │   ├── codefy.pot
    │   ├── en
    │   │   ├── codefy-en.mo
    │   │   └── codefy-en.po
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
    │   │   │   ├── cover.css
    │   │   │   └── main.css
    │   │   ├── images
    │   │   │   ├── CodefyPHP-Banner.png
    │   │   │   ├── CodefyPHP-Banner-Small.png
    │   │   │   └── mark.png
    │   │   └── js
    │   │       ├── admin.js
    │   │       ├── app.js
    │   │       ├── bootstrap.bundle.min.js
    │   │       ├── bootstrap.bundle.min.js.map
    │   │       ├── color-modes.js
    │   │       └── modes.js
    │   ├── favicon.png
    │   ├── index.php
    ├── README.md
    ├── resources
    │   └── views
    │       ├── app-layout.phtml
    │       ├── backend
    │       │   ├── admin-layout.phtml
    │       │   ├── auth-layout.phtml
    │       │   ├── index.phtml
    │       │   ├── login.phtml
    │       │   ├── partials
    │       │   │   ├── x-create-user-modal.phtml
    │       │   │   └── x-edit-user-modal.phtml
    │       │   ├── profile.phtml
    │       │   ├── register.phtml
    │       │   └── users.phtml
    │       ├── cache
    │       ├── frontend
    │       ├── home.phtml
    │       └── partials
    │           └── desktop-nav.phtml
    ├── routes
    │   ├── api
    │   │   └── rest.php
    │   └── web
    │       ├── admin.php
    │       ├── auth.php
    │       ├── register.php
    │       └── web.php
    ├── src
    │   ├── Application
    │   │   ├── Console
    │   │   │   ├── Commands
    │   │   │   └── Kernel.php
    │   │   ├── Http
    │   │   │   ├── Controller
    │   │   │   │   ├── AdminController.php
    │   │   │   │   ├── AuthController.php
    │   │   │   │   ├── HomeController.php
    │   │   │   │   ├── ProfileController.php
    │   │   │   │   └── RegisterController.php
    │   │   │   ├── Middleware
    │   │   │   └── Route
    │   │   │       └── TestRoute.php
    │   │   ├── Provider
    │   │   │   ├── ApiRouteServiceProvider.php
    │   │   │   ├── AppServiceProvider.php
    │   │   │   ├── DatabaseServiceProvider.php
    │   │   │   ├── MiddlewareServiceProvider.php
    │   │   │   ├── Psr16ServiceProvider.php
    │   │   │   ├── RbacServiceProvider.php
    │   │   │   ├── ViewServiceProvider.php
    │   │   │   └── WebRouteServiceProvider.php
    │   │   ├── Service
    │   │   │   ├── DatabaseService.php
    │   │   │   └── Paginator.php
    │   │   └── Shared
    │   │       └── ValueObject
    │   │           ├── TransactionUlid.php
    │   │           ├── UlidIdentity.php
    │   │           └── UuidIdentity.php
    │   ├── Domain
    │   │   └── User
    │   │       ├── Command
    │   │       │   ├── CreateUserCommandHandler.php
    │   │       │   ├── CreateUserCommand.php
    │   │       │   ├── DeleteUserCommandHandler.php
    │   │       │   ├── DeleteUserCommand.php
    │   │       │   ├── UpdateUserCommandHandler.php
    │   │       │   ├── UpdateUserCommand.php
    │   │       │   ├── UpdateUserPasswordCommandHandler.php
    │   │       │   └── UpdateUserPasswordCommand.php
    │   │       ├── Dto
    │   │       │   ├── DestroyUserData.php
    │   │       │   ├── StoreUserData.php
    │   │       │   ├── UpdateUserData.php
    │   │       │   └── UpdateUserPassword.php
    │   │       ├── Enum
    │   │       │   └── UserRole.php
    │   │       ├── Event
    │   │       │   ├── EmailAddressWasChanged.php
    │   │       │   ├── NameWasChanged.php
    │   │       │   ├── PasswordWasChanged.php
    │   │       │   ├── RoleWasChanged.php
    │   │       │   ├── UserWasCreated.php
    │   │       │   └── UserWasDeleted.php
    │   │       ├── Query
    │   │       │   ├── FindUserByEmailQueryHandler.php
    │   │       │   ├── FindUserByEmailQuery.php
    │   │       │   ├── FindUserByIdQueryHandler.php
    │   │       │   ├── FindUserByIdQuery.php
    │   │       │   ├── FindUserByTokenQueryHandler.php
    │   │       │   ├── FindUserByTokenQuery.php
    │   │       │   ├── FindUsersQueryHandler.php
    │   │       │   └── FindUsersQuery.php
    │   │       ├── Repository
    │   │       │   └── UserAggregateRepository.php
    │   │       ├── Service
    │   │       │   ├── UserProjection.php
    │   │       │   └── UserService.php
    │   │       ├── User.php
    │   │       ├── Validator
    │   │       │   ├── DestroyUserValidator.php
    │   │       │   ├── StoreUserValidator.php
    │   │       │   ├── UpdateUserPasswordValidator.php
    │   │       │   └── UpdateUserValidator.php
    │   │       └── ValueObject
    │   │           ├── UserId.php
    │   │           ├── Username.php
    │   │           └── UserToken.php
    │   └── Infrastructure
    │       ├── Persistence
    │       │   ├── PdoTransactionalEventStore.php
    │       │   └── Repository
    │       │       ├── EventSourcedUserRepository.php
    │       │       └── PdoAuthUserRespository.php
    │       └── Projection
    │           └── ExpressiveDbalUserProjection.php
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
    │   └── logs
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

## Configuration

Once you have a server setup, you will need to perform some initial [configuration](configuration.md) before continuing 
below.

## Encryption Key

Before proceeding, you need to generate the encryption key file by running the following command on the terminal:

`php codex generate:key:file`

**Result:**

```text
Generating encryption key file . . .
.enc.key created.
```

Next you can create your database, run migrations, and seed your SQLite database by running the following commands:

`php codex migrate && php codex db:seed`

Once you make the server configuration changes, restart the server. Then, in a browser, visit the url `http://codefy.local` and
you should see a successful installation:
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/codefy-home.png" width="660" alt="Homepage">
</h3>

1. Rename `.env.example` to `.env` and change the variables to match your dev environment

2. Next, open `config/auth.php` to change the url's to match your install

3. Then run the commands `php codex migrate && php codex db:seed` to run the database migrations and seed the database. 
The default password for all accounts is `tUB2sQoPuuX*3pycL0HGYMs2#!`.

4. If you don't seed the database, visit the url http://codefy.local/register/ to register your first account
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/codefy-register.png" width="660" alt="Register Screen">
</h3>

then visit http://codefy.local/login/ to log in with the new credentials, and you will be redirected to the backend's dashboard.
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/codefy-login.png" width="660" alt="Login Screen">
</h3>
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/codefy-dashboard.png" width="660" alt="Dashboard">
</h3>

the profile page is where you can update your profile.
<h3 align="center">
    <img src="https://downloads.joshuaparker.blog/images/codefy-profile.png" width="660" alt="Profile Screen">
</h3>

This is a very simple app to get you started. Check out the code in the `src` directory which makes up the majority of the admin backend, 
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

### .env Updates Part 1

Update the following lines in your .env file:

    // for ddev, it's usually /var/www/html
    APP_BASE_PATH=/var/www/html

    // should be formatted like so: https://codefy.ddev.site/
    APP_BASE_URL=

Restart DDEV to apply changes:

    ddev restart

Now you should be able to run terminal commands like so:

    ddev codex generate:key:file

    ddev codex migrate

    ddev codex db:seed

### .env Updates Part 2

Now update the following lines in your .env file, by running the following command (`ddev codex ddd:uuid`) twice for 
two different strings:

!!!note
    Place the strings in single quotes so that the dashes (`-`) don't cause issues.
    
    APP_KEY=
    
    APP_SALT=

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

## Logging Into the Admin Panel

Once you run the database migrations and seeders, you can log into the admin panel with either of these admin accounts:


| Email                        | Password                     |
|------------------------------|------------------------------|
| `deanna46@example.org`       | `tUB2sQoPuuX*3pycL0HGYMs2#!` |
| `boris54@example.com`        | `tUB2sQoPuuX*3pycL0HGYMs2#!` |
| `webster.cronin@example.net` | `tUB2sQoPuuX*3pycL0HGYMs2#!` |
