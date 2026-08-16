# SeederContext

***

* Full name: `\Qubus\Expressive\Migration\Seeder\SeederContext`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Properties

### db

```php
public \Qubus\Expressive\Database $db
```

***

### container

```php
public \Psr\Container\ContainerInterface $container
```

***

### environment

```php
public string $environment
```

***

### isProduction

```php
public bool $isProduction
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Expressive\Database $db, \Psr\Container\ContainerInterface $container, string $environment, bool $isProduction): mixed
```

**Parameters:**

| Parameter       | Type                                  | Description |
|-----------------|---------------------------------------|-------------|
| `$db`           | **\Qubus\Expressive\Database**        |             |
| `$container`    | **\Psr\Container\ContainerInterface** |             |
| `$environment`  | **string**                            |             |
| `$isProduction` | **bool**                              |             |

***

### resolve

```php
public resolve(string $class): \Qubus\Expressive\Migration\Seeder\Seeder
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$class`  | **string** |             |

**Throws:**

- [`ContainerExceptionInterface`](../../../../Psr/Container/ContainerExceptionInterface.md)
- [`NotFoundExceptionInterface`](../../../../Psr/Container/NotFoundExceptionInterface.md)

***
