***

# SetCookieCollection





* Full name: `\Qubus\Http\Cookies\SetCookieCollection`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### name



```php
private ?string $name
```






***

### value



```php
private ?string $value
```






***

### expires



```php
private int $expires
```






***

### maxAge



```php
private int $maxAge
```






***

### path



```php
private ?string $path
```






***

### domain



```php
private ?string $domain
```






***

### secure



```php
private bool $secure
```






***

### httpOnly



```php
private bool $httpOnly
```






***

### sameSite



```php
private ?\Qubus\Http\Cookies\SameSite $sameSite
```






***

## Methods


### __construct



```php
private __construct(string $name, ?string $value = null): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **?string** |  |





***

### getName

Retrieve name.

```php
public getName(): string
```












***

### getValue

Retrieve value.

```php
public getValue(): ?string
```












***

### getExpires

Retrieve expiry.

```php
public getExpires(): int
```












***

### getMaxAge

Retrieve max age.

```php
public getMaxAge(): int
```












***

### getPath

Retrieve path.

```php
public getPath(): ?string
```












***

### getDomain

Retrieve domain.

```php
public getDomain(): ?string
```












***

### getSecure

Is SetCookieCollection set to secure?

```php
public getSecure(): bool
```












***

### getHttpOnly

Check if set to http only.

```php
public getHttpOnly(): bool
```












***

### getSameSite

Retrieve samesite.

```php
public getSameSite(): ?\Qubus\Http\Cookies\SameSite
```












***

### withValue

Return an instance with the provided value.

```php
public withValue(?string $value = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$value` | **?string** |  |





***

### resolveExpires



```php
private resolveExpires(\DateTimeInterface|int|string|null $expires = null): int
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$expires` | **\DateTimeInterface&#124;int&#124;string&#124;null** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### withExpires

Return an instance with the provided expiry.

```php
public withExpires(\DateTimeInterface|int|string|null $expires = null): \Qubus\Http\Cookies\SetCookieCollection
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$expires` | **\DateTimeInterface&#124;int&#124;string&#124;null** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### rememberForever



```php
public rememberForever(): self
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### expire



```php
public expire(): self
```











**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### withMaxAge

Return an instance with the provided max age.

```php
public withMaxAge(?int $maxAge = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$maxAge` | **?int** |  |





***

### withPath

Return an instance with the provided path.

```php
public withPath(?string $path = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **?string** |  |





***

### withDomain

Return an instance with the provided domain.

```php
public withDomain(?string $domain = null): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$domain` | **?string** |  |





***

### withSecure

Return an instance with/without

```php
public withSecure(bool $secure = true): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$secure` | **bool** |  |





***

### withHttpOnly



```php
public withHttpOnly(bool $httpOnly = true): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$httpOnly` | **bool** |  |





***

### withSameSite



```php
public withSameSite(\Qubus\Http\Cookies\SameSite $sameSite): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$sameSite` | **\Qubus\Http\Cookies\SameSite** |  |





***

### withoutSameSite



```php
public withoutSameSite(): self
```












***

### __toString



```php
public __toString(): string
```












***

### create



```php
public static create(string $name, ?string $value = null): self
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **?string** |  |





***

### createRememberedForever



```php
public static createRememberedForever(string $name, ?string $value = null): self
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |
| `$value` | **?string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### createExpired



```php
public static createExpired(string $name): self
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### fromSetCookieString



```php
public static fromSetCookieString(string $string): self
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |




**Throws:**

- [`TypeException`](../../Exception/Data/TypeException.md)



***

### appendFormattedDomainPartIfSet



```php
private appendFormattedDomainPartIfSet(string[] $cookieStringParts): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieStringParts` | **string[]** |  |





***

### appendFormattedPathPartIfSet



```php
private appendFormattedPathPartIfSet(string[] $cookieStringParts): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieStringParts` | **string[]** |  |





***

### appendFormattedExpiresPartIfSet



```php
private appendFormattedExpiresPartIfSet(string[] $cookieStringParts): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieStringParts` | **string[]** |  |





***

### appendFormattedMaxAgePartIfSet



```php
private appendFormattedMaxAgePartIfSet(string[] $cookieStringParts): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieStringParts` | **string[]** |  |





***

### appendFormattedSecurePartIfSet



```php
private appendFormattedSecurePartIfSet(string[] $cookieStringParts): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieStringParts` | **string[]** |  |





***

### appendFormattedHttpOnlyPartIfSet



```php
private appendFormattedHttpOnlyPartIfSet(string[] $cookieStringParts): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieStringParts` | **string[]** |  |





***

### appendFormattedSameSitePartIfSet



```php
private appendFormattedSameSitePartIfSet(string[] $cookieStringParts): string[]
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$cookieStringParts` | **string[]** |  |





***


***
> Automatically generated on 2025-10-13
