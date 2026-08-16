# ConditionalAware

***

* Full name: `\Qubus\Inheritance\ConditionalAware`

## Methods

### when

Apply the callback if the given "value" is (or resolves to) truthy.

```php
public when(mixed|null $value = null, callable|null $callback = null, callable|null $default = null): mixed
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$value`    | **mixed\|null**    |             |
| `$callback` | **callable\|null** |             |
| `$default`  | **callable\|null** |             |

***
### whenNot

Apply the callback if the given "value" is (or resolves to) falsy.

```php
public whenNot(mixed|null $value = null, callable|null $callback = null, callable|null $default = null): mixed
```

**Parameters:**

| Parameter   | Type               | Description |
|-------------|--------------------|-------------|
| `$value`    | **mixed\|null**    |             |
| `$callback` | **callable\|null** |             |
| `$default`  | **callable\|null** |             |

***
