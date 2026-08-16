---
title: Event Bus
sidebar_title: Event Bus
order: 2
---

As explained in the Busses section, an event bus signals that something has happened. In CodefyPHP, the event bus can 
be used as a simple pub/sub. You can capture what has happened and then pass it on to a queue to be processed later.

Let’s say for example that you want to send an email when ever a new post is created. If done synchronously, the user 
could be waiting until the email has been sent. But if done asynchronously, it can be queued and handled at a later 
time. How you process a queue goes beyond the scope of this documentation.

### Command

To start off we must have a command and then a command handler to work with. First let’s start off with our `CreatePostCommand`:

```php
<?php

declare(strict_types=1);

namespace Domain\Post\Command;

use Domain\Post\ValueObject\Content;
use Domain\Post\ValuObject\PostId;
use Domain\Post\ValuObject\Title;
use Codefy\CommandBus\Command;

final class CreatePostCommand implements Command
{
    public function __construct(
        private PostId $postId,
        private Title $title,
        private Content $content,
    ) {
    }

    public function postId(): PostId
    {
        return $this->postId;
    }

    public function title(): Title
    {
        return $this->title;
    }

    public function content(): Content
    {
        return $this->content;
    }
}
```

As you can see, our command is a simple DTO. Next, the command will need a command handler. A command handler could 
depend on an `EventBus` implementation, or it can depend on `AggregateRepository` or `EventSourcedAggregateRepository`. 
`EventBus` and `AggregateRepository`/`EventSourcedAggregateRepository` should not be used in the same command handler. 
The recommended use for `EventBus` is on a new creation of the aggregate, while 
`AggregateRepository`/`EventSourcedAggregateRepository` should be used on changes/updates.

```php
<?php

declare(strict_types=1);

namespace Domain\Post\Command;

use Codefy\CommandBus\Command;
use Codefy\EventBus\EventBus;
use Domain\Post\Post;
use Domain\Post\ValueObject\Content;
use Domain\Post\ValueObject\PostId;
use Domain\Post\ValueObject\Title;
use Infrastructure\Service\PostSubscriber;
use Qubus\Exception\Data\TypeException;

final class CreatePostCommandHandler
{
    public function __construct(public readonly EventBus $eventBus) 
    {
        $this->eventBus->subscribe(subscriber: new PostSubscriber());
    }

    /**
     * @throws TypeException
     */
    public function handle(CreatePostCommand $command)
    {
        $post = Post::createPostWithoutTap(
            postId: new PostId(value: $command->postId()),
            title: new Title(value: $command->title()),
            content: new Content(value: $command->content())
        );

        $this->eventBus->publish(...$post->pullDomainEvents());


        $post->clearRecordedEvents();

    }
}
```

The above command handler has `EventBus` as a dependency since it handles the creation of a new aggregate. 
`PostSubscriber` is called in the constructor as something the event bus should listen for. `PostSubscriber` could 
contain your projections and/or something that should be queued or acted upon at a later time.

Something else to notice is `$post->clearRecordedEvents()`. When creating handlers that depend on `EventBus`, you need 
to make sure to call the `clearRecordedEvents` method on the aggregate.

```php
<?php

declare(strict_types=1);

namespace Domain\Post\Command;

use Codefy\CommandBus\Command;
use Codefy\CommandBus\CommandHandler;
use Codefy\Domain\Aggregate\AggregateRepository;
use Domain\Post\Post;
use Domain\Post\ValueObject\Content;
use Domain\Post\ValueObject\PostId;
use Domain\Post\ValueObject\Title;
use Qubus\Exception\Data\TypeException;

final class CreatePostCommandHandler
{
    public function __construct(
        public readonly AggregateRepository $aggregateRepository
    ) {
    }

    /**
     * @throws TypeException
     */
    public function handle(CreatePostCommand $command)
    {
        $post = Post::createPostWithoutTap(
            postId: new PostId($command->postId()),
            title: new Title($command->title()),
            content: new Content($command->content())
        );

        $this->aggregateRepository->saveAggregateRoot(aggregate: $post);
    }
}
```

In the second example, you see that the command handler has a dependency on `AggregateRepository` which is an interface. 
You can use `EventSourcedAggregateRepository` to meet the dependency, extend it, or create your own implementation of 
`AggregateRepository`.

### Subscriber

In the constructor, the `subscribe` method is called and the event bus will listen for the `PostSubscriber`. Below is a 
simple implementation of `DomainEventSubscriber`.

```php
<?php

declare(strict_types=1);

namespace Infrastructure\Service;

use Codefy\EventBus\DomainEventSubscriber;
use Codefy\Traits\SubscriberAware;
use Domain\Event\PostWasCreated;
use Domain\Post\Service\PostProjection;

final class PostSubscriber implements DomainEventSubscriber
{
    use SubscriberAware;

    private array $eventType = [
        PostWasCreated::class
    ];

    private PostProjection $projection;

    public function __construct(PostProjection $projection)
    {
        $this->projection = $projection;
    }

    public function handle(PostWasCreated $event)
    {
        $this->projection->projectWhenPostWasCreated($event);
    }
}
```

`PostSubscriber` registers an event to listen for via the `$eventType` array: `PostWasCreated`. If the vent gets 
published: `$this->eventBus->publish(…$post->pullDomainEvents())`, then it will execute whatever code that needs 
executing (i.e. inserting data into a database read table).

The `save` method in our `PostRespository` is the same method injected into our `CreatePostCommandHandler`. Codefy 
ships with an implementation of `EventStore` (memory only): `Codefy\EventBus\InMemoryEventStore`.

