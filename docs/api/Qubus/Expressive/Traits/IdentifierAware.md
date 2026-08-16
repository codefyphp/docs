# IdentifierAware

***

* Full name: `\Qubus\Expressive\Traits\IdentifierAware`

## Methods

### quoteIdentifier

```php
public quoteIdentifier(string $identifier): string
```

**Parameters:**

| Parameter     | Type       | Description |
|---------------|------------|-------------|
| `$identifier` | **string** |             |

***
### quote

Quote a value for an SQL query.

```php
public quote(float|array<array-key,float|bool|int|string|null>|bool|int|string|null $value = null): false|int|string
```

Objects passed to this function will be converted to strings.
Expression objects will use the value of the expression.
Query objects will be compiled and converted to a sub-query.
Fnc objects will be sent of for compiling.
All other objects will be converted using the `__toString` method.

**Parameters:**

| Parameter | Type                                                                                | Description        |
|-----------|-------------------------------------------------------------------------------------|--------------------|
| `$value`  | **float\|array<array-key,float\|bool\|int\|string\|null>\|bool\|int\|string\|null** | any value to quote |

***
