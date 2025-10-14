***

# PayloadAware





* Full name: `\Codefy\CommandBus\Traits\PayloadAware`



## Properties


### payload



```php
private array $payload
```






***

### REQUIRED_FIELDS



```php
protected static array $REQUIRED_FIELDS
```



* This property is **static**.


***

### ALLOWED_FIELDS



```php
protected static array $ALLOWED_FIELDS
```



* This property is **static**.


***

## Methods


### __construct



```php
public __construct(array $payload = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$payload` | **array** |  |





***

### fromPayload



```php
public static fromPayload(array $payload): static
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$payload` | **array** |  |





***

### with



```php
public with(string $key, mixed $value = null): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$value` | **mixed** |  |





***

### without



```php
public without(string $key): static
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### get



```php
public get(string $key, mixed $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$default` | **mixed** |  |





***

### getOrFail



```php
public getOrFail(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |




**Throws:**

- [`UndefinedValueException`](../UndefinedValueException.md)



***

### payload



```php
public payload(): array
```












***

### validate



```php
public static validate(array $payload = []): array
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$payload` | **array** |  |




**Throws:**

- [`InvalidPayloadException`](../InvalidPayloadException.md)



***

***
> Automatically generated on 2025-10-13

