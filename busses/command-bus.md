CodefyPHP has a command bus called `Odin`. It is a fork of Adam Nicholson’s command bus called [Chief](https://github.com/adamnicholson/Chief).

Command Bus?
------------

> The most common style of interface to a module is to use procedures, or object methods. So if you want a module to 
> calculate a bunch of charges for a contract, you might have a BillingService class with a method for doing the 
> calculation, calling it like this `$billingService->calculateCharges($contract);`. A command oriented interface 
> would have a command class for each operation, and be called with something like this 
> `$cmd = new CalculateChargesCommand($contract); $cmd->execute();`. Essentially you have one command class for each 
> method that you would have in the method-oriented interface. A common variation is to have a separate command 
> executor object that actually does the running of the command. `$command = new CalculateChargesCommand($contract); 
> $commandBus->execute($command);`
>
> 
> Fowler, M. (2003, November 23). _CommandOrientedInterface_. Martin fowler. https://www.martinfowler.com/eaaDev/DomainEvent.html

That ‘executor’ Martin mentions is what we call the command bus. The pattern typically consists of 3 classes:

1.  `Command`: A tiny object containing some data (probably some public properties or array passed to the constructor 
or the use of a payload)
2.  `CommandHandler`: Responsible for running the command through a `handle($command)` method
3.  `CommandBus`: All commands are passed to the bus `execute($command)` method, which is responsible for finding the 
right`CommandHandler` and calling the `handle($command)` method.

For every `Command` in your application, there should be a corresponding `CommandHandler`.

Usage
-----

The example below demonstrates how a command bus design could handle registering a new Post in your system using Odin:

    <?php

    declare(strict_types=1);
    
    namespace App\Commands;
    
    use Codefy\CommandBus\Command;
    use Codefy\CommandBus\Odin;
    use Codefy\Domain\Aggregate\AggregateRepository;
    use App\Domain\Content;
    use App\Domain\Post;
    use App\Domain\PostId;
    use App\Domain\Title;
    
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
    
    $odin= new Odin();
    
    $createPostCommand = new CreatePostCommand();
    $createPostCommand->postId = new PostId();
    $createPostCommand->title = new Title(value: 'New Post Title');
    $createPostCommand->content = new Content(value: 'Short form content.');
    
    $odin->execute(command: $createPostCommand);

### Automatic handler resolution

When you pass a `Command` to `Odin::execute()`, Odin will automatically search for the relevant `CommandHandler` and 
call the `handle()` method:

    <?php

    $odin = new Odin;
    $odin->execute(command: new CreatePostCommand);

By default, this will search for a `CommandHandler` with the same name as your `Command`, suffixed with ‘Handler’, in 
both the current namespace as well as a nested `Handlers` namespace.

So `App\Commands\CreatePostCommand` will automatically resolve to `App\Commands\CreatePostCommandHandler` or 
`App\Commands\Handlers\CreatePostCommandHandler` if either class exists.

Want to implement your own method of automatically resolving handlers from commands? Implement your own version of the 
`Codefy\CommandBus\CommandHandlerResolver` interface to modify the automatic resolution behavior.

### Handlers bound by class name

    <?php

    use Codefy\CommandBus\Odin;
    use Codefy\CommandBus\NativeCommandHandlerResolver;
    use Codefy\CommandBus\Busses\SynchronousCommandBus;
    
    $resolver = new NativeCommandHandlerResolver();
    $bus = new SynchronousCommandBus(resolver: $resolver);
    $odin = new odin(bus: $bus);
    
    $resolver->bindHandler(commandName: 'CreatePostCommand', handler: 'CreatePostCommandHandler');
    
    $odin->execute(command: new CreatePostCommand);

### Handlers bound by object

Or, just pass your `CommandHandler` instance:

    <?php

    $resolver->bindHandler(commandName: 'CreatePostCommand', handler: new CreatePostCommandHandler);
    
    $odin->execute(command: new CreatePostCommand);

### Handlers as anonymous functions

Sometimes you might want to quickly write a handler for your `Command` without having to write a new class. With Odin 
you can do this by passing an anonymous function as your handler:

    <?php

    $resolver->bindHandler(commandName: 'CreatePostCommand', handler: function (Command $command) {
        /* ... */
    });
    
    $odin->execute(command: new CreatePostCommand);

### Self-handling commands

Alternatively, you may want to simply allow a `Command` object to execute itself. To do this, just ensure your 
`Command` class also implements `CommandHandler`:

    <?php

    class SelfHandlingCommand implements Command, CommandHandler {
        public function handle(Command $command) { /* ... */ }
    }

    $odin->execute(command: new SelfHandlingCommand);

Decorators
----------

Imagine you want to log every command execution. You could do this by adding a call to your logger in every 
`CommandHandler`, however a much more elegant solution is to use decorators.

Registering a decorator:

    <?php

    $odin = new Odin(
        bus: new SynchronousCommandBus(),
        decorators: [new LoggingDecorator(logger: $logger)]
    );

Now, whenever `Odin::execute()` is called, the command will be passed to `LoggingDecorator::execute()`, which will 
perform some logging action, and then pass the command to the relevant `CommandHandler`.

Odin provides two decorators out-the-box:

*   _LoggingDecorator_: Log before and after all executions to a `Psr\Log\LoggerInterface`
*   _EventDispatchingDecorator_: Dispatch an event to a `Codefy\CommandBus\Decorators\EventDispatcher` after every 
command execution.
*   _CommandQueueingDecorator_: Put the command into a Queue for later execution, if it implements 
`Codefy\CommandBus\QueueableCommand`. (Read more under “Queued Commands”)
*   _TransactionalCommandLockingDecorator_: Lock the command bus when a command implementing the 
`Codefy\CommandBus\TransactionalCommand` is being executed. (Read more under “Transactional Commands”)

### Registering multiple decorators:

    <?php

    // Attach decorators when you instantiate
    $odin = new Odin(bus: new SynchronousCommandBus, decorators: [
        new LoggingDecorator(logger: $logger),
        new EventDispatchingDecorator(dispatcher: $eventDispatcher)
    ]);
    
    // Or attach decorators later
    $odin = new Odin();
    $odin->pushDecorator(decorator: new LoggingDecorator(logger: $logger));
    $odin->pushDecorator(decorator: new EventDispatchingDecorator(dispatcher: $eventDispatcher));
    
    // Or manually stack decorators
    $odin = new Odin(
        bus: new EventDispatchingDecorator(dispatcher: $eventDispatcher,
            innerCommandBus: new LoggingDecorator(logger: $logger, context: $context, 
                innerCommandBus: new CommandQueueingDecorator(queuer: $queuer, 
                    innerCommandBus: new TransactionalCommandLockingDecorator(
                        innerCommandBus: new CommandQueueingDecorator(queuer: $queuer, 
                            innerCommandBus: new SynchronousCommandBus()
                        )
                    )
                )
            )
        )
    );

Queued Commands
---------------

Commands are often used for ‘actions’ on your domain (eg. send an email, create a user, log an event, etc). For these 
type of commands where you don’t need an immediate response you may wish to queue them to be executed later. This is 
where the `CommandQueueingDecorator` comes in to play.

Firstly, to use the `CommandQueueingDecorator`, you must first implement the `CommandQueuer` interface with your 
desired queue package:

    <?php

    interface CommandQueuer {
        /**
         * Queue a Command for executing
         *
         * @param Command $command
         */
        public function queue(Command $command);
    }

Next, attach the `CommandQueueingDecorator` decorator:

    <?php

    $odin = new Odin();
    $queuer = CreatePostCommandBusQueuer();
    $odin->pushDecorator(decorator: new CommandQueueingDecorator(queuer: $queuer));

Then, implement `QueueableCommand` in any command which can be queued:

    <?php

    CreatePostCommand implements Codefy\CommandBus\QueueableCommand {}

Then use Odin as normal:

    <?php

    $command = new CreatePostCommand();
    $odin->execute(command: $command);

If you pass Odin any command which implements `QueueableCommand`, it will be added to the queue. Any commands which do 
_not_ implement `QueueableCommand` will be executed immediately as normal.

If your commands implement `QueueableCommand` but you are not using the `CommandQueueingDecorator`, then they will be 
executed immediately as normal. For this reason, it is good practice to implement `QueueableCommand` for any commands 
which may be queued in the future, even if you aren’t using the queueing decorator yet.

Cached Command Execution
------------------------

The `CachingDecorator` can be used to store the execution return value for a given command.

For example, you may have a `FetchUserReportCommand`, and an associated handler which takes a significant time to 
generate the “UserReport”. Rather than re-generating the report every time, simply make `FetchUserReportCommand` 
implement `CacheableCommand`, and the return value will be cached.

Data is cached to a `psr/cache` (PSR-6) compatible cache library.

> Codefy does not supply a cache library or Odin. You must require this yourself and pass it in as a constructor 
> argument to the `CachingDecorator`. However, Odin has been tested with the [qubus/cache](https://github.com/QubusPHP/cache) 
> library which is both PSR-6 and PSR-16 compliant.

    <?php

    use Codefy\CommandBus\CommandBus;
    use Codefy\CommandBus\CacheableCommand;
    use Codefy\CommandBus\Decorators\CachingDecorator;
    
    $odin = new Odin();
    $odin->pushDecorator(
        decorator: new CachingDecorator(
            cache: $cache, // Your library of preference implementing PSR-6 CacheItemPoolInterface.
            expiresAfter: 3600 // Time in seconds that values should be cached for. 3600 = 1 hour.
        )
    );
    
        
    class FetchUserReportCommand implements CacheableCommand { }
    
    class FetchUserReportCommandHandler {
    	public function handle(FetchUserReportCommand $command) {
    		return 'foobar';
    	}
    }
    
    // (string) "foo" handle() is called
    $report = $odin->execute(
        command: new FetchUserReportCommand()
    );
    
    // (string) "foo" Value taken from cache
    $report = $odin->execute(
        command: new FetchUserReportCommand()
    );
    
    // (string) "foo" Value taken from cache
    $report = $odin->execute(
        command: new FetchUserReportCommand()
    );

Transactional Commands
----------------------

Using the `TransactionalCommandLockingDecorator` can help to prevent more than 1 command being executed at any time. 
In practice, this means that you if you nest a command execution inside a command handler, the nested command will not 
be executed until the first command has completed.

Here’s an example:

    <?php

    use Codefy\CommandBus\CommandBus;
    use Codefy\CommandBus\Command;
    use Codefy\CommandBus\Decorators\TransactionalCommandLockingDecorator;
    
    class CreatePostCommandHandler
    {
        public function __construct(public readonly CommandBus $bus)
        {
        }
    
        public function handle(CreatePostCommand $command)
        {
            $this->bus->execute(command: ChangeTitle('this-will-never-be-executed'));
    
            Post::createPostWithoutTap(
                postId: $command->postId,
                title: $command->title,
                content: $command->content
            );
    
            throw new Exception(message: 'Something unexpected; could not create the post.');
        }
    }
    
    $odin = new Odin();
    $odin->pushDecorator(decorator: new TransactionalCommandLockingDecorator());
    
    $createPostCommand = new CreatePostCommand();
    $createPostCommand->postId = new PostId();
    $createPostCommand->title = new Title(value: 'New Post Title');
    $createPostCommand->content = new Content(value: 'Short form content.');
    
    $odin->execute(command: $command);

So what’s happening here? When `$odin->execute(new ChangeTitleCommand('`A New Post Title`'))` is called, that command 
is actually dropped into an in-memory queue, which will not execute until `CreatePostCommandHandler::handle()` has 
finished. In this example, because we’re showing that an `Exception` is thrown before the method completes, the 
`ChangeTitleCommand` command is never actually executed.

Dependency Injection Container Integration
------------------------------------------

Odin uses a `CommandHandlerResolver` class which is responsible for finding and instantiating the relevant 
`CommandHandler` for a given `Command`.

If you want to use your own Dependency Injection Container to control the actual instantiation, just create your own 
class which implements `Codefy\CommandBus\Container` and pass it to the `CommandHandlerResolver` which is consumed by 
`SynchronousCommandBus`.

    <?php

    use Codefy\CommandBus\Resolvers\NativeCommandHandlerResolver;
    use Codefy\CommandBus\Odin;
    use Codefy\CommandBus\Busses\SynchronousCommandBus;
    use Codefy\CommandBus\Container;
    
    class CodefyContainer implements Container {
        public function make($class) {
            return new $class();
        }
    }
    
    $resolver = new NativeCommandHandlerResolver(container: new CodefyContainer);
    $odin = new Odin(bus: new SynchronousCommandBus(resolver: $resolver));
    $odin->execute(command: new CreatePostCommand);

However, if your command has a constructor which requires other instantiation of objects, then the above will not work. 
Odin provides an implementation of `Container` based on [qubus/injector](https://github.com/QubusPHP/injector). The 
easiest way is to use the container factor, and then pass a config into the container:

    <?php

    use Codefy\CommandBus\Busses\SynchronousCommandBus;
    use Codefy\CommandBus\Container;
    use Codefy\CommandBus\Containers\InjectorContainer;
    use Codefy\CommandBus\Odin;
    use Codefy\CommandBus\Resolvers\NativeCommandHandlerResolver;
    use Codefy\Factory\ContainerFactory;
    
    $config [
        'container' => [
            Injector::STANDARD_ALIASES => [
                Container::class => InjectorContainer::class,
            ]
        ]
    ];
    
    $resolver = new NativeCommandHandlerResolver(
        container: ContainerFactory::make(config: $config['container'])
    );
    $odin = new Odin(bus: new SynchronousCommandBus(resolver: $resolver));
    $odin->execute(command: new CreatePostCommand);