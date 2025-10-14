***

# Message





* Full name: `\Qubus\Http\Cookies\Validation\Message`



## Properties


### nonce



```php
public string $nonce
```






***

### hmac



```php
public string $hmac
```






***

### value



```php
public string $value
```






***

## Methods


### __construct



```php
private __construct(string $nonce, string $hmac, string $value): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$nonce` | **string** |  |
| `$hmac` | **string** |  |
| `$value` | **string** |  |





***

### getNonce



```php
public getNonce(): string
```












***

### getHmac



```php
public getHmac(): string
```












***

### getValue



```php
public getValue(): string
```












***

### fromString



```php
public static fromString(mixed $value): \Qubus\Http\Cookies\Validation\Message
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **mixed** |  |





***


***
> Automatically generated on 2025-10-13
