# Attribute

***

* Full name: `\Qubus\Validation\Attribute`

## Properties

### rules

```php
protected array $rules
```

***

### key

```php
protected string $key
```

***

### alias

```php
protected ?string $alias
```

***

### validation

```php
protected ?\Qubus\Validation\Validation $validation
```

***

### required

```php
protected bool $required
```

***

### primaryAttribute

```php
protected ?\Qubus\Validation\Attribute $primaryAttribute
```

***

### otherAttributes

```php
protected array $otherAttributes
```

***

### keyIndexes

```php
protected array $keyIndexes
```

***

## Methods

### __construct

```php
public __construct(\Qubus\Validation\Validation $validation, string $key, string|null $alias = null, array $rules = []): void
```

**Parameters:**

| Parameter     | Type                             | Description |
|---------------|----------------------------------|-------------|
| `$validation` | **\Qubus\Validation\Validation** |             |
| `$key`        | **string**                       |             |
| `$alias`      | **string\|null**                 |             |
| `$rules`      | **array**                        |             |

***

### setPrimaryAttribute

Set the primary attribute.

```php
public setPrimaryAttribute(\Qubus\Validation\Attribute $primaryAttribute): void
```

**Parameters:**

| Parameter           | Type                            | Description |
|---------------------|---------------------------------|-------------|
| `$primaryAttribute` | **\Qubus\Validation\Attribute** |             |

***

### setKeyIndexes

Set key indexes.

```php
public setKeyIndexes(array $keyIndexes): void
```

**Parameters:**

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `$keyIndexes` | **array** |             |

***

### getPrimaryAttribute

Get primary attributes.

```php
public getPrimaryAttribute(): \Qubus\Validation\Attribute|null
```

***

### setOtherAttributes

Set other attributes.

```php
public setOtherAttributes(array $otherAttributes): void
```

**Parameters:**

| Parameter          | Type      | Description |
|--------------------|-----------|-------------|
| `$otherAttributes` | **array** |             |

***

### addOtherAttribute

Add other attributes.

```php
public addOtherAttribute(\Qubus\Validation\Attribute $otherAttribute): void
```

**Parameters:**

| Parameter         | Type                            | Description |
|-------------------|---------------------------------|-------------|
| `$otherAttribute` | **\Qubus\Validation\Attribute** |             |

***

### getOtherAttributes

Get other attributes.

```php
public getOtherAttributes(): array
```

***

### addRule

Add rule.

```php
public addRule(\Qubus\Validation\Rule $rule): void
```

**Parameters:**

| Parameter | Type                       | Description |
|-----------|----------------------------|-------------|
| `$rule`   | **\Qubus\Validation\Rule** |             |

***

### getRule

Get rule.

```php
public getRule(string $ruleKey): void
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$ruleKey` | **string** |             |

***

### getRules

Get rules.

```php
public getRules(): array
```

***

### hasRule

Check the $ruleKey has in the rule.

```php
public hasRule(string $ruleKey): bool
```

**Parameters:**

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `$ruleKey` | **string** |             |

***

### setRequired

Set required.

```php
public setRequired(bool $required): void
```

**Parameters:**

| Parameter   | Type     | Description |
|-------------|----------|-------------|
| `$required` | **bool** |             |

***

### isRequired

Set rule is required.

```php
public isRequired(): bool
```

***

### getKey

Get key.

```php
public getKey(): string
```

***

### getKeyIndexes

Get key indexes.

```php
public getKeyIndexes(): array
```

***

### getValue

Get value.

```php
public getValue(string|null $key = null): mixed
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$key`    | **string\|null** |             |

**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)

***

### isArrayAttribute

Get that is array attribute.

```php
public isArrayAttribute(): bool
```

***

### isUsingDotNotation

Check this attribute is using dot notation.

```php
public isUsingDotNotation(): bool
```

***

### resolveSiblingKey

Resolve sibling key.

```php
public resolveSiblingKey(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### getHumanizedKey

Get humanize key.

```php
public getHumanizedKey(): string
```

***

### setAlias

Set alias.

```php
public setAlias(string $alias): void
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$alias`  | **string** |             |

***

### getAlias

Get alias.

```php
public getAlias(): string|null
```

***
