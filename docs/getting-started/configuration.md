---
title: Configuration
sidebar_title: Configuration
weight: 4
---

All configuration files for the CodefyPHP Framework are stored in the `config` directory. These config files allow you 
to configure security, your database, caching, cookies, and various other aspects of your application.

## Environment Configuration

You can configure sensitive information through environment variables. As you can see in your `config/app.php`, the 
`Codefy\Framework\Helpers\env` function is used to read configuration from the environment.

When you install the starter app, you will see a `File: ./.env.example` file. You will need to manually rename it 
to `.env` and customize the values. Make sure to not commit your `.env` file to version control, or you end up sharing 
sensitive information you don't want others to see.

Once your values are set, you can use the `env()` function to read from the environment.

```php
$appName = env(key: 'APP_NAME', default: 'CodefyPHP Framework');
```

The second value is a default value. This value will be used if the environment value is not set or is null.

### Environment Variable Types

All variables in your `.env` files are parsed as strings, so some reserved values have been created to allow you to 
return a wider range of types from the `env()` function:

| .env Value     | env() Value      |
|----------------|------------------|
| true           | (bool) true      |
| false          | (bool) false     |
| empty          | (string) ""      |
| null           | (null) null      |

If you need to define an environment variable with a value that contains spaces, you may do so by enclosing the value 
in double quotes.

```shell
APP_NAME="CodefyPHP Framework"
```

## General Configuration

Below are the different environment variables that can be set along with their description.

### Application Variables.

- `APP_NAME` - The name of your application.
- `APP_ENV` - The current application environment: development or production.
- `APP_KEY` - You can set this as your api key to use in your application.
- `APP_SALT` - A long private string used for hashing or encryption.
- `APP_DEBUG` - If set to false, error and warnings will print. If set to true, they will not print to screen.
- `APP_BASE_PATH` - Set the base path of your application without trailing slash (/).
- `APP_BASE_URL` - Set the base url of your application with trailing slash (/).

### Mailer Configuration

- `MAILER_HOST` - Outgoing mail server name.
- `MAILER_PORT` - Outgoing mail server port.
- `MAILER_USERNAME` - SMTP username.
- `MAILER_PASSWORD` - SMTP password.
- `MAILER_AUTHMODE` - Authentication mechanism.
- `MAILER_ENCRYPTION` - SSL, TLS, or STARTTLS.
- `MAILER_FROM_EMAIL` - Sender email address. Maybe the same as `MAILER_USERNAME`.
- `MAILER_FROM_NAME` - Application name.
- `MAILER_SENDMAIL_PATH` - Set the path of sendmail if not using SMTP.

### Database Setup

- `DB_CONNECTION` - The default database connection.
- `DB_DSN` - Database driver being used (mysql, postgres, sqlite, sqlserver).
- `DB_TABLE_PREFIX` - Database table prefix.
- `DB_PERSISTENT` -
- `DB_USER` - Database username.
- `DB_PASSWORD` - Database password.

### Redis Setup

- `REDIS_PREFIX` - Namespace
- `REDIS_PERSISTENT` - true or false
- `REDIS_SCHEME` - tcp, unix, tls
- `REDIS_HOST` - 127.0.0.1
- `REDIS_USERNAME` - For protected servers
- `REDIS_PASSWORD` - For protected servers
- `REDIS_PORT` - 6379 
- `REDIS_MAX_RETRIES` - Retries per request
- `REDIS_DB` - Databases 0-15
- `REDIS_CACHE_DB` - Databases 0-15

### Amazon S3

- `AWS_ACCESS_KEY_ID` - S3 access key.
- `AWS_SECRET_ACCESS_KEY` - S3 secret access key.
- `AWS_DEFAULT_REGION` - S3 region (us-east-2, us-west-1).
- `AWS_BUCKET` - S3 bucket.
- `AWS_URL` - S3 url.
- `AWS_ENDPOINT` - S3 endpoint (s3.us-east-2.amazonaws.com, s3.us-west-1.amazonaws.com).

### Logger Email Setup.

- `LOGGER_EMAIL_SUBJECT` - Email subject for log messages.
- `LOGGER_FROM_EMAIL` - Sender email address. Maybe the same as `MAILER_USERNAME`.
- `LOGGER_TO_EMAIL` - Recipient email address.

## Security

When you push your code to production, make sure to set restrictive file permissions for your `.env` file 
(i.e. `chmod 600` or `chmod 400`).

## Encrypting Environment Data

A `.env` file is the most secure way of storing your secrets. To go even further, you can encrypt the data in your
`.env` file. First make sure that you have a `.enc.key` file which has your encryption key. If you don't already have
one, then run the following command:

```shell
php codex generate:key:file
```

If successful, you will find a new file `.enc.key` in the base path where the `codex` command line script is located.

Next, you will need to run the following command to encrypt the data in `.env`.

```shell
php codex encrypt:env
```

When you run the command, the `.env` will remain untouched, but instead, the command will grab the data from `.env`,
encrypt it, and save the encrypted data in `.env.enc`.

You will still have access to the original `.env` in case you need to make future changes and need to re-encrypt. 
Please make sure that `.env` and `.enc.key` are not under version control.

!!! note
    Encrypting your `.env` file should not happen during development since there may be changes/updates that may need 
    to happen often. It should only be done when pushing to version control without the key or when pushing to 
    production with the key (not in root, but some secure place on the server).

### Decrypting .env Data

In order for the system to decrypt the environment data during runtime, you need to set the bool parameter in the
`withEncryptedEnv()` method to `true` (line 20):

```php linenums="1" hl_lines="23"
<?php

declare(strict_types=1);

use Application\Provider\DatabaseServiceProvider;
use Application\Provider\ViewServiceProvider;
use Codefy\Framework\Application as CodefyApp;
use Codefy\Framework\Providers\AssetsServiceProvider;
use Codefy\Framework\Providers\LocalizationServiceProvider;
use Qubus\Exception\Data\TypeException;

use function Codefy\Framework\Helpers\env;

try {
    $app = CodefyApp::create(
        config: [
            'basePath' => env(
                key: 'APP_BASE_PATH',
                default: dirname(path: __DIR__)
            )
        ]
    )
    ->withEncryptedEnv(bool: true)
    ->withProviders([
        LocalizationServiceProvider::class,
        DatabaseServiceProvider::class,
        AssetsServiceProvider::class,
        ViewServiceProvider::class,
    ])
    ->withSingletons([
        //
    ])
    ->withRouting(
        web: __DIR__ . '/../routes/web/web.php',
        api: __DIR__ . '/../routes/api/rest.php',
    )->return();

    $app->share(nameOrInstance: $app);

    return $app::getInstance();
} catch (TypeException|ReflectionException $e) {
    return $e->getMessage();
}
```

## Accessing Configuration Values

Majority of the configuration options/files are stored in the config directory: `File: ./config`. You may easily access 
your configuration values by using `Codefy\Framework\Proxy\Codefy::$PHP->configContainer` or by using the 
`config()` helper anywhere in your application. The configuration values may be accessed using "dot" syntax,
which includes the `name` of the file and `key` you wish to access. A default value may also be specified and will be
returned if the configuration option does not exist:

```php title="Type Hinted"
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Http\BaseController;
use Codefy\Framework\Proxy\Codefy;
use Psr\Http\Message\ResponseInterface;

class PostController extends BaseController
{
    public function index(): ResponseInterface
    {
        $timezone = Codefy::$PHP->configContainer
            ->getConfigKey(key: 'app.timezone');
    }

    ```
}
```

```php
$timezone = Codefy\Framework\Helpers\config(key: 'app.timezone');

// Use the default value if the configuration value does not exist.
$timezone = config(key: 'app.timezone', default: 'America/New_York');
```

In the above example, `app` is the filename (`./config/app.php`) and `timezone` is the array key.

