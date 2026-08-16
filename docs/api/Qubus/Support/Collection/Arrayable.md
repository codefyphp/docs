# Arrayable

***

* Full name: `\Qubus\Support\Collection\Arrayable`
* Parent interfaces:
  `ArrayAccess`,
  `Countable`,
  `IteratorAggregate`,
  [`\Qubus\Support\Serializable`](../Serializable.md)

## Methods

### clear

Removes all items from array instance.

```php
public clear(): void
```

***

### toArray

Returns an instance as an array.

```php
public toArray(): array
```

***

### isEmpty

Returns `true` if array is empty.

```php
public isEmpty(): bool
```

***

## Inherited methods

### serialize

```php
public serialize(): string
```

***

### unserialize

```php
public unserialize(array $data): void
```

**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$data`   | **array** |             |

***
