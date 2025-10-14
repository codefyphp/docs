***

# Kernel





* Full name: `\Codefy\Framework\Contracts\Http\Kernel`



## Methods


### codefy

Get the CodefyPHP application instance.

```php
public codefy(): \Codefy\Framework\Application
```












***

### handle

Handle a server request.

```php
public handle(\Psr\Http\Message\ServerRequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***

### boot

Kernel boots the application.

```php
public boot(\Psr\Http\Message\ServerRequestInterface $request): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\ServerRequestInterface** |  |





***


***
> Automatically generated on 2025-10-13
