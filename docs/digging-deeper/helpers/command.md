---
title: command
sidebar_title: command
---


Description
-----------

Dispatches the given `$command` through the CommandBus.

Usage
-----

    <?php

    use function Codefy\Framework\Helpers\command;
    
    function command(Command $command): void;

## Example

    <?php
    
    use App\Domain\Content;
    use App\Domain\Post;
    use App\Domain\Post\Command\CreatePostCommand;
    use App\Domain\PostId;
    use App\Domain\Title;
    
    use function Codefy\Framework\Helpers\command;
    
    $createPostCommand = new CreatePostCommand();
    $createPostCommand->postId = new PostId();
    $createPostCommand->title = new Title(value: 'New Post Title');
    $createPostCommand->content = new Content(value: 'Short form content.');
    
    command(command: $createPostCommand);


Parameters
----------

**$command** (`Codefy\CommandBus\Command`) (required) Command to pass through the command bus.