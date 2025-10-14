***

# SeoFactory





* Full name: `\Codefy\Framework\Support\SeoFactory`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**




## Methods


### thing



```php
public static thing(string $type, array $data = []): \Melbahja\Seo\Schema\Thing
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$type` | **string** |  |
| `$data` | **array** |  |





***

### schema



```php
public static schema(\Melbahja\Seo\Interfaces\SchemaInterface $things): \Melbahja\Seo\Schema
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$things` | **\Melbahja\Seo\Interfaces\SchemaInterface** |  |





***

### metaTags

Initialize new meta tags builder.

```php
public static metaTags(): \Melbahja\Seo\MetaTags
```



* This method is **static**.








***

### sitemap

Initialize new sitemap builder.

```php
public static sitemap(string $domain, array $options = []): \Melbahja\Seo\Sitemap
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$domain` | **string** |  |
| `$options` | **array** |  |





***

### robots

Generate robots.txt.

```php
public static robots(): \Melbahja\Seo\Robots
```



* This method is **static**.








***

### ping

Initialize new sitemap ping.

```php
public static ping(array $append = []): \Melbahja\Seo\Ping
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$append` | **array** |  |





***

### indexing

Initialize indexer.

```php
public static indexing(string $host, array $keys): \Melbahja\Seo\Indexing
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$host` | **string** |  |
| `$keys` | **array** |  |





***


***
> Automatically generated on 2025-10-13
