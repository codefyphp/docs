***

# ResourceController





* Full name: `\Qubus\Routing\Interfaces\ResourceController`



## Methods


### index

Display a listing of the resource.

```php
public index(): mixed
```












***

### show

Display the specified resource.

```php
public show(int|string $id): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***

### store

Store a newly created resource in storage.

```php
public store(\Psr\Http\Message\RequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |  |





***

### create

Show the form for creating a new resource.

```php
public create(): \Psr\Http\Message\ResponseInterface
```












***

### edit

Show the form/view for editing the specified resource.

```php
public edit(int|string $id): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***

### update

Update the specified resource in storage.

```php
public update(\Psr\Http\Message\RequestInterface $request): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |  |





***

### destroy

Remove the specified resource from storage.

```php
public destroy(int|string $id): \Psr\Http\Message\ResponseInterface
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***


***
> Automatically generated on 2025-10-13
