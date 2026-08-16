
***

# Documentation



This is an automatically generated documentation for **Documentation**.

## Namespaces

### Global \

#### Helpers

| Function                                  | Description |
|-------------------------------------------|-------------|
| [`csrf_field()`](./Helpers/csrf_field.md) |             |

### \Codefy\Framework

#### Classes

| Class                                                      | Description |
|------------------------------------------------------------|-------------|
| [`Application`](./Application.md) |             |

### \Codefy\Framework\Auth

#### Classes

| Class                                                           | Description |
|-----------------------------------------------------------------|-------------|
| [`Auth`](./Auth/Auth.md)               |             |
| [`Gate`](./Auth/Gate.md)               |             |
| [`UserSession`](./Auth/UserSession.md) |             |

#### Interfaces

| Interface                                                 | Description |
|-----------------------------------------------------------|-------------|
| [`Sentinel`](./Auth/Sentinel.md) |             |

### \Codefy\Framework\Auth\Rbac

#### Classes

| Class                                                              | Description |
|--------------------------------------------------------------------|-------------|
| [`Rbac`](./Auth/Rbac/Rbac.md)             |             |
| [`RbacLoader`](./Auth/Rbac/RbacLoader.md) |             |

#### Interfaces

| Interface                                                | Description |
|----------------------------------------------------------|-------------|
| [`Guard`](./Auth/Rbac/Guard.md) |             |

### \Codefy\Framework\Auth\Rbac\Entity

#### Classes

| Class                                                                             | Description |
|-----------------------------------------------------------------------------------|-------------|
| [`RbacPermission`](./Auth/Rbac/Entity/RbacPermission.md) |             |
| [`RbacRole`](./Auth/Rbac/Entity/RbacRole.md)             |             |

#### Interfaces

| Interface                                                                       | Description |
|---------------------------------------------------------------------------------|-------------|
| [`AssertionRule`](./Auth/Rbac/Entity/AssertionRule.md) |             |
| [`Permission`](./Auth/Rbac/Entity/Permission.md)       |             |
| [`Role`](./Auth/Rbac/Entity/Role.md)                   |             |

### \Codefy\Framework\Auth\Rbac\Exception

#### Classes

| Class                                                                                              | Description |
|----------------------------------------------------------------------------------------------------|-------------|
| [`SentinelException`](./Auth/Rbac/Exception/SentinelException.md)         |             |
| [`UnauthorizedException`](./Auth/Rbac/Exception/UnauthorizedException.md) |             |

### \Codefy\Framework\Auth\Rbac\Resource

#### Classes

| Class                                                                                         | Description |
|-----------------------------------------------------------------------------------------------|-------------|
| [`BaseStorageResource`](./Auth/Rbac/Resource/BaseStorageResource.md) |             |
| [`FileResource`](./Auth/Rbac/Resource/FileResource.md)               |             |

#### Interfaces

| Interface                                                                             | Description |
|---------------------------------------------------------------------------------------|-------------|
| [`StorageResource`](./Auth/Rbac/Resource/StorageResource.md) |             |

### \Codefy\Framework\Auth\Repository

#### Classes

| Class                                                                          | Description |
|--------------------------------------------------------------------------------|-------------|
| [`PdoRepository`](./Auth/Repository/PdoRepository.md) |             |

#### Interfaces

| Interface                                                                                | Description |
|------------------------------------------------------------------------------------------|-------------|
| [`AuthUserRepository`](./Auth/Repository/AuthUserRepository.md) |             |

### \Codefy\Framework\Auth\Traits

#### Classes

| Class                                                                                            | Description |
|--------------------------------------------------------------------------------------------------|-------------|
| [`BadPropertyCallException`](./Auth/Traits/BadPropertyCallException.md) |             |

#### Traits

| Trait                                                                        | Description |
|------------------------------------------------------------------------------|-------------|
| [`ImmutableAware`](./Auth/Traits/ImmutableAware.md) |             |

### \Codefy\Framework\Bootstrap

#### Classes

| Class                                                                            | Description |
|----------------------------------------------------------------------------------|-------------|
| [`BootProviders`](./Bootstrap/BootProviders.md)         |             |
| [`RegisterProviders`](./Bootstrap/RegisterProviders.md) |             |

### \Codefy\Framework\Configuration

#### Classes

| Class                                                                                  | Description |
|----------------------------------------------------------------------------------------|-------------|
| [`ApplicationBuilder`](./Configuration/ApplicationBuilder.md) |             |
| [`Middleware`](./Configuration/Middleware.md)                 |             |

### \Codefy\Framework\Console

#### Classes

| Class                                                                            | Description |
|----------------------------------------------------------------------------------|-------------|
| [`ClassGenerator`](./Console/ClassGenerator.md)         |             |
| [`ConsoleApplication`](./Console/ConsoleApplication.md) |             |
| [`ConsoleCommand`](./Console/ConsoleCommand.md)         |             |
| [`ConsoleKernel`](./Console/ConsoleKernel.md)           |             |
| [`PresetRegistry`](./Console/PresetRegistry.md)         |             |

### \Codefy\Framework\Console\Commands

#### Classes

| Class                                                                                                                 | Description |
|-----------------------------------------------------------------------------------------------------------------------|-------------|
| [`DatabaseSeedCommand`](./Console/Commands/DatabaseSeedCommand.md)                           |             |
| [`EncryptEnvCommand`](./Console/Commands/EncryptEnvCommand.md)                               |             |
| [`FlushPipelineCommand`](./Console/Commands/FlushPipelineCommand.md)                         |             |
| [`GenerateEncryptionKeyCommand`](./Console/Commands/GenerateEncryptionKeyCommand.md)         |             |
| [`GenerateEncryptionKeyFileCommand`](./Console/Commands/GenerateEncryptionKeyFileCommand.md) |             |
| [`InitCommand`](./Console/Commands/InitCommand.md)                                           |             |
| [`MakeCommand`](./Console/Commands/MakeCommand.md)                                           |             |
| [`MigrateCheckCommand`](./Console/Commands/MigrateCheckCommand.md)                           |             |
| [`MigrateCommand`](./Console/Commands/MigrateCommand.md)                                     |             |
| [`MigrateDownCommand`](./Console/Commands/MigrateDownCommand.md)                             |             |
| [`MigrateFreshCommand`](./Console/Commands/MigrateFreshCommand.md)                           |             |
| [`MigrateGenerateCommand`](./Console/Commands/MigrateGenerateCommand.md)                     |             |
| [`MigrateRedoCommand`](./Console/Commands/MigrateRedoCommand.md)                             |             |
| [`MigrateRollbackCommand`](./Console/Commands/MigrateRollbackCommand.md)                     |             |
| [`MigrateStatusCommand`](./Console/Commands/MigrateStatusCommand.md)                         |             |
| [`MigrateUpCommand`](./Console/Commands/MigrateUpCommand.md)                                 |             |
| [`PasswordHashCommand`](./Console/Commands/PasswordHashCommand.md)                           |             |
| [`PhpMigCommand`](./Console/Commands/PhpMigCommand.md)                                       |             |
| [`QueueListCommand`](./Console/Commands/QueueListCommand.md)                                 |             |
| [`QueueRunCommand`](./Console/Commands/QueueRunCommand.md)                                   |             |
| [`RouteListCommand`](./Console/Commands/RouteListCommand.md)                                 |             |
| [`ScheduleListCommand`](./Console/Commands/ScheduleListCommand.md)                           |             |
| [`ScheduleRunCommand`](./Console/Commands/ScheduleRunCommand.md)                             |             |
| [`ServeCommand`](./Console/Commands/ServeCommand.md)                                         |             |
| [`VendorPublishCommand`](./Console/Commands/VendorPublishCommand.md)                         |             |

### \Codefy\Framework\Console\Commands\Domain

#### Classes

| Class                                                                                          | Description |
|------------------------------------------------------------------------------------------------|-------------|
| [`GeneratorCommand`](./Console/Commands/Domain/GeneratorCommand.md)   |             |
| [`MakeCommand`](./Console/Commands/Domain/MakeCommand.md)             |             |
| [`MakeDomainCommand`](./Console/Commands/Domain/MakeDomainCommand.md) |             |
| [`UlidCommand`](./Console/Commands/Domain/UlidCommand.md)             |             |
| [`UuidCommand`](./Console/Commands/Domain/UuidCommand.md)             |             |

### \Codefy\Framework\Console\Commands\Traits

#### Traits

| Trait                                                                                        | Description |
|----------------------------------------------------------------------------------------------|-------------|
| [`MakeCommandAware`](./Console/Commands/Traits/MakeCommandAware.md) |             |

### \Codefy\Framework\Console\Exceptions

#### Classes

| Class                                                                                                                             | Description |
|-----------------------------------------------------------------------------------------------------------------------------------|-------------|
| [`MakeCommandFileAlreadyExistsException`](./Console/Exceptions/MakeCommandFileAlreadyExistsException.md) |             |

### \Codefy\Framework\Contracts

#### Interfaces

| Interface                                                                        | Description |
|----------------------------------------------------------------------------------|-------------|
| [`LoggerFactory`](./Contracts/LoggerFactory.md)         |             |
| [`MailerFactory`](./Contracts/MailerFactory.md)         |             |
| [`RoutingController`](./Contracts/RoutingController.md) |             |

### \Codefy\Framework\Contracts\Console

#### Interfaces

| Interface                                                          | Description |
|--------------------------------------------------------------------|-------------|
| [`Kernel`](./Contracts/Console/Kernel.md) |             |

### \Codefy\Framework\Contracts\Http

#### Interfaces

| Interface                                                       | Description |
|-----------------------------------------------------------------|-------------|
| [`Kernel`](./Contracts/Http/Kernel.md) |             |

### \Codefy\Framework\DataCollector

#### Classes

| Class                                                                            | Description |
|----------------------------------------------------------------------------------|-------------|
| [`CodefyCollector`](./DataCollector/CodefyCollector.md) |             |
| [`RouteCollector`](./DataCollector/RouteCollector.md)   |             |

### \Codefy\Framework\Dto

#### Interfaces

| Interface                                                              | Description |
|------------------------------------------------------------------------|-------------|
| [`DataTransformer`](./Dto/DataTransformer.md) |             |
| [`HasDto`](./Dto/HasDto.md)                   |             |

### \Codefy\Framework\Dto\Attribute

#### Classes

| Class                                                          | Description |
|----------------------------------------------------------------|-------------|
| [`UseDto`](./Dto/Attribute/UseDto.md) |             |

### \Codefy\Framework\Dto\Trait

#### Traits

| Trait                                                          | Description |
|----------------------------------------------------------------|-------------|
| [`DtoAware`](./Dto/Trait/DtoAware.md) |             |

### \Codefy\Framework\Factory

#### Classes

| Class                                                                                  | Description |
|----------------------------------------------------------------------------------------|-------------|
| [`FileLoggerFactory`](./Factory/FileLoggerFactory.md)         |             |
| [`FileLoggerSmtpFactory`](./Factory/FileLoggerSmtpFactory.md) |             |
| [`PHPMailerSmtpFactory`](./Factory/PHPMailerSmtpFactory.md)   |             |

### \Codefy\Framework\Factory\Traits

#### Traits

| Trait                                                                             | Description |
|-----------------------------------------------------------------------------------|-------------|
| [`FileLoggerAware`](./Factory/Traits/FileLoggerAware.md) |             |

### \Codefy\Framework\Http

#### Classes

| Class                                                                 | Description |
|-----------------------------------------------------------------------|-------------|
| [`BaseController`](./Http/BaseController.md) |             |
| [`HttpClient`](./Http/HttpClient.md)         |             |
| [`Kernel`](./Http/Kernel.md)                 |             |
| [`RequestContext`](./Http/RequestContext.md) |             |

### \Codefy\Framework\Http\Errors

#### Classes

| Class                                                                            | Description |
|----------------------------------------------------------------------------------|-------------|
| [`HttpRequestError`](./Http/Errors/HttpRequestError.md) |             |

### \Codefy\Framework\Http\Middleware

#### Classes

| Class                                                                                            | Description |
|--------------------------------------------------------------------------------------------------|-------------|
| [`ApiMiddleware`](./Http/Middleware/ApiMiddleware.md)                   |             |
| [`BindRequestMiddleware`](./Http/Middleware/BindRequestMiddleware.md)   |             |
| [`ContentCacheMiddleware`](./Http/Middleware/ContentCacheMiddleware.md) |             |
| [`CorsMiddleware`](./Http/Middleware/CorsMiddleware.md)                 |             |
| [`CssMinifierMiddleware`](./Http/Middleware/CssMinifierMiddleware.md)   |             |
| [`DebugBarMiddleware`](./Http/Middleware/DebugBarMiddleware.md)         |             |
| [`HtmlMinifierMiddleware`](./Http/Middleware/HtmlMinifierMiddleware.md) |             |
| [`JsMinifierMiddleware`](./Http/Middleware/JsMinifierMiddleware.md)     |             |
| [`ThrottleMiddleware`](./Http/Middleware/ThrottleMiddleware.md)         |             |

### \Codefy\Framework\Http\Middleware\Auth

#### Classes

| Class                                                                                                           | Description |
|-----------------------------------------------------------------------------------------------------------------|-------------|
| [`AuthenticationMiddleware`](./Http/Middleware/Auth/AuthenticationMiddleware.md)       |             |
| [`ExpireUserSessionMiddleware`](./Http/Middleware/Auth/ExpireUserSessionMiddleware.md) |             |
| [`GateMiddleware`](./Http/Middleware/Auth/GateMiddleware.md)                           |             |
| [`UserAuthorizationMiddleware`](./Http/Middleware/Auth/UserAuthorizationMiddleware.md) |             |
| [`UserCookieDecryptMiddleware`](./Http/Middleware/Auth/UserCookieDecryptMiddleware.md) |             |
| [`UserSessionMiddleware`](./Http/Middleware/Auth/UserSessionMiddleware.md)             |             |

### \Codefy\Framework\Http\Middleware\Cache

#### Classes

| Class                                                                                                        | Description |
|--------------------------------------------------------------------------------------------------------------|-------------|
| [`CacheExpiresMiddleware`](./Http/Middleware/Cache/CacheExpiresMiddleware.md)       |             |
| [`CacheMiddleware`](./Http/Middleware/Cache/CacheMiddleware.md)                     |             |
| [`CachePreventionMiddleware`](./Http/Middleware/Cache/CachePreventionMiddleware.md) |             |
| [`ClearSiteDataMiddleware`](./Http/Middleware/Cache/ClearSiteDataMiddleware.md)     |             |

### \Codefy\Framework\Http\Middleware\Csrf

#### Classes

| Class                                                                                                     | Description |
|-----------------------------------------------------------------------------------------------------------|-------------|
| [`CsrfProtectionMiddleware`](./Http/Middleware/Csrf/CsrfProtectionMiddleware.md) |             |
| [`CsrfSession`](./Http/Middleware/Csrf/CsrfSession.md)                           |             |
| [`CsrfTokenMiddleware`](./Http/Middleware/Csrf/CsrfTokenMiddleware.md)           |             |
| [`InvalidTokenException`](./Http/Middleware/Csrf/InvalidTokenException.md)       |             |
| [`TokenMismatchException`](./Http/Middleware/Csrf/TokenMismatchException.md)     |             |

### \Codefy\Framework\Http\Middleware\Csrf\Traits

#### Traits

| Trait                                                                                        | Description |
|----------------------------------------------------------------------------------------------|-------------|
| [`CsrfTokenAware`](./Http/Middleware/Csrf/Traits/CsrfTokenAware.md) |             |

### \Codefy\Framework\Http\Middleware\Exception

#### Classes

| Class                                                                                                                              | Description |
|------------------------------------------------------------------------------------------------------------------------------------|-------------|
| [`ExceptionHandler`](./Http/Middleware/Exception/ExceptionHandler.md)                                     |             |
| [`HtmlHttpExceptionMiddleware`](./Http/Middleware/Exception/HtmlHttpExceptionMiddleware.md)               |             |
| [`HttpExceptionMiddleware`](./Http/Middleware/Exception/HttpExceptionMiddleware.md)                       |             |
| [`JsonHttpExceptionMiddleware`](./Http/Middleware/Exception/JsonHttpExceptionMiddleware.md)               |             |
| [`RedirectionHttpExceptionMiddleware`](./Http/Middleware/Exception/RedirectionHttpExceptionMiddleware.md) |             |
| [`StrategyHttpExceptionMiddleware`](./Http/Middleware/Exception/StrategyHttpExceptionMiddleware.md)       |             |

### \Codefy\Framework\Http\Middleware\Exception\Strategy

#### Classes

| Class                                                                                                                           | Description |
|---------------------------------------------------------------------------------------------------------------------------------|-------------|
| [`HtmlHttpResponseStrategy`](./Http/Middleware/Exception/Strategy/HtmlHttpResponseStrategy.md)         |             |
| [`JsonHttpResponseStrategy`](./Http/Middleware/Exception/Strategy/JsonHttpResponseStrategy.md)         |             |
| [`RedirectHttpResponseStrategy`](./Http/Middleware/Exception/Strategy/RedirectHttpResponseStrategy.md) |             |

#### Interfaces

| Interface                                                                                                       | Description |
|-----------------------------------------------------------------------------------------------------------------|-------------|
| [`HttpResponseStrategy`](./Http/Middleware/Exception/Strategy/HttpResponseStrategy.md) |             |

### \Codefy\Framework\Http\Middleware\Exception\Trait

#### Traits

| Trait                                                                                                                  | Description |
|------------------------------------------------------------------------------------------------------------------------|-------------|
| [`HttpExceptionHandlerAware`](./Http/Middleware/Exception/Trait/HttpExceptionHandlerAware.md) |             |
| [`HttpExceptionRenderAware`](./Http/Middleware/Exception/Trait/HttpExceptionRenderAware.md)   |             |
| [`HttpExceptionUtilityAware`](./Http/Middleware/Exception/Trait/HttpExceptionUtilityAware.md) |             |

### \Codefy\Framework\Http\Middleware\Request

#### Classes

| Class                                                                                                          | Description |
|----------------------------------------------------------------------------------------------------------------|-------------|
| [`FormRequest`](./Http/Middleware/Request/FormRequest.md)                             |             |
| [`FormRequestErrorResponder`](./Http/Middleware/Request/FormRequestErrorResponder.md) |             |
| [`FormRequestHandler`](./Http/Middleware/Request/FormRequestHandler.md)               |             |

#### Interfaces

| Interface                                                                                              | Description |
|--------------------------------------------------------------------------------------------------------|-------------|
| [`FormRequestMiddleware`](./Http/Middleware/Request/FormRequestMiddleware.md) |             |

### \Codefy\Framework\Http\Middleware\SecureHeaders

#### Classes

| Class                                                                                                                            | Description |
|----------------------------------------------------------------------------------------------------------------------------------|-------------|
| [`ContentSecurityPolicyMiddleware`](./Http/Middleware/SecureHeaders/ContentSecurityPolicyMiddleware.md) |             |
| [`SecureHeaders`](./Http/Middleware/SecureHeaders/SecureHeaders.md)                                     |             |

### \Codefy\Framework\Http\Middleware\Spam

#### Classes

| Class                                                                                                 | Description |
|-------------------------------------------------------------------------------------------------------|-------------|
| [`HoneyPotMiddleware`](./Http/Middleware/Spam/HoneyPotMiddleware.md)         |             |
| [`ReferrerSpamMiddleware`](./Http/Middleware/Spam/ReferrerSpamMiddleware.md) |             |

### \Codefy\Framework\Http\Request

#### Classes

| Class                                                                           | Description |
|---------------------------------------------------------------------------------|-------------|
| [`FormDataRequest`](./Http/Request/FormDataRequest.md) |             |
| [`FormRequest`](./Http/Request/FormRequest.md)         |             |

### \Codefy\Framework\Http\Swoole

#### Classes

| Class                                                                      | Description |
|----------------------------------------------------------------------------|-------------|
| [`App`](./Http/Swoole/App.md)                     |             |
| [`BridgeManager`](./Http/Swoole/BridgeManager.md) |             |

### \Codefy\Framework\Http\Throttle

#### Classes

| Class                                                                        | Description |
|------------------------------------------------------------------------------|-------------|
| [`Condition`](./Http/Throttle/Condition.md)         |             |
| [`Interval`](./Http/Throttle/Interval.md)           |             |
| [`RateException`](./Http/Throttle/RateException.md) |             |
| [`RateLimiter`](./Http/Throttle/RateLimiter.md)     |             |

### \Codefy\Framework\Pipeline

#### Classes

| Class                                                                       | Description |
|-----------------------------------------------------------------------------|-------------|
| [`Pipeline`](./Pipeline/Pipeline.md)               |             |
| [`PipelineBuilder`](./Pipeline/PipelineBuilder.md) |             |
| [`PipelineFactory`](./Pipeline/PipelineFactory.md) |             |

#### Traits

| Trait                                                           | Description |
|-----------------------------------------------------------------|-------------|
| [`PipeAware`](./Pipeline/PipeAware.md) |             |

#### Interfaces

| Interface                                                       | Description |
|-----------------------------------------------------------------|-------------|
| [`Chainable`](./Pipeline/Chainable.md) |             |

### \Codefy\Framework\Providers

#### Classes

| Class                                                                                                            | Description |
|------------------------------------------------------------------------------------------------------------------|-------------|
| [`AssetsServiceProvider`](./Providers/AssetsServiceProvider.md)                         |             |
| [`ConfigServiceProvider`](./Providers/ConfigServiceProvider.md)                         |             |
| [`DatabaseConnectionServiceProvider`](./Providers/DatabaseConnectionServiceProvider.md) |             |
| [`EventDispatcherServiceProvider`](./Providers/EventDispatcherServiceProvider.md)       |             |
| [`FlysystemServiceProvider`](./Providers/FlysystemServiceProvider.md)                   |             |
| [`HttpExceptionServiceProvider`](./Providers/HttpExceptionServiceProvider.md)           |             |
| [`LocalizationServiceProvider`](./Providers/LocalizationServiceProvider.md)             |             |
| [`PdoServiceProvider`](./Providers/PdoServiceProvider.md)                               |             |
| [`QueryBuilderServiceProvider`](./Providers/QueryBuilderServiceProvider.md)             |             |
| [`RouterServiceProvider`](./Providers/RouterServiceProvider.md)                         |             |
| [`RoutingServiceProvider`](./Providers/RoutingServiceProvider.md)                       |             |

### \Codefy\Framework\Proxy

#### Classes

| Class                                                  | Description |
|--------------------------------------------------------|-------------|
| [`Codefy`](./Proxy/Codefy.md) |             |

### \Codefy\Framework\Queue

#### Classes

| Class                                                            | Description |
|------------------------------------------------------------------|-------------|
| [`NodeQueue`](./Queue/NodeQueue.md)     |             |
| [`SimpleQueue`](./Queue/SimpleQueue.md) |             |

#### Interfaces

| Interface                                                                              | Description                         |
|----------------------------------------------------------------------------------------|-------------------------------------|
| [`Queue`](./Queue/Queue.md)                                   | Interface for a queue.              |
| [`QueueGarbageCollection`](./Queue/QueueGarbageCollection.md) | Interface for a garbage collection. |
| [`ReliableQueue`](./Queue/ReliableQueue.md)                   | Reliable queue interface.           |
| [`ShouldQueue`](./Queue/ShouldQueue.md)                       |                                     |

### \Codefy\Framework\Queue\Traits

#### Traits

| Trait                                                                 | Description |
|-----------------------------------------------------------------------|-------------|
| [`QueueAware`](./Queue/Traits/QueueAware.md) |             |

### \Codefy\Framework\Scheduler

#### Classes

| Class                                                                        | Description |
|------------------------------------------------------------------------------|-------------|
| [`BaseTask`](./Scheduler/BaseTask.md)               |             |
| [`FailedProcessor`](./Scheduler/FailedProcessor.md) |             |
| [`Schedule`](./Scheduler/Schedule.md)               |             |

#### Interfaces

| Interface                                              | Description |
|--------------------------------------------------------|-------------|
| [`Task`](./Scheduler/Task.md) |             |

### \Codefy\Framework\Scheduler\Event

#### Classes

| Class                                                                          | Description |
|--------------------------------------------------------------------------------|-------------|
| [`TaskCompleted`](./Scheduler/Event/TaskCompleted.md) |             |
| [`TaskFailed`](./Scheduler/Event/TaskFailed.md)       |             |
| [`TaskSkipped`](./Scheduler/Event/TaskSkipped.md)     |             |
| [`TaskStarted`](./Scheduler/Event/TaskStarted.md)     |             |

### \Codefy\Framework\Scheduler\Expressions

#### Classes

| Class                                                                            | Description |
|----------------------------------------------------------------------------------|-------------|
| [`At`](./Scheduler/Expressions/At.md)                   |             |
| [`Daily`](./Scheduler/Expressions/Daily.md)             |             |
| [`Date`](./Scheduler/Expressions/Date.md)               |             |
| [`EveryMinute`](./Scheduler/Expressions/EveryMinute.md) |             |
| [`Hourly`](./Scheduler/Expressions/Hourly.md)           |             |
| [`Monthly`](./Scheduler/Expressions/Monthly.md)         |             |
| [`Quarterly`](./Scheduler/Expressions/Quarterly.md)     |             |
| [`WeekDays`](./Scheduler/Expressions/WeekDays.md)       |             |
| [`WeekEnds`](./Scheduler/Expressions/WeekEnds.md)       |             |
| [`Weekly`](./Scheduler/Expressions/Weekly.md)           |             |

#### Interfaces

| Interface                                                                          | Description |
|------------------------------------------------------------------------------------|-------------|
| [`Expressional`](./Scheduler/Expressions/Expressional.md) |             |

### \Codefy\Framework\Scheduler\Expressions\DayOfWeek

#### Classes

| Class                                                                                  | Description |
|----------------------------------------------------------------------------------------|-------------|
| [`Friday`](./Scheduler/Expressions/DayOfWeek/Friday.md)       |             |
| [`Monday`](./Scheduler/Expressions/DayOfWeek/Monday.md)       |             |
| [`Saturday`](./Scheduler/Expressions/DayOfWeek/Saturday.md)   |             |
| [`Sunday`](./Scheduler/Expressions/DayOfWeek/Sunday.md)       |             |
| [`Thursday`](./Scheduler/Expressions/DayOfWeek/Thursday.md)   |             |
| [`Tuesday`](./Scheduler/Expressions/DayOfWeek/Tuesday.md)     |             |
| [`Wednesday`](./Scheduler/Expressions/DayOfWeek/Wednesday.md) |             |

### \Codefy\Framework\Scheduler\Expressions\MonthOfYear

#### Classes

| Class                                                                                    | Description |
|------------------------------------------------------------------------------------------|-------------|
| [`April`](./Scheduler/Expressions/MonthOfYear/April.md)         |             |
| [`August`](./Scheduler/Expressions/MonthOfYear/August.md)       |             |
| [`December`](./Scheduler/Expressions/MonthOfYear/December.md)   |             |
| [`February`](./Scheduler/Expressions/MonthOfYear/February.md)   |             |
| [`January`](./Scheduler/Expressions/MonthOfYear/January.md)     |             |
| [`July`](./Scheduler/Expressions/MonthOfYear/July.md)           |             |
| [`June`](./Scheduler/Expressions/MonthOfYear/June.md)           |             |
| [`March`](./Scheduler/Expressions/MonthOfYear/March.md)         |             |
| [`May`](./Scheduler/Expressions/MonthOfYear/May.md)             |             |
| [`November`](./Scheduler/Expressions/MonthOfYear/November.md)   |             |
| [`October`](./Scheduler/Expressions/MonthOfYear/October.md)     |             |
| [`September`](./Scheduler/Expressions/MonthOfYear/September.md) |             |

### \Codefy\Framework\Scheduler\Mutex

#### Classes

| Class                                                                      | Description |
|----------------------------------------------------------------------------|-------------|
| [`CacheLocker`](./Scheduler/Mutex/CacheLocker.md) |             |

#### Interfaces

| Interface                                                        | Description |
|------------------------------------------------------------------|-------------|
| [`Locker`](./Scheduler/Mutex/Locker.md) |             |

### \Codefy\Framework\Scheduler\Processor

#### Classes

| Class                                                                              | Description |
|------------------------------------------------------------------------------------|-------------|
| [`BaseProcessor`](./Scheduler/Processor/BaseProcessor.md) |             |
| [`Callback`](./Scheduler/Processor/Callback.md)           |             |
| [`Dispatcher`](./Scheduler/Processor/Dispatcher.md)       |             |
| [`Shell`](./Scheduler/Processor/Shell.md)                 |             |

#### Interfaces

| Interface                                                                  | Description |
|----------------------------------------------------------------------------|-------------|
| [`Processor`](./Scheduler/Processor/Processor.md) |             |

### \Codefy\Framework\Scheduler\Traits

#### Traits

| Trait                                                                                           | Description |
|-------------------------------------------------------------------------------------------------|-------------|
| [`ExpressionAware`](./Scheduler/Traits/ExpressionAware.md)             |             |
| [`LiteralAware`](./Scheduler/Traits/LiteralAware.md)                   |             |
| [`MailerAware`](./Scheduler/Traits/MailerAware.md)                     |             |
| [`ScheduleValidateAware`](./Scheduler/Traits/ScheduleValidateAware.md) |             |

### \Codefy\Framework\Scheduler\ValueObject

#### Classes

| Class                                                                  | Description |
|------------------------------------------------------------------------|-------------|
| [`TaskId`](./Scheduler/ValueObject/TaskId.md) |             |

### \Codefy\Framework\Support

#### Classes

| Class                                                                                  | Description |
|----------------------------------------------------------------------------------------|-------------|
| [`ArgsParser`](./Support/ArgsParser.md)                       |             |
| [`Assets`](./Support/Assets.md)                               |             |
| [`AutoloadResolver`](./Support/AutoloadResolver.md)           |             |
| [`BasePathDetector`](./Support/BasePathDetector.md)           |             |
| [`CodefyMailer`](./Support/CodefyMailer.md)                   |             |
| [`CodefyServiceProvider`](./Support/CodefyServiceProvider.md) |             |
| [`DefaultCommands`](./Support/DefaultCommands.md)             |             |
| [`DefaultMiddlewares`](./Support/DefaultMiddlewares.md)       |             |
| [`DefaultProviders`](./Support/DefaultProviders.md)           |             |
| [`LocalStorage`](./Support/LocalStorage.md)                   |             |
| [`Password`](./Support/Password.md)                           |             |
| [`Paths`](./Support/Paths.md)                                 |             |
| [`RequestMethod`](./Support/RequestMethod.md)                 |             |
| [`SeoFactory`](./Support/SeoFactory.md)                       |             |
| [`Server`](./Support/Server.md)                               |             |
| [`StringParser`](./Support/StringParser.md)                   |             |

### \Codefy\Framework\Support\Traits

#### Traits

| Trait                                                                                       | Description |
|---------------------------------------------------------------------------------------------|-------------|
| [`CollectionStackAware`](./Support/Traits/CollectionStackAware.md) |             |
| [`ContainerAware`](./Support/Traits/ContainerAware.md)             |             |
| [`DbTransactionsAware`](./Support/Traits/DbTransactionsAware.md)   |             |

### \Codefy\Framework\Traits

#### Traits

| Trait                                                                                     | Description |
|-------------------------------------------------------------------------------------------|-------------|
| [`InputValidationAware`](./Traits/InputValidationAware.md)       |             |
| [`LoggerAware`](./Traits/LoggerAware.md)                         |             |
| [`ThrowableTransformAware`](./Traits/ThrowableTransformAware.md) |             |
| [`TokenEncryptionAware`](./Traits/TokenEncryptionAware.md)       |             |

### \Codefy\Framework\Validation

#### Classes

| Class                                                                               | Description |
|-------------------------------------------------------------------------------------|-------------|
| [`HttpInputValidator`](./Validation/HttpInputValidator.md) |             |

#### Interfaces

| Interface                                                                 | Description |
|---------------------------------------------------------------------------|-------------|
| [`DataValidator`](./Validation/DataValidator.md) |             |

### \Codefy\Framework\View

#### Classes

| Class                                                                       | Description |
|-----------------------------------------------------------------------------|-------------|
| [`ErrorViewRenderer`](./View/ErrorViewRenderer.md) |             |
| [`FenomView`](./View/FenomView.md)                 |             |
| [`FoilView`](./View/FoilView.md)                   |             |

#### Interfaces

| Interface                                                                 | Description |
|---------------------------------------------------------------------------|-------------|
| [`TemplateRenderer`](./View/TemplateRenderer.md) |             |
