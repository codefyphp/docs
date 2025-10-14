***

# HoneyPotMiddleware





* Full name: `\Codefy\Framework\Http\Middleware\Spam\HoneyPotMiddleware`
* This class implements:
[`\Psr\Http\Server\MiddlewareInterface`](../../../../../Psr/Http/Server/MiddlewareInterface.md)



## Properties


### current



```php
private static \Codefy\Framework\Http\Middleware\Spam\HoneyPotMiddleware $current
```



* This property is **static**.


***

### attrName



```php
private string $attrName
```






***

## Methods


### __construct



```php
public __construct(string $attrName = &#039;hpt_name&#039;): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attrName` | **string** |  |





***

### getField



```php
public static getField(?string $name = null, ?string $label = null): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **?string** |  |
| `$label` | **?string** |  |





***

### getHiddenField



```php
public static getHiddenField(?string $name = null): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **?string** |  |





***

### process



```php
public process(\Psr\Http\Message\ServerRequestInterface $request, \Psr\Http\Server\RequestHandlerInterface $handler): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |
| `$handler` | **\Psr\Http\Server\RequestHandlerInterface** |  |




**Throws:**

- [`Exception`](../../../../../Exception.md)



***

### isValid



```php
private isValid(\Psr\Http\Message\ServerRequestInterface $request): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***


***
> Automatically generated on 2025-10-13
