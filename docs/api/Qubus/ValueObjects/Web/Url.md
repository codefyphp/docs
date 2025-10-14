***

# Url





* Full name: `\Qubus\ValueObjects\Web\Url`
* This class implements:
[`\Qubus\ValueObjects\ValueObject`](../ValueObject.md)



## Properties


### scheme



```php
protected \Qubus\ValueObjects\Web\SchemeName $scheme
```






***

### user



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $user
```






***

### password



```php
protected \Qubus\ValueObjects\StringLiteral\StringLiteral $password
```






***

### domain



```php
protected \Qubus\ValueObjects\Web\Domain $domain
```






***

### port



```php
protected \Qubus\ValueObjects\Web\PortNumber $port
```






***

### path



```php
protected \Qubus\ValueObjects\Web\Path $path
```






***

### queryString



```php
protected \Qubus\ValueObjects\Web\UrlQueryString $queryString
```






***

### fragmentIdentifier



```php
protected \Qubus\ValueObjects\Web\UrlFragmentIdentifier $fragmentIdentifier
```






***

## Methods


### __construct

Returns a new Url object.

```php
public __construct(\Qubus\ValueObjects\Web\SchemeName $scheme, \Qubus\ValueObjects\StringLiteral\StringLiteral $user, \Qubus\ValueObjects\StringLiteral\StringLiteral $password, \Qubus\ValueObjects\Web\Domain $domain, \Qubus\ValueObjects\Web\PortNumber $port, \Qubus\ValueObjects\Web\Path $path, \Qubus\ValueObjects\Web\UrlQueryString $queryString, \Qubus\ValueObjects\Web\UrlFragmentIdentifier $fragmentIdentifier): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$scheme` | **\Qubus\ValueObjects\Web\SchemeName** |  |
| `$user` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$password` | **\Qubus\ValueObjects\StringLiteral\StringLiteral** |  |
| `$domain` | **\Qubus\ValueObjects\Web\Domain** |  |
| `$port` | **\Qubus\ValueObjects\Web\PortNumber** |  |
| `$path` | **\Qubus\ValueObjects\Web\Path** |  |
| `$queryString` | **\Qubus\ValueObjects\Web\UrlQueryString** |  |
| `$fragmentIdentifier` | **\Qubus\ValueObjects\Web\UrlFragmentIdentifier** |  |





***

### __toString

Returns a string representation of the url.

```php
public __toString(): string
```












***

### fromNative

Returns a new Url object from a native url string.

```php
public static fromNative(): \Qubus\ValueObjects\Web\Url|\Qubus\ValueObjects\ValueObject
```



* This method is **static**.







**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### equals

Tells whether two Url are equals by comparing their components.

```php
public equals(\Qubus\ValueObjects\Web\Url|\Qubus\ValueObjects\ValueObject $url): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$url` | **\Qubus\ValueObjects\Web\Url&#124;\Qubus\ValueObjects\ValueObject** |  |





***

### getDomain

Returns the domain of the Url.

```php
public getDomain(): \Qubus\ValueObjects\Web\Domain
```












***

### getFragmentIdentifier

Returns the fragment identifier of the Url.

```php
public getFragmentIdentifier(): \Qubus\ValueObjects\Web\UrlFragmentIdentifier
```












***

### getPassword

Returns the password part of the Url.

```php
public getPassword(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***

### getPath

Returns the path of the Url.

```php
public getPath(): \Qubus\ValueObjects\Web\Path
```












***

### getPort

Returns the port of the Url.

```php
public getPort(): \Qubus\ValueObjects\Web\PortNumber
```












***

### getQueryString

Returns the query string of the Url.

```php
public getQueryString(): \Qubus\ValueObjects\Web\UrlQueryString
```












***

### getScheme

Returns the scheme of the Url.

```php
public getScheme(): \Qubus\ValueObjects\Web\SchemeName
```












***

### getUser

Returns the user part of the Url.

```php
public getUser(): \Qubus\ValueObjects\StringLiteral\StringLiteral
```












***


***
> Automatically generated on 2025-10-13
