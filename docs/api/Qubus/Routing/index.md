
***

# Documentation



This is an automatically generated documentation for **Documentation**.


## Namespaces


### \Qubus\Routing

#### Classes

| Class | Description |
|-------|-------------|
| [`Formatting`](./Formatting.md) | |
| [`Invoker`](./Invoker.md) | |
| [`Router`](./Router.md) | |
| [`TypeHintRequestResolver`](./TypeHintRequestResolver.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`Psr7Router`](./Psr7Router.md) | |



### \Qubus\Routing\Controller

#### Classes

| Class | Description |
|-------|-------------|
| [`Controller`](./Controller/Controller.md) | |
| [`ControllerMiddlewareOptions`](./Controller/ControllerMiddlewareOptions.md) | |
| [`ControllerMiddlewarePipe`](./Controller/ControllerMiddlewarePipe.md) | |


#### Traits

| Trait | Description |
|-------|-------------|
| [`WithMiddlewaresAware`](./Controller/WithMiddlewaresAware.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`ControllerMiddlewareDelegate`](./Controller/ControllerMiddlewareDelegate.md) | |



### \Qubus\Routing\Events

#### Classes

| Class | Description |
|-------|-------------|
| [`RoutingEventArgument`](./Events/RoutingEventArgument.md) | |
| [`RoutingEventHandler`](./Events/RoutingEventHandler.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`EventHandler`](./Events/EventHandler.md) | |



### \Qubus\Routing\Exceptions

#### Classes

| Class | Description |
|-------|-------------|
| [`CrudRouteException`](./Exceptions/CrudRouteException.md) | |
| [`HttpException`](./Exceptions/HttpException.md) | |
| [`NamedRouteNotFoundException`](./Exceptions/NamedRouteNotFoundException.md) | |
| [`NotFoundHttpException`](./Exceptions/NotFoundHttpException.md) | |
| [`RouteControllerNotFoundException`](./Exceptions/RouteControllerNotFoundException.md) | |
| [`RouteMethodNotFoundException`](./Exceptions/RouteMethodNotFoundException.md) | |
| [`RouteNameRedefinedException`](./Exceptions/RouteNameRedefinedException.md) | |
| [`RouteParamFailedConstraintException`](./Exceptions/RouteParamFailedConstraintException.md) | |
| [`RouteParseException`](./Exceptions/RouteParseException.md) | |
| [`TooLateToAddNewRouteException`](./Exceptions/TooLateToAddNewRouteException.md) | |




### \Qubus\Routing\Factories

#### Classes

| Class | Description |
|-------|-------------|
| [`ResponseFactory`](./Factories/ResponseFactory.md) | |
| [`RouteFactory`](./Factories/RouteFactory.md) | |
| [`RouterFactory`](./Factories/RouterFactory.md) | |



#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`ResponsableFactory`](./Factories/ResponsableFactory.md) | |
| [`RoutableFactory`](./Factories/RoutableFactory.md) | |
| [`RouterableFactory`](./Factories/RouterableFactory.md) | |



### \Qubus\Routing\Handlers

#### Classes

| Class | Description |
|-------|-------------|
| [`CallableRequestHandler`](./Handlers/CallableRequestHandler.md) | |
| [`QueueableRequestHandler`](./Handlers/QueueableRequestHandler.md) | |




### \Qubus\Routing\Interfaces




#### Interfaces

| Interface | Description |
|-----------|-------------|
| [`ApiResourceController`](./Interfaces/ApiResourceController.md) | |
| [`BootManager`](./Interfaces/BootManager.md) | |
| [`ExceptionHandler`](./Interfaces/ExceptionHandler.md) | |
| [`Mappable`](./Interfaces/Mappable.md) | |
| [`MiddlewareResolver`](./Interfaces/MiddlewareResolver.md) | |
| [`ResourceController`](./Interfaces/ResourceController.md) | |
| [`Responsable`](./Interfaces/Responsable.md) | |



### \Qubus\Routing\Route

#### Classes

| Class | Description |
|-------|-------------|
| [`InjectorMiddlewareResolver`](./Route/InjectorMiddlewareResolver.md) | |
| [`Route`](./Route/Route.md) | |
| [`RouteAction`](./Route/RouteAction.md) | |
| [`RouteCollector`](./Route/RouteCollector.md) | |
| [`RouteFileRegistrar`](./Route/RouteFileRegistrar.md) | |
| [`RouteGroup`](./Route/RouteGroup.md) | |
| [`RouteParams`](./Route/RouteParams.md) | |
| [`RouteResource`](./Route/RouteResource.md) | |
| [`RoutingRegistrar`](./Route/RoutingRegistrar.md) | |




### \Qubus\Routing\Traits



#### Traits

| Trait | Description |
|-------|-------------|
| [`RouteMapperAware`](./Traits/RouteMapperAware.md) | |




***
> Automatically generated on 2025-10-13
