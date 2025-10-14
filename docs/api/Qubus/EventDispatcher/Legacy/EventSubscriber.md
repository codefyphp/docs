***

# EventSubscriber





* Full name: `\Qubus\EventDispatcher\Legacy\EventSubscriber`



## Methods


### getSubscribedEvents

Returns an array of event names this subscriber wants to listen to.

```php
public static getSubscribedEvents(): array
```

The array key is the name of the hook. The value can be:

 * The method name. Priority defaults to 0.
 * An array with the method name and priority.
 * An array or arrays with method name and/or priority.

For example:

 * ['eventName' => 'methodName']
 * ['eventName' => ['methodName', $priority]]
 * ['eventName' => [['methodName1', $priority], ['methodName2']]]

* This method is **static**.





**Return Value:**

The event names to listen to.




***


***
> Automatically generated on 2025-10-13
