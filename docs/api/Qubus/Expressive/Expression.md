# Expression

***

* Full name: `\Qubus\Expressive\Expression`

## Properties

### value

```php
protected mixed $value
```

***

## Methods

### __construct

```php
public __construct(mixed $value): mixed
```

**Parameters:**

| Parameter | Type      | Description      |
|-----------|-----------|------------------|
| `$value`  | **mixed** | expression value |

***

### value

Get the expression value as a string.

```php
public value(): string
```

$sql = $expression->value();

***

### __toString

Return the value of the expression as a string.

```php
public __toString(): string
```

echo $expression;

***
