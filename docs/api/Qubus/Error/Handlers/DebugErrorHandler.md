***

# DebugErrorHandler





* Full name: `\Qubus\Error\Handlers\DebugErrorHandler`
* This class is marked as **final** and can't be subclassed
* This class implements:
[`\Qubus\Error\Handlers\ErrorHandler`](./ErrorHandler.md)
* This class is a **Final class**



## Properties


### whoops



```php
public \Whoops\Run $whoops
```






***

### title



```php
private string $title
```






***

## Methods


### __construct

Catch errors and exceptions and execute the method.

```php
public __construct(string $title = &#039;QubusPHP Error&#039;): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$title` | **string** |  |





***

### registerErrorHandler

Handle error catch.

```php
public registerErrorHandler(): void
```












***

### registerHandler



```php
protected registerHandler(): void
```












***


***
> Automatically generated on 2025-10-13
