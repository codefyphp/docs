***

# Mappable





* Full name: `\Qubus\Routing\Interfaces\Mappable`


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`HTTP_METHOD_GET`|public| |&#039;GET&#039;|
|`HTTP_METHOD_POST`|public| |&#039;POST&#039;|
|`HTTP_METHOD_PUT`|public| |&#039;PUT&#039;|
|`HTTP_METHOD_PATCH`|public| |&#039;PATCH&#039;|
|`HTTP_METHOD_OPTIONS`|public| |&#039;OPTIONS&#039;|
|`HTTP_METHOD_DELETE`|public| |&#039;DELETE&#039;|
|`HTTP_METHOD_HEAD`|public| |&#039;HEAD&#039;|
|`HTTP_METHOD_TRACE`|public| |&#039;TRACE&#039;|
|`HTTP_METHOD_CONNECT`|public| |&#039;CONNECT&#039;|

## Methods


### map

Add a route to the map

```php
public map(array $verbs, string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$verbs` | **array** |  |
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### any

Add a route that responds to any HTTP method.

```php
public any(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### get

Add a route that responds to GET HTTP method

```php
public get(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### post

Add a route that responds to POST HTTP method

```php
public post(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### patch

Add a route that responds to PATCH HTTP method

```php
public patch(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### put

Add a route that responds to PUT HTTP method

```php
public put(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### delete

Add a route that responds to DELETE HTTP method

```php
public delete(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### head

Add a route that responds to HEAD HTTP method

```php
public head(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### options

Add a route that responds to OPTIONS HTTP method

```php
public options(string $uri, callable|string $callback): \Qubus\Routing\Interfaces\Routable
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$uri` | **string** |  |
| `$callback` | **callable&#124;string** |  |





***

### group

Add route group

```php
public group(array|string $params, callable $callback): self
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$params` | **array&#124;string** |  |
| `$callback` | **callable** |  |





***


***
> Automatically generated on 2025-10-13
