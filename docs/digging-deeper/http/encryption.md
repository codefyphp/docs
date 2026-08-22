---
title: Encryption
sidebar_title: Encryption
summary: Encrypt and decrypt CodefyPHP values, cookies, and environment files with narrow cryptography contracts, managed keys, rotation, and failure handling.
keywords: php-encryption,encrypted-cookies,secret-management
weight: 13
---

# Encryption

The HTTP Component uses Defuse PHP Encryption for authenticated symmetric encryption. The
`QubusEncryption` adapter implements the package's `Encryption`,
`Encryptor`, and `Decryptor` contracts and can be injected anywhere those
interfaces are accepted.

## Generate and store a key

Generate a key once in a controlled administrative process:

```php
<?php

declare(strict_types=1);

use Defuse\Crypto\Key;

$key = Key::createNewRandomKey();
$encoded = $key->saveToAsciiSafeString();

// Send $encoded to your secret manager. Do not commit or print it in production.
```

Load it from a secret at runtime:

```php
<?php

use Defuse\Crypto\Key;
use Qubus\Http\Encryption\Adapter\QubusEncryption;

$encoded = getenv('APP_ENCRYPTION_KEY');
if (!is_string($encoded) || $encoded === '') {
    throw new RuntimeException('APP_ENCRYPTION_KEY is not configured.');
}

$encryption = new QubusEncryption(Key::loadFromAsciiSafeString($encoded));
```

Do not use a password, UUID, application name, or raw random text directly as a
Defuse key. Use Defuse's key creation and serialization methods.

## Encrypt and decrypt values

```php
<?php

$ciphertext = $encryption->encrypt('sensitive value');
$plaintext = $encryption->decrypt($ciphertext);
```

Ciphertext includes authentication. Decryption throws
`WrongKeyOrModifiedCiphertextException` when a value was modified, truncated,
or encrypted with another key. Treat this as invalid data rather than retrying
with user-controlled input.

The optional `rawBinary` argument controls Defuse's transport representation:

```php
<?php

$binaryCiphertext = $encryption->encrypt('payload', rawBinary: true);
$plaintext = $encryption->decrypt($binaryCiphertext, rawBinary: true);
```

!!!note
    Use the default ASCII-safe form for headers, configuration, JSON, and text
    storage. Raw binary is appropriate only for binary-safe storage and transport.

## Depend on the narrow contracts

Services that only write protected data should require `Encryptor`; services
that only read it should require `Decryptor`:

```php
<?php

use Qubus\Http\Encryption\Encryptor;

final readonly class TokenVault
{
    public function __construct(private Encryptor $encryptor)
    {
    }

    public function protect(string $token): string
    {
        return $this->encryptor->encrypt($token);
    }
}
```

This keeps application code independent of the concrete Defuse adapter and
makes test doubles straightforward.

## Encrypting cookies

Use `EncryptCookiesMiddleware` for a broad policy or
`ResponseCookieEncryptor` and `RequestCookieDecryptor` for selected signed and
encrypted cookie values. Complete examples and middleware-order guidance are in
[Cookies](cookies.md).

!!!note
    Cookie encryption keys should be separate from keys used for databases,
    environment files, or unrelated application data.

## Encrypted environment files

`Encryption\Env\File` encrypts an entire input file and writes the ciphertext
to an output file:

```php
<?php

use Defuse\Crypto\Key;
use Qubus\Http\Encryption\Env\File;

$key = Key::loadFromAsciiSafeString(
    trim((string) file_get_contents('/run/secrets/env-key')),
);

File::encrypt(
    input: '/srv/app/.env.plain',
    output: '/srv/app/.env.encrypted',
    key: $key,
);

$plaintext = File::decrypt('/srv/app/.env.encrypted', $key);
```

Protect the key file separately from the encrypted data. Encrypting a file is
not useful if its key is committed beside it.

`SecureEnv::parse()` decrypts an environment file and exports non-empty values
with `putenv()`:

```php
<?php

use Qubus\Http\Encryption\Env\SecureEnv;

SecureEnv::parse(
    inputFile: '/srv/app/.env.encrypted',
    keyFile: '/run/secrets/env-key',
);

$databaseHost = getenv('DATABASE_HOST');
```

The key file must contain the exact ASCII-safe Defuse key without surrounding
whitespace.

The decrypted file uses simple `KEY=value` syntax:

```dotenv
# Empty lines and comments are ignored.
APP_ENV=production
DATABASE_HOST=db.internal
MAIL_FROM="support@example.com"
```

The parser splits on the first equals sign and trims whitespace and surrounding
single/double quotes. It is intentionally small: it does not implement variable
expansion, multiline values, `export` prefixes, or shell evaluation.

## Process-scope warning

`putenv()` changes the current process environment. In PHP-FPM that state can
survive for the worker lifetime, and in Swoole it is shared by requests handled
by the same worker. Load immutable configuration during application startup,
not from request-specific data.

## Failure handling and rotation

File read/write failures raise `RuntimeException`. Invalid key formats,
environment problems, and modified ciphertext use Defuse exceptions. Catch
these at the application bootstrap boundary, fail closed, and avoid including
key material or plaintext in logs.

For key rotation, store a key identifier with encrypted application records and
support the old and new keys during a bounded migration. The basic adapter does
not embed application-level key IDs or rotate data automatically.
