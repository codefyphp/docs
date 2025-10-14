***

# Parser





* Full name: `\Qubus\View\Parser`
* This class is marked as **final** and can't be subclassed
* This class is a **Final class**



## Properties


### stream



```php
private \Qubus\View\TokenStream $stream
```






***

### extends



```php
private $extends
```






***

### blocks



```php
private array $blocks
```






***

### currentBlock



```php
private array $currentBlock
```






***

### tags



```php
private array $tags
```






***

### inForLoop



```php
private int $inForLoop
```






***

### macros



```php
private array $macros
```






***

### inMacro



```php
private bool $inMacro
```






***

### imports



```php
private array $imports
```






***

## Methods


### __construct



```php
public __construct(\Qubus\View\TokenStream $stream): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$stream` | **\Qubus\View\TokenStream** |  |





***

### parse



```php
public parse(mixed $path, mixed $class): \Qubus\View\Module
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$path` | **mixed** |  |
| `$class` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### subparse



```php
private subparse(mixed $test = null): \Qubus\View\NodeList
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$test` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseIf



```php
private parseIf(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseIfModifier



```php
private parseIfModifier(mixed $token, mixed $node): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |
| `$node` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseFor



```php
private parseFor(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseBreak



```php
private parseBreak(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseContinue



```php
private parseContinue(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseExtends



```php
private parseExtends(mixed $token): mixed
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseAssign



```php
private parseAssign(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseBlock



```php
private parseBlock(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseParent



```php
private parseParent(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseMacro



```php
private parseMacro(mixed $token): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseCall



```php
private parseCall(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseYield



```php
private parseYield(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseImport



```php
private parseImport(mixed $token): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseInclude



```php
private parseInclude(mixed $token): \Qubus\View\BaseNode
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$token` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseExpression



```php
private parseExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseConditionalExpression



```php
private parseConditionalExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseXorExpression



```php
private parseXorExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseOrExpression



```php
private parseOrExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseAndExpression



```php
private parseAndExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseNotExpression



```php
private parseNotExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseInclusionExpression



```php
private parseInclusionExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseCompareExpression



```php
private parseCompareExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseConcatExpression



```php
private parseConcatExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseJoinExpression



```php
private parseJoinExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseAddExpression



```php
private parseAddExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseSubExpression



```php
private parseSubExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseMulExpression



```php
private parseMulExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseDivExpression



```php
private parseDivExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseModExpression



```php
private parseModExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseUnaryExpression



```php
private parseUnaryExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseNegExpression



```php
private parseNegExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parsePosExpression



```php
private parsePosExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parsePrimaryExpression



```php
private parsePrimaryExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseLiteralExpression



```php
private parseLiteralExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseFunctionCallExpression



```php
private parseFunctionCallExpression(mixed $node): \Qubus\View\BaseExpression
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$node` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseArrayExpression



```php
private parseArrayExpression(): \Qubus\View\BaseExpression
```











**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parsePostfixExpression



```php
private parsePostfixExpression(mixed $node): \Qubus\View\BaseExpression
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$node` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseAttributeExpression



```php
private parseAttributeExpression(mixed $node): \Qubus\View\BaseExpression
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$node` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***

### parseFilterExpression



```php
private parseFilterExpression(mixed $node): \Qubus\View\BaseExpression
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$node` | **mixed** |  |




**Throws:**

- [`SyntaxErrorException`](./SyntaxErrorException.md)



***


***
> Automatically generated on 2025-10-13
