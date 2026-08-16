# Migration

***

* Full name: `\Qubus\Expressive\Migration\Migration`

## Properties

### version

```php
protected int|string|null $version
```

***

### objectmap

```php
protected ?\ArrayAccess $objectmap
```

***

### input

```php
protected ?\Symfony\Component\Console\Input\InputInterface $input
```

***

### output

```php
protected ?\Symfony\Component\Console\Output\OutputInterface $output
```

***

### dialogHelper

```php
protected ?\Symfony\Component\Console\Helper\QuestionHelper $dialogHelper
```

***

### adapter

```php
protected ?\Qubus\Expressive\Migration\Adapter\MigrationAdapter $adapter
```

***

## Methods

### __construct

Constructor

```php
final public __construct(int|string $version): mixed
```

* This method is **final**.
**Parameters:**

| Parameter  | Type            | Description |
|------------|-----------------|-------------|
| `$version` | **int\|string** |             |

***

### init

Init.

```php
public init(): void
```

***

### up

Do the migration.

```php
public up(): void
```

***

### down

Undo the migration.

```php
public down(): void
```

***

### getAdapter

Get adapter.

```php
public getAdapter(): \Qubus\Expressive\Migration\Adapter\MigrationAdapter
```

***

### getVersion

Get Version.

```php
public getVersion(): int|string|null
```

***

### setVersion

Set version.

```php
public setVersion(int|string $version): self
```

**Parameters:**

| Parameter  | Type            | Description |
|------------|-----------------|-------------|
| `$version` | **int\|string** |             |

***

### getName

Get name.

```php
public getName(): string
```

***

### getObjectMap

Get ObjectMap.

```php
public getObjectMap(): \ArrayAccess
```

***

### setObjectMap

Set ObjectMap.

```php
public setObjectMap(\ArrayAccess $objectmap): self
```

**Parameters:**

| Parameter    | Type             | Description |
|--------------|------------------|-------------|
| `$objectmap` | **\ArrayAccess** |             |

***

### getOutput

Get Output.

```php
public getOutput(): \Symfony\Component\Console\Output\OutputInterface|null
```

***

### setOutput

Set Output.

```php
public setOutput(\Symfony\Component\Console\Output\OutputInterface $output): self
```

**Parameters:**

| Parameter | Type                                                  | Description |
|-----------|-------------------------------------------------------|-------------|
| `$output` | **\Symfony\Component\Console\Output\OutputInterface** |             |

***

### getInput

Get Input.

```php
public getInput(): \Symfony\Component\Console\Input\InputInterface|null
```

***

### setInput

Set Input.

```php
public setInput(\Symfony\Component\Console\Input\InputInterface $input): self
```

**Parameters:**

| Parameter | Type                                                | Description |
|-----------|-----------------------------------------------------|-------------|
| `$input`  | **\Symfony\Component\Console\Input\InputInterface** |             |

***

### ask

Ask for input.

```php
public ask(\Symfony\Component\Console\Question\Question $question): string
```

**Parameters:**

| Parameter   | Type                                             | Description |
|-------------|--------------------------------------------------|-------------|
| `$question` | **\Symfony\Component\Console\Question\Question** |             |

***

### get

Get something from the objectmap

```php
public get(string $key): mixed
```

**Parameters:**

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `$key`    | **string** |             |

***

### getDialogHelper

Get Dialog Helper.

```php
public getDialogHelper(): \Symfony\Component\Console\Helper\QuestionHelper|null
```

***

### setDialogHelper

Set Dialog Helper.

```php
public setDialogHelper(\Symfony\Component\Console\Helper\QuestionHelper $dialogHelper): self
```

**Parameters:**

| Parameter       | Type                                                 | Description |
|-----------------|------------------------------------------------------|-------------|
| `$dialogHelper` | **\Symfony\Component\Console\Helper\QuestionHelper** |             |

***

### schema

```php
public schema(): \Qubus\Expressive\Schema
```

***
