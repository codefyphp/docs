# Chainable

***

* Full name: `\Codefy\Framework\Pipeline\Chainable`

## Methods

### send

Set the object being sent through the pipeline.

```php
public send(mixed $passable): self
```

**Parameters:**

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `$passable` | **mixed** |             |

***

### through

Set the array of pipes.

```php
public through(mixed $pipes): self
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$pipes`  | **mixed** |             |

***

### via

Set the method to call on the pipes.

```php
public via(string $method): self
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$method` | **string** |             |

***

### then

Run the pipeline with a final destination callback.

```php
public then(\Closure $destination): mixed
```

**Parameters:**

| Parameter      | Type         | Description |
|----------------|--------------|-------------|
| `$destination` | **\Closure** |             |

***

### thenReturn

Run the pipeline and return the result.

```php
public thenReturn(): mixed
```

***

### run

Run a single pipe.

```php
public run(class-string $pipe, mixed $data = true): mixed
```

**Parameters:**

| Parameter | Type             | Description |
|-----------|------------------|-------------|
| `$pipe`   | **class-string** |             |
| `$data`   | **mixed**        |             |

***
