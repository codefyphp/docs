***

# Sentinel





* Full name: `\Codefy\Framework\Auth\Sentinel`



## Methods


### authenticate

Authenticates user if the user exists.

```php
public authenticate(\Psr\Http\Message\ServerRequestInterface $request): \Qubus\Http\Session\SessionEntity|null
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***

### unauthorized

If user does not exist, return an unauthorized response.

```php
public unauthorized(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***


***
> Automatically generated on 2025-10-13
