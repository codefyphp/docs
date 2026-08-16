# SeederTransaction

***

* Full name: `\Qubus\Expressive\Migration\Seeder\SeederTransaction`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### context

```php
private \Qubus\Expressive\Migration\Seeder\SeederContext $context
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\Migration\Seeder\SeederContext $context): mixed
```

**Parameters:**

| Parameter  | Type                                                 | Description |
|------------|------------------------------------------------------|-------------|
| `$context` | **\Qubus\Expressive\Migration\Seeder\SeederContext** |             |

***

### run

```php
public run(string $seederClass): void
```

**Parameters:**

| Parameter      | Type       | Description |
|----------------|------------|-------------|
| `$seederClass` | **string** |             |

**Throws:**

- [`Exception`](../../../../Exception.md)

***

### runWithDependencies

```php
private runWithDependencies(string $class): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$class`  | **string** |             |

**Throws:**

- [`ContainerExceptionInterface`](../../../../Psr/Container/ContainerExceptionInterface.md)
- [`NotFoundExceptionInterface`](../../../../Psr/Container/NotFoundExceptionInterface.md)
- [`ReflectionException`](../../../../ReflectionException.md)

***
