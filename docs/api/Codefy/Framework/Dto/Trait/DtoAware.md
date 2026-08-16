# DtoAware

***

* Full name: `\Codefy\Framework\Dto\Trait\DtoAware`

## Methods

### toDto

Convert validated data to DTO.

```php
public toDto(): object
```

This method creates a DTO instance using only validated data from Input Validator or Form Request.

**Return Value:**

The corresponding DTO instance.

**Throws:**

If DTO class is not found or doesn't have fromData method.
- [`RuntimeException`](../../../../RuntimeException.md)

***
### getDtoClass

Get the DTO class name for this Input Validator or Form Request.

```php
public getDtoClass(): string
```

**Return Value:**

The fully qualified DTO class name

***
### toDtoArray

Convert DTO object data to array.

```php
public toDtoArray(): array
```

***
