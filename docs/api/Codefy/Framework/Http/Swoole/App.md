***

# App





* Full name: `\Codefy\Framework\Http\Swoole\App`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### app



```php
public ?\Codefy\Framework\Application $app
```






***

### server



```php
public ?\Swoole\Http\Server $server
```






***

### serverStartTimestamp



```php
public int $serverStartTimestamp
```






***

## Methods


### __construct



```php
public __construct(?\Codefy\Framework\Application $app = null, ?\Swoole\Http\Server $server = null, int $serverStartTimestamp): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$app` | **?\Codefy\Framework\Application** |  |
| `$server` | **?\Swoole\Http\Server** |  |
| `$serverStartTimestamp` | **int** |  |





***

### init



```php
public init(callable $routesCallable): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$routesCallable` | **callable** |  |





***

### start

Starts Swoole Server

```php
public start(): void
```












***

### initRoutes



```php
private initRoutes(callable $callable): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$callable` | **callable** |  |





***


***
> Automatically generated on 2025-10-13
