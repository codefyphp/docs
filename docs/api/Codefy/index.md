
***

# Documentation



This is an automatically generated documentation for **Documentation**.


## Namespaces


### \Codefy\CommandBus

#### Classes

| Class | Description |
|-------|-------------|
| [`InvalidPayloadException`](./CommandBus/InvalidPayloadException.md) | |
| [`Odin`](./CommandBus/Odin.md) | The main Odin class is a CommandBus, which is effectively a decorator<br />around another CommandBus interface.|
| [`PayloadCommand`](./CommandBus/PayloadCommand.md) | |
| [`PropertyCommand`](./CommandBus/PropertyCommand.md) | Abstract class for constructing property mappings.|
| [`UndefinedValueException`](./CommandBus/UndefinedValueException.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`CacheableCommand`](./CommandBus/CacheableCommand.md) | |
| [`Command`](./CommandBus/Command.md) | |
| [`CommandBus`](./CommandBus/CommandBus.md) | |
| [`CommandHandler`](./CommandBus/CommandHandler.md) | |
| [`CommandHandlerResolver`](./CommandBus/CommandHandlerResolver.md) | |
| [`CommandQueuer`](./CommandBus/CommandQueuer.md) | |
| [`Container`](./CommandBus/Container.md) | |
| [`Decorator`](./CommandBus/Decorator.md) | |
| [`HasCacheOptions`](./CommandBus/HasCacheOptions.md) | |
| [`QueueableCommand`](./CommandBus/QueueableCommand.md) | |
| [`TransactionalCommand`](./CommandBus/TransactionalCommand.md) | |



### \Codefy\CommandBus\Busses

#### Classes

| Class | Description |
|-------|-------------|
| [`SynchronousCommandBus`](./CommandBus/Busses/SynchronousCommandBus.md) | |




### \Codefy\CommandBus\Containers

#### Classes

| Class | Description |
|-------|-------------|
| [`ContainerFactory`](./CommandBus/Containers/ContainerFactory.md) | |
| [`InjectorContainer`](./CommandBus/Containers/InjectorContainer.md) | |
| [`NativeContainer`](./CommandBus/Containers/NativeContainer.md) | |
| [`Psr11Container`](./CommandBus/Containers/Psr11Container.md) | |




### \Codefy\CommandBus\Decorators

#### Classes

| Class | Description |
|-------|-------------|
| [`CachingDecorator`](./CommandBus/Decorators/CachingDecorator.md) | |
| [`CommandQueueingDecorator`](./CommandBus/Decorators/CommandQueueingDecorator.md) | Queue commands which implement QueueableCommand into a CommandQueuer.|
| [`EventDispatchingDecorator`](./CommandBus/Decorators/EventDispatchingDecorator.md) | |
| [`LoggingDecorator`](./CommandBus/Decorators/LoggingDecorator.md) | |
| [`TransactionalCommandLockingDecorator`](./CommandBus/Decorators/TransactionalCommandLockingDecorator.md) | TransactionalCommandLockingDecorator treats commands as transactions. Meaning that any<br />subsequent Commands passed to the bus from inside the relevant CommandHandler<br />will not be executed until the initial command is completed.|



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`EventDispatcher`](./CommandBus/Decorators/EventDispatcher.md) | |



### \Codefy\CommandBus\Exceptions

#### Classes

| Class | Description |
|-------|-------------|
| [`CommandCouldNotBeHandledException`](./CommandBus/Exceptions/CommandCouldNotBeHandledException.md) | |
| [`CommandPropertyNotFoundException`](./CommandBus/Exceptions/CommandPropertyNotFoundException.md) | |
| [`OdinException`](./CommandBus/Exceptions/OdinException.md) | |
| [`UnresolvableCommandHandlerException`](./CommandBus/Exceptions/UnresolvableCommandHandlerException.md) | |




### \Codefy\CommandBus\Handlers

#### Classes

| Class | Description |
|-------|-------------|
| [`CallableCommandHandler`](./CommandBus/Handlers/CallableCommandHandler.md) | |
| [`LazyLoadingCommandHandler`](./CommandBus/Handlers/LazyLoadingCommandHandler.md) | |




### \Codefy\CommandBus\Resolvers

#### Classes

| Class | Description |
|-------|-------------|
| [`NativeCommandHandlerResolver`](./CommandBus/Resolvers/NativeCommandHandlerResolver.md) | |




### \Codefy\CommandBus\Traits



#### Traits

| Trait | Description |
|-------|-------------|
| [`InnerBusAware`](./CommandBus/Traits/InnerBusAware.md) | |
| [`PayloadAware`](./CommandBus/Traits/PayloadAware.md) | |




### \Codefy\Domain




#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`IdentityMap`](./Domain/IdentityMap.md) | Holds unique Aggregate instances in memory, mapped by id.|
| [`Metadata`](./Domain/Metadata.md) | |
| [`UnitOfWork`](./Domain/UnitOfWork.md) | A unit of work that acts both as an identity map and a change tracker.|



### \Codefy\Domain\Aggregate

#### Classes

| Class | Description |
|-------|-------------|
| [`AggregateNotFoundException`](./Domain/Aggregate/AggregateNotFoundException.md) | |
| [`AggregateType`](./Domain/Aggregate/AggregateType.md) | |
| [`EventSourcedAggregate`](./Domain/Aggregate/EventSourcedAggregate.md) | |
| [`EventSourcedAggregateRepository`](./Domain/Aggregate/EventSourcedAggregateRepository.md) | |
| [`InvalidAggregateIdGivenException`](./Domain/Aggregate/InvalidAggregateIdGivenException.md) | |
| [`MultipleInstancesOfAggregateDetectedException`](./Domain/Aggregate/MultipleInstancesOfAggregateDetectedException.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`AggregateId`](./Domain/Aggregate/AggregateId.md) | |
| [`AggregateRepository`](./Domain/Aggregate/AggregateRepository.md) | |
| [`AggregateRoot`](./Domain/Aggregate/AggregateRoot.md) | Entities that are an aggregate root.|
| [`AggregateRootFactory`](./Domain/Aggregate/AggregateRootFactory.md) | |
| [`IsEventSourced`](./Domain/Aggregate/IsEventSourced.md) | |
| [`RecordsEvents`](./Domain/Aggregate/RecordsEvents.md) | An object that records the events that happened to it<br />since the last time it was cleared, or since it was<br />restored from persistence.|



### \Codefy\Domain\EventSourcing

#### Classes

| Class | Description |
|-------|-------------|
| [`AggregateChanged`](./Domain/EventSourcing/AggregateChanged.md) | Something that happened in the past and that is of importance to the business.|
| [`BaseProjection`](./Domain/EventSourcing/BaseProjection.md) | |
| [`CorruptEventStreamException`](./Domain/EventSourcing/CorruptEventStreamException.md) | |
| [`DomainEventIsImmutableException`](./Domain/EventSourcing/DomainEventIsImmutableException.md) | |
| [`DomainEvents`](./Domain/EventSourcing/DomainEvents.md) | |
| [`DomainEventsArray`](./Domain/EventSourcing/DomainEventsArray.md) | |
| [`EventId`](./Domain/EventSourcing/EventId.md) | |
| [`EventName`](./Domain/EventSourcing/EventName.md) | |
| [`EventStoreTransaction`](./Domain/EventSourcing/EventStoreTransaction.md) | Code originated at https://github.com/beberlei/litecqrs-php/|
| [`EventStream`](./Domain/EventSourcing/EventStream.md) | |
| [`EventStreamIsEmptyException`](./Domain/EventSourcing/EventStreamIsEmptyException.md) | |
| [`InMemoryEventStore`](./Domain/EventSourcing/InMemoryEventStore.md) | |
| [`TransactionId`](./Domain/EventSourcing/TransactionId.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`DomainEvent`](./Domain/EventSourcing/DomainEvent.md) | Something that happened in the past and that is of importance to the business.|
| [`EventSourcingException`](./Domain/EventSourcing/EventSourcingException.md) | |
| [`EventStore`](./Domain/EventSourcing/EventStore.md) | Event store for publishing a domain event<br />and retrieving an aggregate&#039;s history.|
| [`Projection`](./Domain/EventSourcing/Projection.md) | |
| [`TransactionalEventStore`](./Domain/EventSourcing/TransactionalEventStore.md) | Event store for publishing a domain event<br />and retrieving an aggregate&#039;s history.|



### \Codefy\Domain\Model

#### Classes

| Class | Description |
|-------|-------------|
| [`EntityNotFoundException`](./Domain/Model/EntityNotFoundException.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`Entity`](./Domain/Model/Entity.md) | |
| [`EntityId`](./Domain/Model/EntityId.md) | |
| [`EntityRepository`](./Domain/Model/EntityRepository.md) | |



### \Codefy\EventBus

#### Classes

| Class | Description |
|-------|-------------|
| [`CommandEventBus`](./EventBus/CommandEventBus.md) | |
| [`GenericPublisher`](./EventBus/GenericPublisher.md) | |
| [`NullPublisher`](./EventBus/NullPublisher.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`DomainEventPublisher`](./EventBus/DomainEventPublisher.md) | |
| [`DomainEventSubscriber`](./EventBus/DomainEventSubscriber.md) | |
| [`EventBus`](./EventBus/EventBus.md) | |



### \Codefy\QueryBus

#### Classes

| Class | Description |
|-------|-------------|
| [`Enquire`](./QueryBus/Enquire.md) | |
| [`UnresolvableQueryHandlerException`](./QueryBus/UnresolvableQueryHandlerException.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`Query`](./QueryBus/Query.md) | |
| [`QueryBus`](./QueryBus/QueryBus.md) | |
| [`QueryHandler`](./QueryBus/QueryHandler.md) | |
| [`QueryHandlerResolver`](./QueryBus/QueryHandlerResolver.md) | |



### \Codefy\QueryBus\Busses

#### Classes

| Class | Description |
|-------|-------------|
| [`SynchronousQueryBus`](./QueryBus/Busses/SynchronousQueryBus.md) | |




### \Codefy\QueryBus\Handlers

#### Classes

| Class | Description |
|-------|-------------|
| [`CallableQueryHandler`](./QueryBus/Handlers/CallableQueryHandler.md) | |
| [`LazyLoadingQueryHandler`](./QueryBus/Handlers/LazyLoadingQueryHandler.md) | |




### \Codefy\QueryBus\Resolvers

#### Classes

| Class | Description |
|-------|-------------|
| [`NativeQueryHandlerResolver`](./QueryBus/Resolvers/NativeQueryHandlerResolver.md) | |




### \Codefy\Traits



#### Traits

| Trait | Description |
|-------|-------------|
| [`EventProducerAware`](./Traits/EventProducerAware.md) | |
| [`EventSourcedAware`](./Traits/EventSourcedAware.md) | |
| [`EventSourcedRepositoryAware`](./Traits/EventSourcedRepositoryAware.md) | |
| [`IdentityMapAware`](./Traits/IdentityMapAware.md) | |
| [`PublisherAware`](./Traits/PublisherAware.md) | |
| [`ReplayAware`](./Traits/ReplayAware.md) | |
| [`SubscriberAware`](./Traits/SubscriberAware.md) | |
| [`WhenAware`](./Traits/WhenAware.md) | |




***
> Automatically generated on 2025-10-13
