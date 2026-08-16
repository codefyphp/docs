# ApiResourceController

***

* Full name: `\Qubus\Routing\Interfaces\ApiResourceController`

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
public show(int|string $id): mixed
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

***

### store

Store a newly created resource in storage.

```php
public store(\Psr\Http\Message\RequestInterface $request): mixed
```

**Parameters:**

| Parameter  | Type                                   | Description |
|------------|----------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |             |

***

### update

Update the specified resource in storage.

```php
public update(\Psr\Http\Message\RequestInterface $request): mixed
```

**Parameters:**

| Parameter  | Type                                   | Description |
|------------|----------------------------------------|-------------|
| `$request` | **\Psr\Http\Message\RequestInterface** |             |

***

### destroy

Remove the specified resource from storage.

```php
public destroy(int|string $id): mixed
```

**Parameters:**

| Parameter | Type            | Description |
|-----------|-----------------|-------------|
| `$id`     | **int\|string** |             |

***
