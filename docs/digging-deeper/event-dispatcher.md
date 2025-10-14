---
title: Events
sidebar_title: Events
order: 22
---

## Installation

```shell
composer require qubus/event-dispatcher
```

## Legacy Event Dispatcher

Many applications develop a system that allows for code behavior change without modifying the core. Many of these 
systems will implement the observer pattern or the mediator pattern.

CodefyPHP’s legacy event dispatcher implements the observer pattern. Create custom events and listeners that allows components 
in your project to react if something occurs.

The event dispatcher contains three elements: the event, the listener, and the dispatcher. The dispatcher class raises 
events that the listeners throughout the system will listen for or subscribe to.

Please note that the [event dispatcher](https://github.com/QubusPHP/event-dispatcher) is different from the 
[Event Bus](domain-driven-design/busses/event-bus.md) for domain events.

The following example should help explain in more detail on how to use the event dispatcher. This example shows how to 
use it to send an email after a user registers to a site.

### Event Class

First we need an event class:

    <?php

    use Qubus\EventDispatcher\Legacy\GenericEvent;
    
    final class MessageSent extends GenericEvent
    {
        public const EVENT_NAME = self::class;
    
        public function getName(): string
        {
            return self::EVENT_NAME;
        }
        public function message(): string
        {
            return 'Congrats! Your account was created successfully.';
        }
    }

### Listener or Subscriber

Next, you could create a `listener` or `subscriber`. For this example, I am going to use a subscriber. Subscribers 
allow you to group together events rather than just one event via a listener.

    <?php

    use Qubus\EventDispatcher\Legacy\Event;
    use Qubus\EventDispatcher\Legacy\EventSubscriber;
    
    final class MessageSentSubscriber implements EventSubscriber
    {
    
        public static function getSubscribedEvents(): array
        {
            return [
                MessageSent::class => 'onMessageSent',
            ];
        }
    
        public function onMessageSent(Event $event)
        {
            echo $event->message();
        }
    }

The `MessageSentSubscriber` class implements the `EventSubscriber` interface which needs to implement the 
`getSubscribedEvents` method. The getSubscribedEvents array should return an array of events you want it to be 
subscribed to. For the array, the key is the event name (`MessageSent::class`) and the value is the method that should 
be called when the event is triggered, also known as the `listener method`.

Now that we have our classes in place, create a file called `subscriber_event.php` and add the following:

    <?php

    require('vendor/autoload.php');
    
    use Qubus\EventDispatcher\Legacy\Dispatcher;
    use Qubus\EventDispatcher\Legacy\Event;
    use Qubus\EventDispatcher\Legacy\EventSubscriber;
    use Qubus\EventDispatcher\Legacy\GenericEvent;
    use Qubus\Exception\Data\TypeException;
    
    // init the event dispatcher
    $dispatcher = new Dispatcher();
    
    // register the subscriber
    $subscriber = new MessageSentSubscriber();
    try {
        $dispatcher->addSubscriber($subscriber);
    } catch (TypeException $e) {
        return $e->getMessage();
    }
    
    // dispatch
    $dispatcher->dispatch(MessageSent::class, new MessageSent());

When you type out the following command `php subscriber_event.php` via a terminal and hit return, you should see your 
message: Congrats! Your account was created successfully.

Working with an event dispatcher might not seem as simple as a hook/plugin system like you find in a CMS like WordPress, 
but once you get the hang of it, you will see that it is pretty powerful.

## PSR-14 Event Dispatcher

Codefy also includes a PSR-14 event dispatcher implementation.

`Qubus\EventDispatcher\EventDispatcher` provides a [`Psr\EventDispatcher\EventDispatcherInterface`](https://github.com/php-fig/event-dispatcher/blob/master/src/EventDispatcherInterface.php) implementation. 
It accepts a [`Psr\EventDispatcher\ListenerProviderInterface`](https://github.com/php-fig/event-dispatcher/blob/master/src/ListenerProviderInterface.php) 
to its constructor, and, when dispatching events, queries the provider for listeners to notify.

### Example

At its most basic, usage looks like this:

    <?php
    
    use Qubus\EventDispatcher\EventDispatcher;
    use Qubus\EventDispatcher\Providers\SimpleProvider;
    
    $provider = new SimpleProvider();
    $provider->listen(SomeEvent::class, function (SomeEvent $event) : void {
        // do something with the event
    });
    
    $dispatcher = new EventDispatcher($provider);
    
    $dispatcher->dispatch(new SomeEvent());

