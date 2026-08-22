---
title: CodefyPHP 3 Is Here
description: Discover CodefyPHP 3 features for asset management, queued jobs, scheduled tasks, environment encryption, middleware, and search optimization.
summary: Discover CodefyPHP 3 features for asset management, queued jobs, scheduled tasks, environment encryption, middleware, and search optimization.
keywords: codefyphp-3,php-framework,release-notes
date:
  created: 2025-10-15 08:00:00
authors: [nomadicjosh]
---

# CodefyPHP 3 Is Here

CodefyPHP 3 is the newest release of the PHP web framework for building complex applications. This release includes a 
plethora of changes, updates, enhancements, and bug fixes. Due to config changes cross many file of the config files, 
it is recommended that you read thoroughly through the [documentation](https://codefyphp.com/docs/) and the 
[skeleton](https://github.com/codefyphp/skeleton) app to ascertain the best way to upgrade your existing applications.

<!-- more -->

From asset management to encrypting your environment data, CodefyPHP 3 makes it easier to create secure, robust applications 
that scale over time. Below are just a few of the changes you will find in version 3.

This new release brings lots of changes, updates, and bug fixes:

- fixed: marking service providers as registered.
- feature: console commands
    -  `vendor:publish`
    - [`asset:flush`](../../digging-deeper/assets.md#pipeline)
    - [`generate:key:file`](../../getting-started/configuration.md#encrypting-environment-data)
    - [`encrypt:env`](../../getting-started/configuration.md#encrypting-environment-data)
    - [`queue:*`](../../digging-deeper/queues.md)
- feature: helpers
    - [`command()`](../../digging-deeper/helpers/command.md)
    - [`ask()`](../../digging-deeper/helpers/ask.md)
    - [`trans()`](../../digging-deeper/localization.md#translation-helpers)
    - [`queue()`](../../digging-deeper/helpers/queue.md)
- feature: [job queues](../../digging-deeper/queues.md)
- feature: [schedule tasks](../../digging-deeper/scheduler.md#scheduling-tasks)
- feature: middlewares
    - Content cache
    - HTTP cache
    - Referer Spam
    - API
    - Rate Limiter
    - HTML, JS, and CSS minifier
- feature: [SEO helper](../../digging-deeper/seo.md) for better SEO
- enhancement: removed native providers and console commands from configs
- feature: automatic loading of native providers and console commands

## Command Bus

With the new `command()` helper, there is less initialization and code duplication when you need to pass a command 
through the command bus:

```php
<?php

declare(strict_types=1);

namespace App\Domain\Post\Commands;

use App\Domain\Post;
use App\Domain\Post\ValueObject\Content;
use App\Domain\Post\ValueObject\PostId;
use App\Domain\Post\ValueObject\Title;
use Codefy\CommandBus\Command;
use Codefy\Domain\Aggregate\AggregateRepository;

class CreatePostCommand implements Command
{
    public PostId $postId;
    public Title $title;
    public Content $content;
}

class CreatePostCommandHandler
{
    public function __construct(public readonly AggregateRepository $aggregateRepository)
    {
    }

    public function handle(CreatePostCommand $command): void
    {
        $post = Post::createPostWithoutTap(
            postId: $command->postId,
            title: $command->title,
            content: $command->content
        );
        $this->aggregateRepository->save(aggregate: $post);
    }
}
```

The old way of passing the command through the bus:

```php

use App\Domain\Post\Commands\CreatePostCommand;
use App\Domain\Post\ValueObject\Content;
use App\Domain\Post\ValueObject\PostId;
use App\Domain\Post\ValueObject\Title;
use Codefy\CommandBus\Busses\SynchronousCommandBus;
use Codefy\CommandBus\Containers\ContainerFactory;
use Codefy\CommandBus\Odin;
use Codefy\CommandBus\Resolvers\NativeCommandHandlerResolver;

// passing the command through the bus
$resolver = new NativeCommandHandlerResolver(
    container: ContainerFactory::make(config: config(key: 'commandbus.container'))
);
$odin = new Odin(bus: new SynchronousCommandBus($resolver));

$odin->execute($command);

$createPostCommand = new CreatePostCommand();
$createPostCommand->postId = new PostId();
$createPostCommand->title = new Title(value: 'New Post Title');
$createPostCommand->content = new Content(value: 'Short form content.');

$odin->execute(command: $createPostCommand);
```

Verses the new way of passing the command through the bus:

```php

use App\Domain\Post\Commands\CreatePostCommand;
use App\Domain\Post\ValueObject\Content;
use App\Domain\Post\ValueObject\PostId;
use App\Domain\Post\ValueObject\Title;
use Codefy\CommandBus\Odin;

use function Codefy\Framework\Helpers\command;

$createPostCommand = new CreatePostCommand();
$createPostCommand->postId = new PostId();
$createPostCommand->title = new Title(value: 'New Post Title');
$createPostCommand->content = new Content(value: 'Short form content.');

command(command: $createPostCommand);
```

## Asset Management

Asset management should't be chore. You can now setup a collection of assets in your `./config/assets.php` file, and 
use theme in your views:

```php title="Collection in ./config/assets.php"
'collections' => [
    'one'   => 'one.css',
    'two'   => ['two.css', 'two.js'],
    'external'  => ['//example.com/external.css', '//secure.example.com/https.css', '//example.com/protocol/agnostic.js'],
    'mix'   => ['internal.css', '//example.com/external.js'],
    'nested' => ['one', 'two'],
    'duplicated' => ['nested', 'one.css','two.css', 'three.js'],
],
```

After setup, you can use the above collection in different scenarios:

Using `Codefy\Framework\Proxy\Codefy::$PHP->assets->add('two');` will result in

```html
<!-- CSS -->
<link type="text/css" rel="stylesheet" href="css/two.css" />
<!-- JS -->
<script type="text/javascript" src="js/two.js"></script>
```

## Search Engine Optimization

Generate schema.org:

```php
<?php

use App\Shared\Services\Server;
use Codefy\Framework\Support\SeoFactory;

$schema = SeoFactory::schema(
    SeoFactory::thing('Website', [
        'url'          => Server::siteUrl(),
        'logo'         => Server::siteUrl('static/assets/img/auth/auth-logo.png'),
        'contactPoint' => SeoFactory::thing('ContactPoint', [
            'telephone' => '+1-000-555-1212',
            'contactType' => 'customer service'
        ])
    ])
);

echo '<script type="application/ld+json">' . "\n" . json_encode($schema, JSON_PRETTY_PRINT) . "\n" . '</script>';
```

Will result in (reformatted for presentation):

```html
<script type="application/ld+json">
{
    "@context": "https://schema.org",
    "@graph": [
        {
            "url": "https://codefy.ddev.site/",
            "logo": "https://codefy.ddev.site/static/assets/img/auth/auth-logo.png",
            "contactPoint": {
                "telephone": "+1-000-555-1212",
                "contactType": "customer service",
                "@type": "ContactPoint",
                "@context": "https://schema.org/"
            },
            "@type": "Website",
            "@context": "https://schema.org/"
        }
    ]
}
</script>
```

Along with the above, there is a host of other enhancements, new features and bug fixes in version 3. Check out the 
new [documentation](https://codefyphp.com/docs/) for a full view of what v3.0.0 has to offer.
