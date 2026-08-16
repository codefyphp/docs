# MacroAware

***

* Full name: `\Qubus\Inheritance\MacroAware`

## Properties

### macros

The registered string macros.

```php
protected static array $macros
```

* This property is **static**.

***

## Methods

### macro

Register a custom macro.

```php
public static macro(string $name, object|callable $macro): void
```

* This method is **static**.
**Parameters:**

| Parameter | Type                 | Description |
|-----------|----------------------|-------------|
| `$name`   | **string**           |             |
| `$macro`  | **object\|callable** |             |

***
### mixin

Mix another object into the class.

```php
public static mixin(object $mixin, bool $replace = true): void
```

* This method is **static**.
**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$mixin`   | **object** |             |
| `$replace` | **bool**   |             |

**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

***
### hasMacro

Checks if macro is registered.

```php
public static hasMacro(string $name): bool
```

* This method is **static**.
**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$name`   | **string** |             |

***
### flushMacros

Flush the existing macros.

```php
public static flushMacros(): void
```

* This method is **static**.
***
### __callStatic

Dynamically handle calls to the class.

```php
public static __callStatic(string $method, mixed $parameters): mixed
```

* This method is **static**.
**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$method`     | **string** |             |
| `$parameters` | **mixed**  |             |

**Throws:**

- [`BadMethodCallException`](../../BadMethodCallException.md)

***
### __call

Dynamically handle calls to the class.

```php
public __call(string $method, mixed $parameters): mixed
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$method`     | **string** |             |
| `$parameters` | **mixed**  |             |

**Throws:**

- [`BadMethodCallException`](../../BadMethodCallException.md)

***
