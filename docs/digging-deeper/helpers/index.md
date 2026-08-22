---
title: Index
sidebar_title: Index
summary: Browse the CodefyPHP and Qubus PHP helper reference for requests, configuration, collections, strings, security, translation, mail, queues, and users.
keywords: codefyphp-helpers,qubus-helpers,php-functions
weight: 0
---

<div class="column-list" markdown="1">

[abort](#abort)
[abort_if](#abort_if)
[add_trailing_slash](#add_trailing_slash)
[app](#app)
[array_list](#array_list)
[ask](#ask)
[command](#command)
[compact_unique_array](#compact_unique_array)
[concat_ws](#concat_ws)
[config](#config)
[convert_array_to_object](#convert_array_to_object)
[each__](#each__)
[esc_attr](#esc_attr)
[esc_attr__](#esc_attr__)
[esc_html](#esc_html)
[esc_html__](#esc_html__)
[esc_js](#esc_js)
[esc_js_value](#esc_js_value)
[esc_textarea](#esc_textarea)
[esc_url](#esc_url)
[explode_array](#explode_array)
[flatten_array](#flatten_array)
[gate](#gate)
[gravatar](#gravatar)
[gravatar_profile](#gravatar_profile)
[is_error](#is_error)
[is_false](#is_false)
[is_null__](#is_null__)
[is_true__](#is_true__)
[mail](#mail)
[method_field](#method_field)
[now](#now)
[php_like](#php_like)
[php_where](#php_where)
[purify_html](#purify_html)
[queue](#queue)
[remove_trailing_slash](#remove_trailing_slash)
[rescue](#rescue)
[site_url](#site_url)
[sort_element_callback](#sort_element_callback)
[strip_tags__](#strip_tags__)
[t__](#t__)
[throw_if](#throw_if)
[trim__](#trim__)
[truncate_string](#truncate_string)
[unslash](#unslash)
[user](#user)

</div>

## abort

Throw an [HttpException](../../api/Qubus/Exception/Http/HttpException.md) with the given data. [More Info...](abort.md)

```php
<?php

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\abort;
use function Codefy\Framework\Helpers\ask;

function find_user_by_id(string $id): object
{
    $user = ask(new FindUserByIdQuery(['userId' => $id]));

    if (!$user) {
        abort(
            code: 404,
            uri: '/admin/',
            message: 'User not found.'
        );
    }

    return $user;
}
```

## abort_if

Abort (throw an HttpException) if the given condition is true. [More Info...](abort_if.md)

```php
<?php

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\abort_if;
use function Codefy\Framework\Helpers\ask;

function find_user_by_id(string $id): object|bool
{
    return ask(new FindUserByIdQuery(['userId' => $id]));
}

abort_if(
    condition: false === find_user_by_id('01KDNPDG0YE32R47FBC6R0VBE2'),
    code: 404,
    uri: '/admin/',
    message: 'User not found.'
);
```

## abort_unless

Abort (throw an HttpException) unless the given condition is true. [More Info...](abort_unless.md)

```php
<?php

use function Codefy\Framework\Helpers\abort_if;
use function Codefy\Framework\Helpers\gate;

abort_unless(
    condition: gate('edit_user'),
    code: 403,
    uri: '/admin/',
    message: 'Access denied.'
);
```

## add_trailing_slash

Appends a trailing slash.

Will remove trailing forward and backslashes if it exists already before adding a trailing forward slash. This prevents
double slashing a string or path. [More Info...](add_trailing_slash.md)

## app

Returns the `Qubus\Injector\ServiceContainer` or `Psr\Container\ContainerInterface` instance. You may pass a `class`,
`alias`, or `interface` name to resolve it from the container as well as any needed parameters. [More Info...](app.md)

!!!warning
    This helper is available for ease of use, but should be used sparingly. It is highly recommended that you use
    a [`ServiceProvider`](../../getting-started/dependency-injection.md#service-provider-contracts) and dependency injection.

```php
<?php

use function Codefy\Framework\Helpers\app;

return app(); // returns ContainerInterface|ServiceContainer
```

```php
<?php

use Qubus\Routing\Psr7Router;

use function Codefy\Framework\Helpers\app;

$router = app(name: Psr7Router::class); // resolves router from Injector
```

```php
<?php

use Qubus\Routing\Psr7Router;

use function Codefy\Framework\Helpers\app;

$router = app()->alias(
    original: \Psr\SimpleCache\CacheInterface::class,
    alias: \Qubus\Cache\Psr16\SimpleCache::class
); // binds alias to the original (interface)
```

## array_list

Return a collection based on type. [More Info...](array_list.md)

```php
<?php

use function Qubus\Support\Helpers\array_list;

$callables = [
    fn() => 'Hello World!',
    fn() => 'I love programming!',
    fn() => 'I love PHP!'
];

$list = array_list('callable');
foreach ($callables as $callable) {
    $list->add($callable);
}

echo $list->type(); // callable
// or
echo $list->all()[2](); // I love PHP!
```

To use the `array_list()` helper beyond the example above, check out [`Collections`](../collections.md).
The `array_list()` helper and the `collect()` helper inherit some of the same methods but may return different results.
Another difference is that `collect()` can return a mixture of primitives and data structures, while `array_list()`
returns an array of the same specified primitive type.

## ask

Queries the given query and returns a result if any. [More Info...](ask.md)

```php
<?php

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\ask;

$userId = '01KFRYWSVYEFS9MHXHZR0JDF59';

$query = new FindUserByIdQuery(data: [
    'userId' => $userId,
]);

$user = ask($query);
```

## command

Dispatches the given `$command` through the CommandBus. [More Info...](command.md)

```php
<?php

use App\Domain\Post\Commands\CreatePostCommand;
use App\Domain\Post\ValueObject\Content;
use App\Domain\Post\ValueObject\PostId;
use App\Domain\Post\ValueObject\Title;

use function Codefy\Framework\Helpers\command;

$createPostCommand = new CreatePostCommand();
$createPostCommand->postId = new PostId();
$createPostCommand->title = new Title(value: 'New Post Title');
$createPostCommand->content = new Content(value: 'Short form content.');

command(command: $createPostCommand);
```

## compact_unique_array

Strips out all duplicate values and compact the array. [More Info...](compact_unique_array.md)

## concat_ws

Concatenation with separator. [More Info...](concat_ws.md)

```php
echo concat_ws('CodefyPHP', 'Framework'); // "CodefyPHP,Framework"

echo concat_ws(
    'I love mangoes',
    'grapes',
    ', ',
    'pears',
    'and pineapple on pizza.'
); // "I love mangoes, grapes, pears, and pineapple on pizza."
```

## config

Return the `ConfigContainer` instance or get / set the specified configuration value. The configuration values may be
accessed using "dot" syntax, which includes the name of the file and the option you wish to access. You may also
provide a default value that will be returned if the configuration option does not exist. [More Info...](config.md)

```php
<?php

use function Codefy\Framework\Helpers\config;

$timezone = config(key: 'app.timezone');
// or
$timezone = config(key: 'app.timezone', default: 'America/Los_Angeles');
```

```php
<?php

use function Codefy\Framework\Helpers\config;

$config = config(); // returns the ConfigContainer instance.
```

```php
<?php

use function Codefy\Framework\Helpers\config;

config(key: ['app' => ['locale' => 'es']]); // set app.locale value to 'es'.
```

## convert_array_to_object

Takes an array and turns it into an object. [More Info...](convert_array_to_object.md)

## each__

Provides a compatibility replacement for PHP's removed `each()` function. [More Info...]()

```php
use function Qubus\Security\Helpers\each__;

$items = ['first' => 'A', 'second' => 'B'];
$pair = each__($items);

// [0 => 'first', 1 => 'A', 'key' => 'first', 'value' => 'A']
```

## esc_attr

Escaping for HTML attributes. [More Info...](esc_attr.md)

## esc_attr__

Escapes a translated string to make it safe for HTML attribute. [More Info...](esc_attr__.md)

## esc_html

Escapes html.

## esc_html__

Escapes a translated string to make it safe for HTML output. [More Info...](esc_html.md)

## esc_js

Escaping for inline javascript. [More Info...](esc_js.md)

```php
use function Qubus\Security\Helpers\esc_js;
use function Qubus\Security\Helpers\esc_js_value;

$handler = 'showMessage(' . esc_js_value(value: $message) . ');';
echo '<button onclick="' . esc_js(string: $handler) . '">Show</button>';
```

## esc_js_value

Secures untrusted data for JavaScript syntax. [More Info...](esc_js_value.md)

```php
<?php

use function Qubus\Security\Helpers\esc_js;
use function Qubus\Security\Helpers\esc_js_value;

require 'vendor/autoload.php';

$message = "Joshua's \"code\"";

// First: serialize untrusted data as a JavaScript value.
$handler = 'alert(' . esc_js_value(value: $message) . ');';

// Second: escape the complete handler for its HTML attribute.
$attribute = esc_js(string: $handler);

echo '<input type="button" value="push" onclick="' . $attribute . '" />';
```

## esc_textarea

Escapes for textarea.  [More Info...](esc_textarea.md)

## esc_url

Escapes a url. [More Info...](esc_url.md)

## explode_array

Splits a string using one or more delimiters. [More Info...](explode_array.md)

```php
use function Qubus\Security\Helpers\explode_array;

$colors = explode_array(delimiters: ',', string: 'red,green,blue');
// ['red', 'green', 'blue']

$tokens = explode_array(delimiters: [',', '|'], string: 'red,green|blue');
// ['red', 'green', 'blue']

$rows = explode_array(delimiters: ',', string: ['a,b', 'c,d']);
// ['a', 'b', 'c', 'd']
```

## flatten_array

Recursively flattens a multidimensional array into one level. [More Info...](flatten_array.md)

```php
use function Qubus\Security\Helpers\flatten_array;

$flat = flatten_array(array: [
    'user' => [
        'name' => 'Ada',
        'roles' => ['admin', 'editor'],
    ],
    'active' => true,
]);

// ['name' => 'Ada', 0 => 'admin', 1 => 'editor', 'active' => true]
```

## gate

Returns a `Codefy\Framework\Auth\Gate` instance or true if user has specified permission. [More Info...](gate.md)

```php
<?php

use function Codefy\Framework\Helpers\gate;

$auth = gate(); // returns Gate instance
// or
$auth = gate(permission: 'edit_user');
// or
$auth = gate(
    permission: 'edit_user',
    ruleParams: ['userId' => $userId, 'post' => $post]
);
```

## gravatar

Return a new Gravatar Image instance. [More Info...](gravatar.md)

```php
<?php

// Get a Gravatar image instance:
$image = gravatar('email@example.com');
// return: Gravatar\Image

// Get a Gravatar image URL:
$imageUrl = gravatar('email@example.com')->url();
// return: //www.gravatar.com/avatar/5658ffccee7f0ebfda2b226238b1eb6e

// Show a Gravatar image URL:
echo gravatar('email@example.com');
// output: //www.gravatar.com/avatar/5658ffccee7f0ebfda2b226238b1eb6e

// With optional parameters:
$avatar = gravatar('email@example.com')
    ->size(120)
    ->defaultImage('robohash')
    ->maxRating('pg')
    ->extension('jpg');
echo $avatar;

// Or set the email later:
$avatar = gravatar()
    ->email('email@example.com')
    ->size(200);
echo $avatar;

// With initials (convenience method):
$avatar = gravatar('email@example.com')
    ->withInitials('JD')
    ->size(120);
echo $avatar;
```

## gravatar_profile

Return a new Gravatar Profile instance. [More Info...](gravatar_profile.md)

```php
<?php

// Get a Gravatar profile instance:
$profile = gravatar_profile('email@example.com');
// return: Gravatar\Profile

// Get a Gravatar profile URL:
echo gravatar_profile('email@example.com');
// output: https//www.gravatar.com/5658ffccee7f0ebfda2b226238b1eb6e

// With format parameter:
$profileUrl = gravatar_profile('email@example.com')
    ->format('json')
    ->url();
```

## is_error

Check whether variable is an Error instance. [More Info...](is_error.md)

```php
<?php

use Qubus\Error\Error;

use function Qubus\Error\Helpers\is_error;

function has_permission(string $permission): Error|string
{
    if ($permission === '') {
        return new Error('The permission value is invalid');
    }
    
    return $permission;
}

$permission = has_permission('');

if (is_error($permission)) {
    echo $permission->getMessage();
}
```

## is_false

Checks if return is false. [More Info...](is_false__.md)

## is_null__

Checks if a variable is null. [More Info...](is_null__.md)

Works the same as PHP’s native `is_null()` function.

## is_true__

Checks if return is true. [More Info...](is_true__.md)

## mail

An alternative to using PHP's native mail function with other options for SMTP (default), Qmail, and Sendmail.  [More Info...](mail.md)

```php
<?php

use function Codefy\Framework\Helpers\mail;
use function Codefy\Framework\Helpers\storage_path;

try {
    return mail(
        to: ['test@example.com' => 'Recipient Name'],
        subject: 'Email Message',
        message: 'This is a <strong>simple</strong> email message.',
        headers: [
            'cc' => [
                'recipientone@example.com' => 'Recipient One',
                'recipienttwo@example.com' => 'Recipient Two'
            ],
            'bcc' => ['another@example.com' => 'Another Recipient'],
        ],
        attachments: [storage_path('file.pdf')]
    );
} catch (\PHPMailer\PHPMailer\Exception | Exception $e) {
    return $e->getMessage();
}
```

## method_field

This function generates an HTML hidden input field containing the spoofed value of the form's HTTP verb. [More Info...](method_field.md)

```php
<form method="POST">
    <?=\Codefy\Framework\Helpers\method_field('put');?>
</form>
```

```html
<form method="POST">
    <input type="hidden" name="_method" value="PUT" />
</form>
```

## now

Create a new Carbon instance for the current datetime. [More Info...](now.md)

```php
<?php

use function Qubus\Support\Helpers\now;

$now = now();
// or with timezone
$now = now('America/Los_Angeles');
```

## php_like

SQL Like operator in PHP. [More Info...](php_like.md)

```php
<?php

php_like('%uc%','Lucy'); //true

php_like('%cy', 'Lucy'); //true

php_like('lu%', 'Lucy'); //true

php_like('%lu', 'Lucy'); //false

php_like('cy%', 'Lucy'); //false
```

## php_where

SQL Where operator in PHP. [More Info...](php_where.md)

```php
<?php

// Where dog is in ['cat', 'bear', 'chicken', 'dog']
php_where('dog', 'in', ['cat', 'bear', 'chicken', 'dog']); // true
```

## purify_html

Accepts untrusted rich-text HTML and returns a safe HTML fragment for an HTML document body. It 
preserves common formatting while removing executable markup, unsafe attributes, and dangerous URL schemes.  [More Info...](purify_html.md)

```php
<?php

use function Qubus\Security\Helpers\purify_html;

$untrustedHtml = <<<'HTML'
<p class="intro" onclick="alert(1)">
    Hello <strong>world</strong>.
    <a href="javascript:alert(1)" target="_blank">Open</a>
</p>
HTML;

$safeHtml = purify_html(string: $untrustedHtml);

echo $safeHtml;
```

## queue

Helper function to send a job to a queue or dispatch a job. [More Info...](queue.md)

Send a job to the queue:

```php
<?php

return queue(
    queue: new \Application\Service\NewEmailSignup(
        request: new \Qubus\Http\ServerRequest()
    )
)->createItem();
// returns the last inserted id (ULID)
```

Dispatch a queued job:

```php
<?php

return queue(queue: $queue)->dispatch();
// returns bool; $queue is the object that is plucked out of the queue
```

## remove_trailing_slash

Removes trailing forward slashes and backslashes if they exist. [More Info...](remove_trailing_slash.md)

## rescue

Catches a potential exception and returns a default value. [More Info...](rescue.md)

```php
<?php

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\ask;
use function Qubus\Support\Helpers\rescue;

$query = ask(new FindUserByIdQuery(['userId' => '01KFRYX7G3E8PB6QRJ84ZG7J7D']));

// If record exists, you get the result
// If not, the code executes without throwing an error
$user = rescue(function () use($query) {
    return $query;
});

$user = rescue(function () use($query) {
    return $user;
}, null);
```

## site_url

Returns the url of your application. [More Info...](site_url.md)

## sort_element_callback

Sorts a structured array by `Name` property. [More Info...](sort_element_callback.md)

## strip_tags__

Properly strip all HTML tags including script and style (default).

This differs from PHP’s native `strip_tags()` function because this function removes the contents of the tags. E.g.
`strip_tags__( '<script>something</script>' )` will return `''`. [More Info...](strip_tags__.md)

```php
<?php

$string = '<b>sample</b> text with <div>tags</div>';

strip_tags__(string: $string); //returns 'text with'

strip_tags__(
    string: $string,
    removeBreaks: false,
    tags: '<b>'
); //returns '<b>sample</b> text with'

strip_tags__(
    string: $string,
    removeBreaks: false, 
    tags: '<b>',
    invert: true
); //returns 'text with <div>tags</div>'
```

## t__

Translates a string. [More Info...](t__.md)

## throw_if

Throw the given exception if the given condition is true. [More Info...](throw_if.md)

```php
<?php

$auth = gate('edit_user') === false;
throw_if($auth, new AuthException('Access denied.'));
// or
throw_if($auth, AuthException::class, 'Access denied');
```

## trim__

Despite its name, this helper removes all whitespace—not only whitespace at the beginning and end. [More Info...](trim__.md)

```php
use function Qubus\Security\Helpers\trim__;

$compact = trim__(string: " A value\nwith spaces\t");
// 'Avaluewithspaces'

$parts = trim__(string: ['first value', "second\nvalue"]);
// ['firstvalue', 'secondvalue']
```

## truncate_string

Truncates a string to the given length. It will optionally preserve HTML tags if `$isHtml` is set to true. [More Info...](truncate_string.md)

## unslash

Recursively remove backslashes from a string or nested array of strings. [More Info...](unslash.md)

```php
use function Qubus\Security\Helpers\unslash;

$input = [
    'name' => "O\\'Reilly",
    'quote' => '\\"Hello\\"',
];

$clean = unslash(value: $input);
// ['name' => "O'Reilly", 'quote' => '"Hello"']
```

## user

Returns the authenticated user. [More Info...](user.md)

```php
<?php

use function Codefy\Framework\Helpers\user;

$user = user();
echo $user->user_id; // returns the user's ID
echo $user->email; // returns the user's email
```







