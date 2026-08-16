# ClassInfo

***

* Full name: `\Qubus\Support\ClassInfo`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**

## Methods

### reflect

ReflectionClass object.

```php
public static reflect(object|string $objectOrClass): \ReflectionClass
```

* This method is **static**.
**Parameters:**

| Parameter        | Type               | Description |
|------------------|--------------------|-------------|
| `$objectOrClass` | **object\|string** |             |

**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

***

### short

Retrieve the class's name.

```php
public static short(object|string $objectOrClass): string
```

* This method is **static**.
**Parameters:**

| Parameter        | Type               | Description |
|------------------|--------------------|-------------|
| `$objectOrClass` | **object\|string** |             |

**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

***

### name

Retrieve class's name its namespace name (i.e. Qubus\Support\ClassName).

```php
public static name(object|string $objectOrClass): string
```

* This method is **static**.
**Parameters:**

| Parameter        | Type               | Description |
|------------------|--------------------|-------------|
| `$objectOrClass` | **object\|string** |             |

**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

***

### namespace

Retrieve the namespace name of a class.

```php
public static namespace(object|string $objectOrClass): string
```

* This method is **static**.
**Parameters:**

| Parameter        | Type               | Description |
|------------------|--------------------|-------------|
| `$objectOrClass` | **object\|string** |             |

**Throws:**

- [`ReflectionException`](../../ReflectionException.md)

***
