# Kernel

***

* Full name: `\Codefy\Framework\Contracts\Console\Kernel`

## Methods

### handle

Handle an incoming console command.

```php
public handle(\Symfony\Component\Console\Input\InputInterface $input, \Symfony\Component\Console\Output\OutputInterface|null $output = null): int
```

**Parameters:**

| Parameter | Type                                                        | Description |
|-----------|-------------------------------------------------------------|-------------|
| `$input`  | **\Symfony\Component\Console\Input\InputInterface**         |             |
| `$output` | **\Symfony\Component\Console\Output\OutputInterface\|null** |             |

***

### all

Gets all the commands registered.

```php
public all(): \Symfony\Component\Console\Command\Command[]
```

***

### output

Get the output for the last run command.

```php
public output(): string
```

***

### bootstrap

Bootstrap the console kernel.

```php
public bootstrap(): void
```

***

### call

Run a Codex console command by name.

```php
public call(string $command, array $parameters = [], bool|\Symfony\Component\Console\Output\OutputInterface|null $outputBuffer = null): int
```

**Parameters:**

| Parameter       | Type                                                              | Description |
|-----------------|-------------------------------------------------------------------|-------------|
| `$command`      | **string**                                                        |             |
| `$parameters`   | **array**                                                         |             |
| `$outputBuffer` | **bool\|\Symfony\Component\Console\Output\OutputInterface\|null** |             |

***
