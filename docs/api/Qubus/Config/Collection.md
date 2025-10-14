***

# Collection





* Full name: `\Qubus\Config\Collection`
* Parent class: [`\Qubus\Config\Configuration`](./Configuration.md)
* This class implements:
[`\ArrayAccess`](../../ArrayAccess.md), [`\Qubus\Config\ConfigContainer`](./ConfigContainer.md)



## Properties


### container



```php
private array $container
```






***

## Methods


### factory



```php
public static factory(array|\Qubus\Config\Configuration $config): \Qubus\Config\Collection
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array&#124;\Qubus\Config\Configuration** |  |





***

### setConfigKey

Set a config

```php
public setConfigKey(string $key, mixed $value): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$value` | **mixed** |  |





***

### hasConfigKey

Checks if a key exists.

```php
public hasConfigKey(string $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### removeConfigKey



```php
public removeConfigKey(string $key): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |





***

### getConfigKey

Get a config

```php
public getConfigKey(string $key, mixed|null $default = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |
| `$default` | **mixed&#124;null** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### reset



```php
public reset(): $this
```












***

### __get



```php
public __get(string $key): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **string** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### __call



```php
public __call(mixed $key, array|null $args = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |
| `$args` | **array&#124;null** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### __isset



```php
public __isset(mixed $key): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$key` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### offsetExists



```php
public offsetExists(mixed $offset): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### offsetGet



```php
public offsetGet(mixed $offset): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |




**Throws:**

- [`TypeException`](../Exception/Data/TypeException.md)



***

### offsetSet



```php
public offsetSet(mixed $offset, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |
| `$value` | **mixed** |  |





***

### offsetUnset



```php
public offsetUnset(mixed $offset): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$offset` | **mixed** |  |





***


## Inherited methods


### __construct



```php
public __construct(array|\Qubus\Config\Configuration $config): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array&#124;\Qubus\Config\Configuration** |  |




**Throws:**

- [`PathNotFoundException`](./Path/PathNotFoundException.md)



***

### getPaths



```php
public getPaths(): \Qubus\Config\Path\PathCollection
```












***

### setPaths



```php
public setPaths(\Qubus\Config\Path\PathCollection $pathCollection): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pathCollection` | **\Qubus\Config\Path\PathCollection** |  |





***

### setEnvironment



```php
public setEnvironment(?string $environment = null): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$environment` | **?string** |  |





***

### removeEnvironment



```php
public removeEnvironment(): $this
```












***

### getEnvironment



```php
public getEnvironment(): ?string
```












***

### getDotenv



```php
public getDotenv(): ?\Dotenv\Dotenv
```












***

### setDotenv



```php
public setDotenv(\Dotenv\Dotenv $dotenv): $this
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$dotenv` | **\Dotenv\Dotenv** |  |





***


***
> Automatically generated on 2025-10-13
