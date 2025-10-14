***

# Pipeline





* Full name: `\Codefy\Framework\Pipeline\Pipeline`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Codefy\Framework\Pipeline\Chainable`](./Chainable.md)
* This class is a **Final class**



## Properties


### passable

The object being passed through the pipeline.

```php
protected mixed $passable
```






***

### onFailure

The callback to be executed on failure pipeline.

```php
protected \Closure|null $onFailure
```






***

### pipes

The array of class pipes.

```php
protected array $pipes
```






***

### method

The method to call on each pipe.

```php
protected string $method
```






***

### finally

The final callback to be executed after the pipeline ends regardless of the outcome.

```php
protected \Closure|null $finally
```






***

### container



```php
protected \Qubus\Injector\ServiceContainer $container
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Injector\ServiceContainer $container): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$container` | **\Qubus\Injector\ServiceContainer** |  |





***

### send

Set the object being sent through the pipeline.

```php
public send(mixed $passable): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$passable` | **mixed** |  |





***

### through

Set the array of pipes.

```php
public through(mixed $pipes): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pipes` | **mixed** |  |





***

### pipe

Push additional pipes onto the pipeline.

```php
public pipe(callable $pipe): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pipe` | **callable** |  |





***

### via

Set the method to call on the pipes.

```php
public via(string $method): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$method` | **string** |  |





***

### then

Run the pipeline with a final destination callback.

```php
public then(\Closure $destination): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$destination` | **\Closure** |  |




**Throws:**

- [`Exception`](../../../Exception.md)

- [`Throwable`](../../../Throwable.md)



***

### thenReturn

Run the pipeline and return the result.

```php
public thenReturn(): mixed
```











**Throws:**

- [`Throwable`](../../../Throwable.md)



***

### finally

Set a final callback to be executed after the pipeline ends regardless of the outcome.

```php
public finally(\Closure $callback): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **\Closure** |  |





***

### prepareDestination

Get the final piece of the Closure onion.

```php
protected prepareDestination(\Closure $destination): \Closure
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$destination` | **\Closure** |  |





***

### carry

Get a Closure that represents a slice of the application onion.

```php
protected carry(): \Closure
```












***

### getContainer

Get the container instance.

```php
protected getContainer(): \Qubus\Injector\ServiceContainer|null
```












***

### onFailure

Set callback to be executed on failure pipeline.

```php
public onFailure(\Closure $callback): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callback` | **\Closure** |  |





***

### run

Run a single pipe.

```php
public run(string $pipe, mixed $data = true): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pipe` | **string** |  |
| `$data` | **mixed** |  |





***

### parsePipeString

Parse full pipe string to get name and parameters.

```php
protected parsePipeString(string $pipe): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$pipe` | **string** |  |





***

### pipes

Get the array of configured pipes.

```php
protected pipes(): array
```












***

### handleCarry

Handle the value returned from each pipe before passing it to the next.

```php
protected handleCarry(mixed $carry): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$carry` | **mixed** |  |





***

### handleException

Handle the given exception.

```php
protected handleException(mixed $passable, \Throwable $e): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$passable` | **mixed** |  |
| `$e` | **\Throwable** |  |




**Throws:**

- [`Throwable`](../../../Throwable.md)



***


## Inherited methods


### withTransaction

Enable transaction in pipeline.

```php
public withTransaction(): static
```












***

### beginTransaction

Begin the transaction if enabled.

```php
protected beginTransaction(): void
```











**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### commitTransaction

Commit the transaction if enabled.

```php
protected commitTransaction(): void
```











**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***

### rollbackTransaction

Rollback the transaction if enabled.

```php
protected rollbackTransaction(): void
```











**Throws:**

- [`Exception`](../../../Qubus/Exception/Exception.md)



***


***
> Automatically generated on 2025-10-13
