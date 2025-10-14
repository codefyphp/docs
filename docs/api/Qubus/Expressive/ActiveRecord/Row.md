***

# Row





* Full name: `\Qubus\Expressive\ActiveRecord\Row`



## Properties


### model



```php
protected ?\Qubus\Expressive\ActiveRecord\Model $model
```






***

## Methods


### __construct



```php
public __construct(\Qubus\Expressive\ActiveRecord\Model $model, mixed $rowObject): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$model` | **\Qubus\Expressive\ActiveRecord\Model** |  |
| `$rowObject` | **mixed** |  |





***

### __get



```php
public __get(mixed $field): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### __set



```php
public __set(mixed $field, mixed $value): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |
| `$value` | **mixed** |  |





***

### __isset



```php
public __isset(mixed $field): bool
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$field` | **mixed** |  |





***

### __call



```php
public __call(mixed $name, mixed $arguments): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **mixed** |  |
| `$arguments` | **mixed** |  |





***

### __toString



```php
public __toString(): string
```












***

### save



```php
public save(): \Qubus\Expressive\ActiveRecord\Model|int|bool|\Qubus\Expressive\QueryBuilder
```












***

### delete



```php
public delete(): bool|int|\Qubus\Expressive\QueryBuilder|null
```












***


***
> Automatically generated on 2025-10-13
