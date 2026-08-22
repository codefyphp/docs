---
title: Dependency Injection
sidebar_title: Dependency Injection
summary: Configure Qubus Injector for PHP autowiring, interface mappings, constructor arguments, factories, shared services, lazy proxies, invocation, and PSR-11.
keywords: php-dependency-injection,autowiring,psr-11
weight: 5
---

## Installation

```shell
composer require qubus/injector
```

## Introduction

Qubus Injector is a standalone dependency-injection container for PHP. It can:

- recursively autowire concrete classes from constructor type declarations;
- map interfaces and abstract classes to implementations;
- define constructor arguments, shared instances, factories, lazy proxies, and post-construction preparations;
- resolve and invoke functions, methods, closures, and invokable objects;
- load mappings from a configuration object; and
- operate as a PSR-11 container through its dedicated adapter.

The package does not bootstrap an application or discover and run service
providers. Frameworks may build those policies on top of the contracts included
in this package.

## Requirements and installation

The current release requires PHP 8.4 or later.

```shell
composer require qubus/injector
```

Create an injector with an `InjectorConfig`. `InjectorFactory` is the
convenient way to construct one:

```php
<?php

declare(strict_types=1);

use Qubus\Injector\Config\InjectorFactory;
use Qubus\Injector\Injector;

$injector = new Injector(InjectorFactory::create());
```

Each injector uses a caching reflector by default. Reflection metadata is
cached for the lifetime of that reflector; the package does not claim that
reflection is cost-free or that it is always faster than another approach.

## Autowiring concrete classes

A concrete class whose required constructor arguments are concrete class types
needs no registration:

```php
<?php

declare(strict_types=1);

namespace App;

final class SparkPlug
{
}

final class Piston
{
}

final class V8
{
    public function __construct(
        public readonly SparkPlug $sparkPlug,
        public readonly Piston $piston,
    ) {
    }
}

final class Car
{
    public function __construct(public readonly V8 $engine)
    {
    }
}
```

```php
<?php

use App\Car;

$car = $injector->make(Car::class);

assert($car instanceof Car);
assert($car->engine instanceof App\V8);
```

`make()` recursively resolves the dependency tree. Constructors must be
public. Interfaces, abstract classes, builtin parameters, and ambiguous union
or intersection types need an explicit mapping or argument value.

## Mapping abstractions with aliases

Use `alias()` when a type declaration should resolve to a particular
implementation:

```php
<?php

declare(strict_types=1);

namespace App;

interface Engine
{
}

final class V8 implements Engine
{
}

final class Car
{
    public function __construct(public readonly Engine $engine)
    {
    }
}
```

```php
<?php

use App\Car;
use App\Engine;
use App\V8;

$injector->alias(Engine::class, V8::class);

$car = $injector->make(Car::class);
assert($car->engine instanceof V8);
```

Aliases may form chains. The injector normalizes class names and detects alias
cycles. A class or interface cannot be both aliased and directly shared in
conflicting ways.

## Constructor argument definitions

Use `define()` to configure one class. Definition keys normally match
constructor parameter names:

```php
<?php

use App\Car;
use App\V8;

$injector->define(Car::class, [
    'engine' => V8::class,
]);
```

A bare named key means “make this class.” It is suitable for class-string
values, not scalar values or existing objects.

Definitions support the following forms:

| Form                                   | Meaning                                  | Example                                               |
|----------------------------------------|------------------------------------------|-------------------------------------------------------|
| `'name' => ClassName::class`           | Resolve the value with `make()`          | `'engine' => V8::class`                               |
| `':name' => $value`                    | Inject a raw value                       | `':port' => 2525`                                     |
| `'+name' => $callable`                 | Invoke an argument provider              | `'+requestId' => $provider`                           |
| `'@name' => [ClassName::class, $args]` | Make a class with nested definitions     | `'@mailer' => [SmtpMailer::class, [':port' => 2525]]` |
| `0 => $value`                          | Inject a raw value by parameter position | `0 => 'sqlite::memory:'`                              |

The three named prefixes are also exposed as `Injector::A_RAW`,
`Injector::A_DELEGATE`, and `Injector::A_DEFINE`.

### Raw scalar, array, and object values

Prefix a named parameter with `:` to prevent the injector from interpreting
its value as a class name:

```php
<?php

use PDO;

$injector
    ->define(PDO::class, [
        ':dsn' => 'sqlite:/var/app/data.sqlite',
        ':username' => null,
        ':password' => null,
    ])
    ->share(PDO::class);
```

Existing objects also need the raw prefix when used in a named definition:

```php
<?php

$clock = new App\SystemClock();

$injector->define(App\TokenService::class, [
    ':clock' => $clock,
]);
```

Numeric definitions are always positional raw values. Named definitions are
usually clearer and remain correct if parameters are reordered.

### Argument providers

The `+` prefix registers a callable that supplies one argument. The injector
passes the requested parameter name and itself to the callable:

```php
<?php

use Qubus\Injector\Injector;

$injector->define(App\RequestContext::class, [
    '+requestId' => static function (
        string $parameter,
        Injector $injector,
    ): string {
        return bin2hex(random_bytes(16));
    },
]);
```

This callable is trusted application code. Its return value is inserted as-is.

### Nested class definitions

Use `@` when one argument needs a one-off class definition:

```php
<?php

$injector->define(App\NotificationService::class, [
    '@mailer' => [
        App\SmtpMailer::class,
        [
            ':host' => 'smtp.example.test',
            ':port' => 2525,
        ],
    ],
]);
```

The nested argument array follows the same definition rules.

### Call-time definitions

The second argument to `make()` supplies definitions for that call:

```php
<?php

$service = $injector->make(App\NotificationService::class, [
    'mailer' => App\NullMailer::class,
]);
```

Call-time values replace matching stored values for this construction. They do
not rewrite the stored definition. If the requested type already has a cached
shared instance, that instance is returned and call-time definitions cannot
reconstruct it.

### Global parameter definitions

`defineParam()` supplies a fallback by parameter name:

```php
<?php

$injector->defineParam('timezone', 'UTC');

$formatter = $injector->make(App\DateFormatter::class);
```

A class-specific or call-time definition takes precedence. Type-driven
resolution is attempted before the global value; the global value is used
before the parameter's declared default.

## Argument resolution order

Stored definitions and call-time definitions are merged first, with call-time
entries replacing matching stored entries. Constructor parameters are then
resolved in this order:

1. a positional numeric definition;
2. a bare named class definition;
3. a named raw definition (`:`);
4. a named argument provider (`+`);
5. a named nested class definition (`@`);
6. a resolvable declared class type, including its alias, delegate, or share;
7. a global value registered with `defineParam()`;
8. the parameter's default value;
9. `null` for an optional internal parameter when reflection exposes no
   usable default; otherwise an `InjectionException`.

At the requested-object level, an already-created share is returned first. A
registered delegate creates the object instead of normal constructor
provisioning. Preparations run after a new object is created.

## Sharing instances

`share()` provides container-scoped instance reuse.

### Lazy sharing by class name

```php
<?php

$injector->share(App\EventBus::class);

$first = $injector->make(App\EventBus::class);
$second = $injector->make(App\EventBus::class);

assert($first === $second);
```

Passing a class name delays construction until the first request.

### Sharing an existing object

```php
<?php

$connection = new PDO('sqlite:/var/app/data.sqlite');
$injector->share($connection);

assert($injector->make(PDO::class) === $connection);
```

The public API has no `unshare()` or `refresh()` method. Create a new
injector when a different container scope is required.

To share an implementation behind an interface, alias the interface and share
the implementation:

```php
<?php

$injector
    ->alias(App\Clock::class, App\SystemClock::class)
    ->share(App\SystemClock::class);
```

## Delegated construction

`delegate()` replaces normal construction with a factory. Factory parameters
are themselves resolved by the injector:

```php
<?php

use App\Clock;
use App\TokenService;

$injector->delegate(
    TokenService::class,
    static fn (Clock $clock): TokenService => new TokenService($clock),
);

$tokens = $injector->make(TokenService::class);
```

The factory must return an object. Supported executable forms include:

- a closure or other callable;
- a function name;
- an invokable object or invokable class name;
- `[$object, 'method']`;
- `[ClassName::class, 'staticMethod']`;
- `'ClassName::staticMethod'`; and
- an instance-method class reference, for which the injector first provisions
  the owning object.

Only public functions and methods can be invoked.

## Preparations and setter injection

`prepare()` runs after an object has been created. Register a class or
interface name and a callback:

```php
<?php

use App\Report;
use Qubus\Injector\Injector;

$injector->prepare(
    Report::class,
    static function (Report $report, Injector $injector): void {
        $report->setLocale('en_US');
    },
);

$report = $injector->make(Report::class);
```

Preparation callbacks receive the created object and the injector as their two
arguments. A callback may mutate the object and return nothing, or return a
replacement compatible with the registered class or interface. Constructor
injection is generally preferable when the class design permits it.

## Executing callables with injection

`execute()` resolves a callable's parameters and returns its result:

```php
<?php

$result = $injector->execute(
    [App\ReportController::class, 'show'],
    [
        ':reportId' => 42,
    ],
);
```

The callable may be a closure, function, invokable class or object, static
method, object method, or public instance method referenced by class. Argument
definitions use the same key syntax and precedence as constructor definitions.

When an executable will be called repeatedly, build it once:

```php
<?php

$executable = $injector->buildExecutable(
    [App\ReportController::class, 'show'],
);

$first = $executable(41);
$second = $executable(42);
```

`buildExecutable()` returns `Qubus\Injector\Executable`. Its public
inspection methods are:

- `getCallableReflection(): ReflectionFunctionAbstract`;
- `getInvocationObject()`, which returns the invocation object or `null`;
  and
- `isInstanceMethod(): bool`.

Arguments supplied directly to `Executable::__invoke()` are passed to the
callable as-is; use `execute()` when missing parameters need container
resolution.

## Lazy proxies

`proxy()` delegates construction through a user-supplied proxy factory. The
callback receives the resolved class name and a zero-argument initializer
that constructs the real object:

```php
<?php

use ProxyManager\Factory\LazyLoadingValueHolderFactory;

$factory = new LazyLoadingValueHolderFactory();

$injector->proxy(
    App\ExpensiveService::class,
    static fn (string $class, Closure $initializer): object =>
        $factory->createProxy(
            $class,
            static function (
                & $wrappedObject,
                object $proxy,
                string $method,
                array $parameters,
                & $initializer,
            ) use ($initializer): bool {
                $wrappedObject = $initializer();
                $initializer = null;

                return true;
            },
        ),
);
```

Proxy callbacks and their returned objects are application-controlled. Proxy
registrations are not included in `inspect()` output.

## Inspecting registrations

`inspect()` returns registered mappings. With no arguments it returns every
inspectable category:

```php
<?php

use Qubus\Injector\Injector;

$all = $injector->inspect();

$forClock = $injector->inspect(App\Clock::class);

$aliasesAndShares = $injector->inspect(
    nameFilter: null,
    typeFilter: Injector::I_ALIASES | Injector::I_SHARES,
);
```

The result is keyed by these constants:

| Constant                | Value | Category                         |
|-------------------------|------:|----------------------------------|
| `Injector::I_BINDINGS`  |     1 | Class and parameter definitions  |
| `Injector::I_DELEGATES` |     2 | Construction delegates           |
| `Injector::I_PREPARES`  |     4 | Preparations                     |
| `Injector::I_ALIASES`   |     8 | Aliases                          |
| `Injector::I_SHARES`    |    16 | Shared class names and instances |
| `Injector::I_ALL`       |    31 | All inspectable categories       |

The optional filter is normalized like a class name. The optional type filter
is a bitmask.

## Inspecting the active dependency chain

`getInjectionChain()` returns a `Qubus\Injector\InjectionChain` snapshot.
This is useful in delegates and diagnostics:

```php
<?php

$injector->delegate(
    App\Logger::class,
    static function () use ($injector): App\Logger {
        $chain = $injector->getInjectionChain();

        foreach ($chain->getChain() as $consumer) {
            // Class names are normalized by the injector.
        }

        return new App\Logger();
    },
);
```

`InjectionChain::getChain()` returns the complete array.
`getByIndex($index)` returns an entry or `false`; negative indexes count
backward from the end. Circular construction and alias cycles are rejected
with an `InjectionException`.

## Configuration-driven registration

`InjectorFactory::create()` accepts a mapping array:

```php
<?php

use App\Clock;
use App\Mailer;
use App\NotificationService;
use App\SmtpMailer;
use App\SystemClock;
use Qubus\Injector\Config\InjectorFactory;
use Qubus\Injector\Injector;

$config = InjectorFactory::create([
    'standardAliases' => [
        Mailer::class => SmtpMailer::class,
    ],
    'sharedAliases' => [
        Clock::class => SystemClock::class,
    ],
    'argumentDefinitions' => [
        SmtpMailer::class => [
            'host' => 'smtp.example.test',
            'port' => 2525,
        ],
    ],
    'delegations' => [
        App\RequestId::class =>
            static fn (): App\RequestId => App\RequestId::generate(),
    ],
    'preparations' => [
        NotificationService::class =>
            static function (NotificationService $service): void {
                $service->enableMetrics();
            },
    ],
]);

$injector = new Injector($config);
```

`sharedAliases` both creates the alias and marks its resolved implementation
as shared, so the same mapping does not also need to appear in
`standardAliases`. The six mapping names are available as
`Injector::STANDARD_ALIASES`, `SHARED_ALIASES`,
`ARGUMENT_DEFINITIONS`, `ARGUMENT_PROVIDERS`, `DELEGATIONS`, and
`PREPARATIONS`.

Configuration `argumentDefinitions` use plain parameter names. Non-callable
scalar, array, and object values are converted into raw definitions
automatically. Use `Qubus\Injector\Injection` when a value is a class to
be made:

```php
<?php

use App\Mailer;
use App\NotificationService;
use App\SmtpMailer;
use Qubus\Injector\Config\InjectorFactory;
use Qubus\Injector\Injection;

$config = InjectorFactory::create([
    'argumentDefinitions' => [
        NotificationService::class => [
            'mailer' => new Injection(SmtpMailer::class),
        ],
    ],
]);
```

### Configuration argument providers

`argumentProviders` can install interface-based lazy proxies for selected
constructor parameters:

```php
<?php

use App\Mailer;
use App\NotificationService;
use App\SmtpMailer;
use Qubus\Injector\Config\InjectorFactory;

$config = InjectorFactory::create([
    'argumentProviders' => [
        'mailer' => [
            'interface' => Mailer::class,
            'mappings' => [
                NotificationService::class =>
                    static fn (string $target, string $interface): object =>
                        new SmtpMailer('smtp.example.test', 2525),
            ],
        ],
    ],
]);
```

Each mapping callback receives the target class and configured interface and
must return an object compatible with that interface. Supply a non-empty
`interface` for callable mappings. Callable proxy factories belong under
`argumentProviders`, not `argumentDefinitions`. This feature uses the
installed ProxyManager implementation.

Additional mappings can be applied later:

```php
<?php

$injector->registerMappings(InjectorFactory::create([
    'standardAliases' => [
        App\Cache::class => App\ArrayCache::class,
    ],
]));
```

Invalid mapping shapes or callbacks result in
`Qubus\Injector\InvalidMappingsException` or
`Qubus\Injector\ConfigException`.

## PSR-11 container

The PSR-11 implementation is
`Qubus\Injector\Psr11\Container`, not
`Qubus\Injector\Container\ServiceContainer`:

```php
<?php

use App\Clock;
use App\SystemClock;
use Psr\Container\ContainerInterface;
use Qubus\Injector\Config\InjectorFactory;
use Qubus\Injector\Psr11\Container;

$container = new Container(InjectorFactory::create());
$container->alias(Clock::class, SystemClock::class);

$clock = $container->get(Clock::class);

assert($container instanceof ContainerInterface);
assert($container->has(Clock::class));
assert($clock instanceof SystemClock);
```

`has()` can return `true` for an unregistered concrete class when it is
instantiable through autowiring. `get()` throws:

- `Qubus\Injector\Psr11\NotFoundException` when an identifier is neither
  registered nor an existing class; and
- `Qubus\Injector\Psr11\ContainerException` when the entry exists but
  cannot be constructed.

Both exceptions implement their corresponding PSR-11 interfaces.
`Qubus\Injector\Psr11\NotFoundException` also extends the legacy
`Qubus\Exception\Http\Client\NotFoundException`, preserving existing
catch blocks while adding the PSR-11 contract.

If application code should receive the container through
`Psr\Container\ContainerInterface`, register that policy explicitly:

```php
<?php

$container
    ->alias(Psr\Container\ContainerInterface::class, $container::class)
    ->share($container);
```

## Service-provider contracts

The package includes:

- `Qubus\Injector\ServiceProvider\Serviceable`, which declares
  `register(): void`;
- `Qubus\Injector\ServiceProvider\Bootable`, which declares boot,
  callback, and publishing methods; and
- the abstract
  `Qubus\Injector\ServiceProvider\BaseServiceProvider`.

`BaseServiceProvider` stores the `ServiceContainer` and supplies no-op
`register()` and `boot()` methods. It intentionally remains abstract and
does not choose a boot-callback or publishing policy. A framework-specific base
class or each concrete provider must implement the other `Bootable` methods.

For example, an application can define its own lifecycle policy:

```php
<?php

declare(strict_types=1);

namespace App\Provider;

use Closure;
use Qubus\Injector\ServiceProvider\BaseServiceProvider;

abstract class ApplicationServiceProvider extends BaseServiceProvider
{
    /** @var list<Closure> */
    private array $bootingCallbacks = [];

    /** @var list<Closure> */
    private array $bootedCallbacks = [];

    /** @var array<string, array<string, string>> */
    private array $published = [];

    public function booting(Closure $callback): void
    {
        $this->bootingCallbacks[] = $callback;
    }

    public function booted(Closure $callback): void
    {
        $this->bootedCallbacks[] = $callback;
    }

    public function callBootingCallbacks(): void
    {
        foreach ($this->bootingCallbacks as $callback) {
            $this->container->execute($callback);
        }
    }

    public function callBootedCallbacks(): void
    {
        foreach ($this->bootedCallbacks as $callback) {
            $this->container->execute($callback);
        }
    }

    public function publishes(array $paths, ?string $group = null): void
    {
        $group ??= 'default';
        $this->published[$group] = array_replace(
            $this->published[$group] ?? [],
            $paths,
        );
    }

    public function pathsToPublish(?string $tag = null): array
    {
        if ($tag !== null) {
            return $this->published[$tag] ?? [];
        }

        return array_merge(...array_values($this->published ?: [[]]));
    }
}
```

A concrete provider can then register application mappings:

```php
<?php

declare(strict_types=1);

namespace App\Provider;

use App\Clock;
use App\SystemClock;

final class CoreServiceProvider extends ApplicationServiceProvider
{
    public function register(): void
    {
        $this->container
            ->alias(Clock::class, SystemClock::class)
            ->share(SystemClock::class);
    }
}
```

The application or framework is responsible for instantiating providers and
deciding lifecycle order. A typical order is register every provider, run
booting callbacks, boot every provider, then run booted callbacks. Nothing in
the injector automatically loads `bootstrap/providers.php` or
`config/app.php`.

### CodefyPHP service providers

CodefyPHP supplies the framework-specific policy through
`Codefy\Framework\Support\CodefyServiceProvider`. It extends
`BaseServiceProvider`, stores the application as `$this->codefy`, manages
booting and booted callbacks, implements publishing groups, and exposes
`defaultProviders()` and `publishTags()`.

A CodefyPHP application provider can therefore concentrate on container
registration and application boot work:

```php
<?php

declare(strict_types=1);

namespace Application\Provider;

use Application\Contract\Clock;
use Application\Service\ReportService;
use Application\Support\SystemClock;
use Codefy\Framework\Support\CodefyServiceProvider;

final class AppServiceProvider extends CodefyServiceProvider
{
    public function register(): void
    {
        $this->codefy->alias(
            original: Clock::class,
            alias: SystemClock::class,
        );

        $this->codefy->share(nameOrInstance: Clock::class);

        $this->codefy->define(
            name: ReportService::class,
            args: [
                ':timezone' => 'UTC',
            ],
        );
    }

    public function boot(): void
    {
        $this->publishes(
            paths: [
                __DIR__ . '/../../resources/report.php' => 'config',
            ],
            group: 'config',
        );
    }
}
```

`register()` should define aliases, arguments, delegates, proxies, and
shares. Code that depends on all providers having been registered belongs in
`boot()`. CodefyPHP invokes provider booting callbacks, executes `boot()`,
and then invokes provider booted callbacks.

Application providers can be listed in `bootstrap/providers.php`:

```php
<?php

return [
    Application\Provider\AppServiceProvider::class,
];
```

They can also be merged with CodefyPHP's defaults in `config/app.php`:

```php
<?php

use Codefy\Framework\Support\CodefyServiceProvider;

return [
    // Other application settings...

    'providers' => CodefyServiceProvider::defaultProviders()
        ->merge([
            Application\Provider\AppServiceProvider::class,
        ])
        ->toArray(),
];
```

Current CodefyPHP applications combine configured providers with the
`bootstrap/providers.php` list and de-duplicate the resulting class names.
The framework's `app()` helper resolves entries through its application
container:

```php
<?php

use Application\Service\ReportService;

use function Codefy\Framework\Helpers\app;

$reports = app(name: ReportService::class);

assert($reports instanceof ReportService);
```

These files, the `app()` helper, and automatic provider lifecycle handling
belong to CodefyPHP. Applications using Qubus Injector directly should use
their own provider runner, as shown in the preceding section.

## Reflectors and reflection caches

The default reflector is
`Qubus\Injector\Cache\CachingReflector`, backed by
`Qubus\Injector\Cache\ArrayReflectionCache`. Supply a custom reflector
when another cache lifetime or reflection strategy is required:

```php
<?php

use Qubus\Injector\Cache\ArrayReflectionCache;
use Qubus\Injector\Cache\CachingReflector;
use Qubus\Injector\Config\InjectorFactory;
use Qubus\Injector\Injector;
use Qubus\Injector\StandardReflector;

$reflector = new CachingReflector(
    reflector: new StandardReflector(),
    cache: new ArrayReflectionCache(),
);

$injector = new Injector(InjectorFactory::create(), $reflector);
```

`Qubus\Injector\Reflector` defines:

| Method                                                                               | Result                            |
|--------------------------------------------------------------------------------------|-----------------------------------|
| `getClass(string\|object $class)`                                                    | A `ReflectionClass`               |
| `getConstructor(string\|object $class)`                                              | Its `ReflectionMethod`, or `null` |
| `getConstructorParams(string\|object $class)`                                        | Constructor parameters, or `null` |
| `getParamTypeHint(ReflectionFunctionAbstract $function, ReflectionParameter $param)` | One class type name, or `null`    |
| `getFunction(string\|Closure $function)`                                             | A `ReflectionFunction`            |
| `getMethod(string\|object $class, string $method)`                                   | A `ReflectionMethod`              |

`Qubus\Injector\Cache\ReflectionCache` defines
`fetch(string $key)` and `store(string $key, $data)`. Their return types
remain undeclared for compatibility with existing third-party cache
implementations. Bundled cache implementations return the cached value from
`fetch()` and return nothing from `store()`. A cache miss is represented
by `false`; `null` is a cacheable value.

The package also exposes `ApcReflectionCache` and
`ApcuReflectionCache`. They require the corresponding extension and a
runtime capable of storing the reflected values. Both use a five-second
external-cache TTL by default; `setTimeToLive(int $seconds)` changes it to a
positive value. A failed store throws `ApcStoreException` or
`ApcuStoreException`. The array cache is the portable default.

The standard reflector resolves one unambiguous non-builtin named class type.
For a union, it can resolve the type when exactly one member is a non-builtin
class. It also understands `self`, `static`, and `parent`. Builtins,
unions with multiple class members, and intersection types require explicit
definitions.

## Configuration object API

`Qubus\Injector\Config\InjectorConfig` implements `Config` and extends
`ArrayObject`, providing array access, iteration, and counting. It provides:

| Method                                             | Purpose                                                           |
|----------------------------------------------------|-------------------------------------------------------------------|
| `all(): array`                                     | Return all configuration                                          |
| `get(string $key, $default = null): string\|array` | Read a string or array; string keys support dot notation          |
| `has(string $key): bool`                           | Check whether a key exists, including a key whose value is `null` |
| `add($key, $value): InjectorConfig`                | Add or replace a value; a `null` key appends                      |
| `remove(...$withKeys): InjectorConfig`             | Remove one or more top-level values                               |
| `merge(...$arrayToMerge): InjectorConfig`          | Recursively merge arrays or traversable values                    |
| `toArray(): array`                                 | Export the configuration                                          |
| `toJson(): string`                                 | JSON encode with exception reporting                              |
| `count(): int`                                     | Count top-level entries                                           |

`InjectorFactory::create($config, $default)` recursively combines defaults
and supplied configuration and returns an `InjectorConfig`.
`ArrayAccess` operations support integer offsets and mixed values. The
minimal `Config` interface deliberately retains its original string-key and
`string|array` return contract so existing custom implementations remain
valid.

## Public API quick reference

`Qubus\Injector\ServiceContainer` defines the primary fluent API:

| Method                                                                                           | Result                                            |
|--------------------------------------------------------------------------------------------------|---------------------------------------------------|
| `define(string $name, array $args): ServiceContainer`                                            | Store constructor definitions                     |
| `defineParam(string $paramName, $value): ServiceContainer`                                       | Store a global parameter fallback                 |
| `alias(string $original, string $alias): ServiceContainer`                                       | Map an abstraction or class name                  |
| `share(string\|object $nameOrInstance): ServiceContainer`                                        | Register a lazy class share or immediate instance |
| `prepare(string $name, callable\|string\|array\|object $callableOrMethodStr): ServiceContainer`  | Register post-construction work                   |
| `delegate(string $name, callable\|string\|array\|object $callableOrMethodStr): ServiceContainer` | Register a construction factory                   |
| `proxy(string $name, callable\|string\|array\|object $callableOrMethodStr): ServiceContainer`    | Register a lazy proxy factory                     |
| `make(string $name, array $args = [])`                                                           | Resolve an entry                                  |
| `execute(callable\|string\|array\|object $callableOrMethodStr, array $args = [])`                | Resolve and invoke a callable                     |

`Qubus\Injector\Injector` is constructed with
`__construct(Config $config, ?Reflector $reflector = null)` and additionally
exposes:

| Method                                                                              | Purpose                                    |
|-------------------------------------------------------------------------------------|--------------------------------------------|
| `registerMappings(Config $config): void`                                            | Apply configuration mappings               |
| `inspect(?string $nameFilter = null, ?int $typeFilter = null)`                      | Inspect registrations                      |
| `buildExecutable(callable\|string\|array\|object $callableOrMethodStr): Executable` | Normalize a callable for direct invocation |
| `getInjectionChain(): InjectionChain`                                               | Snapshot the active dependency chain       |

The small `Qubus\Injector\Injection` value object accepts an alias in its
constructor and exposes it through `getAlias(): string`. It is used by
configuration-driven argument definitions. Cloning an injector preserves
registrations but resets the active construction chain.

## Errors and safe usage

Provisioning and invocation failures use
`Qubus\Injector\InjectionException`. Its
`getDependencyChain()` method exposes the relevant resolution chain.
`Qubus\Injector\InjectorException` defines numeric codes
for invalid aliases, shares, executables, constructors, definitions, cycles,
and factory failures.

| Code constant              | Meaning                                                    |
|----------------------------|------------------------------------------------------------|
| `E_NON_EMPTY_STRING_ALIAS` | An alias endpoint is empty                                 |
| `E_SHARED_CANNOT_ALIAS`    | A populated share cannot be aliased                        |
| `E_SHARE_ARGUMENT`         | `share()` received neither a class string nor an object    |
| `E_ALIASED_CANNOT_SHARE`   | An already-aliased name was shared as an instance          |
| `E_INVOKABLE`              | An executable is invalid                                   |
| `E_NON_PUBLIC_CONSTRUCTOR` | A constructor is not public                                |
| `E_NEEDS_DEFINITION`       | An interface or abstract class has no construction mapping |
| `E_MAKE_FAILURE`           | Reflection could not construct the requested class         |
| `E_UNDEFINED_PARAM`        | A required parameter cannot be resolved                    |
| `E_DELEGATE_ARGUMENT`      | A delegate registration is invalid                         |
| `E_CYCLIC_DEPENDENCY`      | The object graph contains a cycle                          |
| `E_MAKING_FAILED`          | Construction or a factory returned a non-object            |
| `E_CYCLIC_ALIAS`           | An alias would create a cycle                              |
| `E_INVALID_DEFINITION`     | A nested `@` definition is malformed                       |

Each code has a paired `M_...` message constant on the same interface.

Container mappings, class names, and executable names must be treated as
trusted application configuration. Do not pass unvalidated request data to
`make()`, `execute()`, `delegate()`, `proxy()`, or configuration
mappings: these APIs can instantiate classes and invoke public PHP callables.

The injector resolves object graphs; it does not manage process, request, or
transaction lifetimes beyond the scope of a particular injector instance.
Create appropriately scoped injector instances and explicitly configure
resources that need cleanup.
