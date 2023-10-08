The easiest way to install CodefyPHP is to use composer by creating a new project using the current stable branch of 
the [skeleton app starter](https://github.com/codefyphp/skeleton). Make sure to substitute `project-name` for the name of 
your specific project.

    composer create-project codefyphp/skeleton:1.x project-name

The architecture is pretty simple. The PSR-4 namespace is `App`, and under that namespace you can set the architecture 
as you see fit. Below is a tree of the starter skeleton app:

    ├── App
    │   ├── Application
    │   │   └── Console
    │   │       └── Kernel.php
    │   ├── Domain
    │   ├── Infrastructure
    │   │   ├── Errors
    │   │   ├── Http
    │   │   │   ├── Controllers
    │   │   │   │   └── HomeController.php
    │   │   │   ├── Middleware
    │   │   │   └── Routes
    │   │   ├── Persistence
    │   │   │   └── Repository
    │   │   └── Providers
    │   │       ├── ApiRouteServiceProvider.php
    │   │       ├── AppServiceProvider.php
    │   │       └── WebRouteServiceProvider.php
    │   └── Shared
    ├── bootstrap
    │   ├── app.php
    │   └── phpmig.php
    ├── config
    │   ├── app.php
    │   ├── database.php
    │   ├── filesystem.php
    │   ├── mailer.php
    │   ├── routes.php
    │   └── view.php
    ├── database
    │   └── migrations
    │       ├── 20220925064056_CreateUsersTable.php
    │       └── 20230901025725_CreateEventStoreTable.php
    ├── locale
    ├── public
    │   └── index.php
    ├── resources
    │   └── views
    │       ├── cache
    ├── storage
    │   ├── app
    │   │   └── public
    │   ├── framework
    │   │   ├── cache
    │   │   ├── cookies
    │   │   ├── media
    │   │   ├── sessions
    │   │   └── views
    │   └── logs

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


Once you make server configuration changes, restart the server. Then, in a browser, visit the url `codefy.local` and 
you should see a successful installation.