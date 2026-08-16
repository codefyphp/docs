# Middleware

***

* Full name: `\Codefy\Framework\Configuration\Middleware`

## Properties

### customAliases

```php
protected static array $customAliases
```

* This property is **static**.

***

## Methods

### alias

Register additional middleware aliases.

```php
public alias(array<string,class-string<\Psr\Http\Server\MiddlewareInterface>> $aliases): $this
```

**Parameters:**

| Parameter  | Type                                                                 | Description |
|------------|----------------------------------------------------------------------|-------------|
| `$aliases` | **array<string,class-string<\Psr\Http\Server\MiddlewareInterface>>** |             |

***

### defaultMiddlewares

```php
public static defaultMiddlewares(): \Codefy\Framework\Support\DefaultMiddlewares
```

* This method is **static**.
***

### getAliases

Returns additional middleware aliases.

```php
public getAliases(): array
```

***
