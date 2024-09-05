As explained in the Busses section, an event bus signals that something has happened. In CodefyPHP, the event bus can 
be used as a simple pub/sub. You can capture what has happened and then pass it on to a queue to be processed later.

Let’s say for example that you want to send an email when ever a new post is created. If done synchronously, the user 
could be waiting until the email has been sent. But if done asynchronously, it can be queued and handled at a later 
time. How you process a queue goes beyond the scope of this documentation.

### Command

To start off we must have a command and then a command handler to work with. First let’s start off with our `CreatePostCommand`:

    <?php

    declare(strict_types=1);
    
    namespace App\Domain\Commands;
    
    use App\Domain\Content;
    use App\Domain\PostId;
    use App\Domain\Title;
    use Codefy\CommandBus\Command;
    
    class CreatePostCommand implements Command
    {
        public function __construct(public PostId $postId, public Title $title, public Content $content)
        {
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

As you can see, our command is a simple DTO. Next, the command will need a command handler. A command handler could 
depend on an `EventBus` implementation, or it can depend on `AggregateRepository` or `EventSourcedAggregateRepository`. 
`EventBus` and `AggregateRepository`/`EventSourcedAggregateRepository` should not be used in the same command handler. 
The recommended use for `EventBus` is on a new creation of the aggregate, while 
`AggregateRepository`/`EventSourcedAggregateRepository` should be used on changes/updates.

    <?php

    declare(strict_types=1);
    
    namespace App\Domain\Commands;
    
    use App\Domain\Content;
    use App\Domain\Post;
    use App\Domain\PostId;
    use App\Domain\Title;
    use App\Infrastructure\PostSubscriber;
    use Codefy\CommandBus\Command;
    use Codefy\EventBus\EventBus;
    use Qubus\Exception\Data\TypeException;
    
    class CreatePostCommandHandler
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

The above command handler has `EventBus` as a dependency since it handles the creation of a new aggregate. 
`PostSubscriber` is called in the constructor as something the event bus should listen for. `PostSubscriber` could 
contain your projections and/or something that should be queued or acted upon at a later time.

Something else to notice is `$post->clearRecordedEvents()`. When creating handlers that depend on `EventBus`, you need 
to make sure to call the `clearRecordedEvents` method on the aggregate.

    <?php

    declare(strict_types=1);
    
    namespace App\Domain\Commands;
    
    use Codefy\CommandBus\Command;
    use Codefy\CommandBus\CommandHandler;
    use Codefy\Domain\Aggregate\AggregateRepository;
    use Codefy\Tests\Domain\Content;
    use Codefy\Tests\Domain\Post;
    use Codefy\Tests\Domain\PostId;
    use Codefy\Tests\Domain\Title;
    use Qubus\Exception\Data\TypeException;
    
    class CreatePostCommandHandler
    {
        public function __construct(public readonly AggregateRepository $aggregateRepository)
        {
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

In the second example, you see that the command handler has a dependency on `AggregateRepository` which is an interface. 
You can use `EventSourcedAggregateRepository` to meet the dependency, extend it, or create your own implementation of 
`AggregateRepository`.

### Subscriber

In the constructor, the `subscribe` method is called and the event bus will listen for the `PostSubscriber`. Below is a 
simple implementation of `DomainEventSubscriber`.

    <?php

    declare(strict_types=1);
    
    namespace App\Infrastructure;
    
    use App\Domain\Event\PostWasCreated;
    use Codefy\EventBus\DomainEventSubscriber;
    use Codefy\Traits\SubscriberAware;
    
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

`PostSubscriber` registers an event to listen for via the `$eventType` array: `PostWasCreated`. If the vent gets 
published: `$this->eventBus->publish(…$post->pullDomainEvents())`, then it will execute whatever code that needs 
executing (i.e. inserting data into a database read table).

The `save` method in our `PostRespository` is the same method injected into our `CreatePostCommandHandler`. Codefy 
ships with an implementation of `EventStore` (memory only): `Codefy\EventBus\InMemoryEventStore`.

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.