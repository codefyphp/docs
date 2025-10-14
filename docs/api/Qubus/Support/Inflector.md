***

# Inflector

Pluralize and singularize English words.



* Full name: `\Qubus\Support\Inflector`



## Properties


### uncountableWords



```php
protected static array $uncountableWords
```



* This property is **static**.


***

### pluralRules



```php
protected static array $pluralRules
```



* This property is **static**.


***

### singularRules



```php
protected static array $singularRules
```



* This property is **static**.


***

### init



```php
protected static bool $init
```



* This property is **static**.


***

## Methods


### initialize

Load any localized rulesets based on the current language configuration
If not exists, the current rules remain active

```php
public static initialize(): void
```



* This method is **static**.








***

### ordinalize

Add order suffix to numbers ex. 1st 2nd 3rd 4th 5th.

```php
public static ordinalize(int $number): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$number` | **int** | the number to ordinalize |


**Return Value:**

the ordinalized version of $number




**See Also:**

* http://snipplr.com/view/4627/a-function-to-add-a-prefix-to-numbers-ex-1st-2nd-3rd-4th-5th/ - 

***

### pluralize

Gets the plural version of the given word.

```php
public static pluralize(string $word, int $count): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$word` | **string** | the word to pluralize |
| `$count` | **int** | number of instances |


**Return Value:**

the plural version of $word




***

### singularize

Gets the singular version of the given word

```php
public static singularize(string $word): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$word` | **string** | the word to singularize |


**Return Value:**

the singular version of $word




***

### camelize

Takes a string that has words separated by underscores and turns it into
a CamelCased string.

```php
public static camelize(string $underscoredWord): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$underscoredWord` | **string** | the underscored word |


**Return Value:**

the CamelCased version of $underscoredWord




***

### underscore

Takes a CamelCased string and returns an underscore separated version.

```php
public static underscore(string $camelCasedWord): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$camelCasedWord` | **string** | the CamelCased word |


**Return Value:**

an underscore separated version of $camelCasedWord




***

### ascii

Translate string to 7-bit ASCII.

```php
public static ascii(string $str, bool $allowNonAscii = false): string
```

Only works with UTF-8.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | String to translate |
| `$allowNonAscii` | **bool** | Whether to remove non ascii |


**Return Value:**

Translated string.




***

### slugify

Converts your text to a URL-friendly title so it can be used in the URL.

```php
public static slugify(string|array $string, array $constructorOptions = [], string|array|null $onTheFlyOptions = null): string
```

Only works with UTF8 input and only outputs 7 bit ASCII characters.

* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string&#124;array** | The text to slugify. |
| `$constructorOptions` | **array** | Options that can be passed to the constructor. |
| `$onTheFlyOptions` | **string&#124;array&#124;null** | Override options that can be passed to slugify method. |


**Return Value:**

The slugified text.




***

### humanize

Turns an underscore or dash separated word and turns it into a human looking string.

```php
public static humanize(string $str, string $sep = &#039;_&#039;, bool $lowercase = true): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$str` | **string** | the word |
| `$sep` | **string** | the separator (either _ or -) |
| `$lowercase` | **bool** | lowercase string and upper case first |


**Return Value:**

the human version of given string




***

### demodulize

Takes the class name out of a modulized string.

```php
public static demodulize(string $classNameInModule): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$classNameInModule` | **string** | the modulized class |


**Return Value:**

the string without the class name




***

### denamespace

Takes the namespace off the given class name.

```php
public static denamespace(string $className): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$className` | **string** | the class name |


**Return Value:**

the string without the namespace




***

### getNamespace

Returns the namespace of the given class name.

```php
public static getNamespace(string $className): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$className` | **string** | the class name |


**Return Value:**

the string without the namespace




***

### tableize

Takes a class name and determines the table name. The table name is a
pluralized version of the class name.

```php
public static tableize(string $className): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$className` | **string** | The table name. |


**Return Value:**

The table name.




***

### wordsToUpper

Takes an underscored classname and uppercases all letters after the underscores.

```php
public static wordsToUpper(string $class, string $sep = &#039;_&#039;): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$class` | **string** | classname |
| `$sep` | **string** | separator |





***

### classify

Takes a table name and creates the class name.

```php
public static classify(string $name, bool $forceSingular = true): string
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$name` | **string** | the table name |
| `$forceSingular` | **bool** | whether to singularize the table name or not |


**Return Value:**

the class name




***

### isCountable

Checks if the given word has a plural version.

```php
public static isCountable(string $word): bool
```



* This method is **static**.




**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$word` | **string** | the word to check |


**Return Value:**

if the word is countable




***


***
> Automatically generated on 2025-10-13
