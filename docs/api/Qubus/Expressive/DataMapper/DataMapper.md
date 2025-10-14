***

# DataMapper





* Full name: `\Qubus\Expressive\DataMapper\DataMapper`



## Methods


### findAll



```php
public findAll(string $orderBy = &#039;&#039;, array $options = []): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$orderBy` | **string** |  |
| `$options` | **array** |  |





***

### findOne



```php
public findOne(int|string $id): ?\Qubus\Expressive\DataMapper\SerializableEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***

### create



```php
public create(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |  |





***

### update



```php
public update(\Qubus\Expressive\DataMapper\SerializableEntity $entity): \Qubus\Expressive\DataMapper\SerializableEntity
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$entity` | **\Qubus\Expressive\DataMapper\SerializableEntity** |  |





***

### delete



```php
public delete(int|string $id): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$id` | **int&#124;string** |  |





***


***
> Automatically generated on 2025-10-13
