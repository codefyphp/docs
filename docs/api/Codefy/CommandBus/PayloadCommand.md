***

# PayloadCommand





* Full name: `\Codefy\CommandBus\PayloadCommand`
* Parent class: [`stdClass`](../../stdClass.md)
* This class implements:
[`\Codefy\CommandBus\Command`](./Command.md)






## Inherited methods


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

- [`UndefinedValueException`](./UndefinedValueException.md)



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

- [`InvalidPayloadException`](./InvalidPayloadException.md)



***


***
> Automatically generated on 2025-10-13
