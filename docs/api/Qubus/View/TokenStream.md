***

# TokenStream





* Full name: `\Qubus\View\TokenStream`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### tokens



```php
public array $tokens
```






***

### currentToken



```php
public \Qubus\View\Token $currentToken
```






***

### queue



```php
protected array $queue
```






***

### cursor



```php
protected int $cursor
```






***

### eos



```php
protected bool $eos
```






***

## Methods


### __construct



```php
public __construct(array $tokens): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tokens` | **array** |  |





***

### next



```php
public next(): \Qubus\View\Token
```












***

### look



```php
public look(int $t = 1): \Qubus\View\Token
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$t` | **int** |  |





***

### skip



```php
public skip(int $times = 1): \Qubus\View\TokenStream
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$times` | **int** |  |





***

### expect



```php
public expect(mixed $primary, mixed $secondary = null): \Qubus\View\Token
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$primary` | **mixed** |  |
| `$secondary` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### expectTokens



```php
public expectTokens(mixed $tokens): \Qubus\View\TokenStream
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$tokens` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### test



```php
public test(mixed $primary, mixed $secondary = null): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$primary` | **mixed** |  |
| `$secondary` | **mixed** |  |





***

### consume



```php
public consume(mixed $primary, mixed $secondary = null): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$primary` | **mixed** |  |
| `$secondary` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### isEOS



```php
public isEOS(): bool
```












***


***
> Automatically generated on 2025-10-13
