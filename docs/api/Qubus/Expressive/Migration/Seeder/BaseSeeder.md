# BaseSeeder

***

* Full name: `\Qubus\Expressive\Migration\Seeder\BaseSeeder`
* This class implements:
  [`\Qubus\Expressive\Migration\Seeder\Seeder`](./Seeder.md)
* This class is an **Abstract class**

## Properties

### faker

```php
protected \Faker\Generator $faker
```

***

## Methods

### __construct

```php
final public __construct(): mixed
```

* This method is **final**.
***

### withFakerSeed

Set a deterministic Faker seed

```php
public withFakerSeed(int $seed): static
```

**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$seed`   | **int** |             |

***

### call

Call another seeder

```php
protected call(string|\Qubus\Expressive\Migration\Seeder\Seeder $seeder, \Qubus\Expressive\Migration\Seeder\SeederContext $context): void
```

**Parameters:**

| Parameter  | Type                                                  | Description |
|------------|-------------------------------------------------------|-------------|
| `$seeder`  | **string\|\Qubus\Expressive\Migration\Seeder\Seeder** |             |
| `$context` | **\Qubus\Expressive\Migration\Seeder\SeederContext**  |             |

**Throws:**

- [`NotFoundExceptionInterface`](../../../../Psr/Container/NotFoundExceptionInterface.md)
- [`ContainerExceptionInterface`](../../../../Psr/Container/ContainerExceptionInterface.md)

***
