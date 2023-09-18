CodefyPHP has three service busses: Command, Event, and Query. Busses exchange messages between components. The messages 
are Data Transfer Objects (DTO’s) that contain information to be acted on.

Command Bus
-----------

The command bus signals an intent: `CreatePostCommand`. A command is passed to the command bus which will in turn pass 
it to the corresponding command handler. The command handler will perform the needed operation to – for example – create 
a post. The command should not return data, and there should be one command to one command handler.

Event Bus
---------

The event bus signals what has happened: `PostWasCreated`. You must adopt the naming convention of what has happened 
versus what is meant to happen. The event should not return data, should only hold primitives (strings, integers, 
booleans) not classes, and can be handled by any number of handlers.

Query Bus
---------

The query bus signals a question and is not the same as a database query: `LatestPostsQuery`. The query returns data, 
should only have one query to one query handler, and it should not change the application’s state.

Validation
----------

Service bus messages should always be valid. The best and recommended approach is to validate input before it gets to 
the dispatcher because only valid messages should be dispatched. However there is always an exception to the rule. For 
example, a CreatePostCommand might require a valid author or administrator. The command should validate that either the 
uuid or username is valid, but whether the uuid/username exists, is connected to someone with the proper permissions to 
create a post should only be validated by the handler.

In the next section, you will learning how to create and use commands and command handlers.