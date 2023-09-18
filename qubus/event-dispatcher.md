Many applications develop a system that allows for code behavior change without modifying the core. Many of these 
systems will implement the observer pattern or the mediator pattern.

CodefyPHP’s event dispatcher implements the observer pattern. Create custom events and listeners that allows components 
in your project to react if something occurs.

The event dispatcher contains three elements: the event, the listener, and the dispatcher. The dispatcher class raises 
events that the listeners throughout the system will listen for or subscribe to.

Please note that the [event dispatcher](https://github.com/QubusPHP/event-dispatcher) is different from the 
[Event Bus](https://codefyphp.com/knowledgebase/event-bus/) for domain events.

The following example should help explain in more detail on how to use the event dispatcher. This example shows how to 
use it to send an email after a user registers to a site.

First we need an event class:

    use Qubus\EventDispatcher\GenericEvent;
    
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

Next, you could create a `listener` or `subscriber`. For this example, I am going to use a subscriber. Subscribers 
allow you to group together events rather than just one event via a listener.

    use Qubus\EventDispatcher\Event;
    use Qubus\EventDispatcher\EventSubscriber;
    
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
be called when the event is triggered, also know as the `listener method`.

Now that we have our classes in place, create a file called `subscriber_event.php` and add the following:

    require('vendor/autoload.php');
    
    use Qubus\EventDispatcher\Dispatcher;
    use Qubus\EventDispatcher\Event;
    use Qubus\EventDispatcher\EventSubscriber;
    use Qubus\EventDispatcher\GenericEvent;
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