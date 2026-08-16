# TranslationsAware

***

* Full name: `\Qubus\Validation\Traits\TranslationsAware`

## Properties

### translations

```php
protected array $translations
```

***

## Methods

### setTranslation

Given $key and $translation to set translation

```php
public setTranslation(mixed $key, mixed $translation): void
```

**Parameters:**

| Parameter      | Type      | Description |
|----------------|-----------|-------------|
| `$key`         | **mixed** |             |
| `$translation` | **mixed** |             |

***
### setTranslations

Given $translations and set multiple translations

```php
public setTranslations(array $translations): void
```

**Parameters:**

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `$translations` | **array** |             |

***
### getTranslation

Given translation from given $key

```php
public getTranslation(string $key): string
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***
### getTranslations

Get all $translations

```php
public getTranslations(): array
```

***
