***

# Lexer





* Full name: `\Qubus\View\Lexer`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**


## Constants

| Constant | Visibility | Type | Value |
|:---------|:-----------|:-----|:------|
|`BLOCK_BEGIN`|public| |&#039;{%&#039;|
|`BLOCK_BEGIN_TRIM`|public| |&#039;{%-&#039;|
|`BLOCK_END`|public| |&#039;%}&#039;|
|`BLOCK_END_TRIM`|public| |&#039;-%}&#039;|
|`COMMENT_BEGIN`|public| |&#039;{#&#039;|
|`COMMENT_BEGIN_TRIM`|public| |&#039;{#-&#039;|
|`COMMENT_END`|public| |&#039;#}&#039;|
|`COMMENT_END_TRIM`|public| |&#039;-#}&#039;|
|`OUTPUT_BEGIN`|public| |&#039;{{&#039;|
|`OUTPUT_BEGIN_TRIM`|public| |&#039;{{-&#039;|
|`OUTPUT_END`|public| |&#039;}}&#039;|
|`OUTPUT_END_TRIM`|public| |&#039;-}}&#039;|
|`RAW_BEGIN`|public| |&#039;{!&#039;|
|`RAW_BEGIN_TRIM`|public| |&#039;{!-&#039;|
|`RAW_END`|public| |&#039;!}&#039;|
|`RAW_END_TRIM`|public| |&#039;-!}&#039;|
|`POSITION_TEXT`|public| |0|
|`POSITION_BLOCK`|public| |1|
|`POSITION_OUTPUT`|public| |2|
|`POSITION_RAW`|public| |3|
|`REGEX_CONSTANT`|public| |&#039;/true\b | false\b | null\b/Ax&#039;|
|`REGEX_NAME`|public| |&#039;/[a-zA-Z_][a-zA-Z0-9_]*/A&#039;|
|`REGEX_NUMBER`|public| |&#039;/[\-]?[0-9][0-9_]*(?:\.[0-9][0-9_]*)?/A&#039;|
|`REGEX_STRING`|public| |&#039;/(?:&quot;([^&quot;\\\\]*(?:\\\\.[^&quot;\\\\]*)*)&quot;|
        \&#039;([^\&#039;\\\\]*(?:\\\\.[^\&#039;\\\\]*)*)\&#039;)/Axsmu&#039;|
|`REGEX_OPERATOR`|public| |&#039;/and\b|xor\b|or\b|not\b|in\b|
        =&gt;|&lt;&gt;|&lt;=?|&gt;=?|[!=]==|[!=]?=|\.\.|[\[\]().,%*\/+|?:\-@~]/Ax&#039;|

## Properties


### source



```php
private array|string $source
```






***

### line



```php
private int $line
```






***

### char



```php
private int $char
```






***

### cursor



```php
private int $cursor
```






***

### position



```php
private int $position
```






***

### queue



```php
private array $queue
```






***

### end



```php
private int $end
```






***

### trim



```php
private bool $trim
```






***

## Methods


### __construct



```php
public __construct(mixed $source): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$source` | **mixed** |  |





***

### tokenize



```php
public tokenize(): \Qubus\View\TokenStream
```












***

### next



```php
private next(): \Qubus\View\Token
```












***

### adjustLineChar



```php
private adjustLineChar(string $string): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$string` | **string** |  |





***

### lexText



```php
private lexText(): array
```












***

### lexBlock



```php
private lexBlock(): array
```












***

### lexOutput



```php
private lexOutput(): array
```












***

### lexRaw



```php
private lexRaw(): array
```












***

### lexExpression



```php
private lexExpression(): array
```












***


***
> Automatically generated on 2025-10-13
