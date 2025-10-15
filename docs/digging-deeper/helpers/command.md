---
title: command
sidebar_title: command
---


Description
-----------

Dispatches the given `$command` through the CommandBus.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\command;

function command(Command $command): void;
```

## Example

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

Parameters
----------

**$command** (`Codefy\CommandBus\Command`) (required) Command to pass through the command bus.