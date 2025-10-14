***

# BaseController





* Full name: `\Codefy\Framework\Http\BaseController`
* Parent class: [`Controller`](../../../Qubus/Routing/Controller/Controller.md)
* This class implements:
[`\Codefy\Framework\Contracts\RoutingController`](../Contracts/RoutingController.md)



## Properties


### sessionService



```php
protected \Qubus\Http\Session\SessionService $sessionService
```






***

### router



```php
protected \Qubus\Routing\Router $router
```






***

### view



```php
protected \Qubus\View\Renderer $view
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Http\Session\SessionService $sessionService, \Qubus\Routing\Router $router, \Qubus\View\Renderer $view): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sessionService` | **\Qubus\Http\Session\SessionService** |  |
| `$router` | **\Qubus\Routing\Router** |  |
| `$view` | **\Qubus\View\Renderer** |  |





***

### setView

Sets the view instance.

```php
public setView(\Qubus\View\Renderer $view): \Codefy\Framework\Http\BaseController
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$view` | **\Qubus\View\Renderer** |  |





***

### redirect

Redirects to given $url.

```php
public redirect(string $url, int $status = 302): \Psr\Http\Message\ResponseInterface|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$url` | **string** | A string. |
| `$status` | **int** | HTTP status code. Defaults to `302`. |





***


***
> Automatically generated on 2025-10-13
