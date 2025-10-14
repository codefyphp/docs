***

# MessageTranslatorAware





* Full name: `\Qubus\Validation\Traits\MessageTranslatorAware`



## Properties


### messages



```php
protected array $messages
```






***

## Methods


### __construct



```php
public __construct(array $messages = []): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$messages` | **array** |  |





***

### trans

Translate a string.

```php
public trans(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** | Key to be spliced. |





***

### arrayGet

Use dot(.) string.

```php
protected arrayGet(array $array, string|null $key, mixed|null $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$array` | **array** |  |
| `$key` | **string&#124;null** |  |
| `$default` | **mixed&#124;null** |  |





***

***
> Automatically generated on 2025-10-13

