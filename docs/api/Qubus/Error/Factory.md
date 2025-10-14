***

# Factory





* Full name: `\Qubus\Error\Factory`




## Methods


### createDebugErrorHandler



```php
public static createDebugErrorHandler(string $title = &#039;QubusPHP Error&#039;): \Qubus\Error\Handlers\DebugErrorHandler
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$title` | **string** |  |





***

### createPsr3ErrorHandler



```php
public static createPsr3ErrorHandler(\Psr\Log\LoggerInterface $logger): \Qubus\Error\Handlers\Psr3ErrorHandler
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$logger` | **\Psr\Log\LoggerInterface** |  |





***

### createProductionErrorHandler



```php
public static createProductionErrorHandler(bool $displayErrors = false, bool $notifyPsr3Loggers = false, bool $notifyNativePhpLog = true): \Qubus\Error\Handlers\ProductionErrorHandler
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$displayErrors` | **bool** |  |
| `$notifyPsr3Loggers` | **bool** |  |
| `$notifyNativePhpLog` | **bool** |  |





***


***
> Automatically generated on 2025-10-13
