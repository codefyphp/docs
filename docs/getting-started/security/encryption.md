---
title: Encryption
sidebar_title: Encryption
summary: Encrypt and decrypt sensitive CodefyPHP values with OpenSSL-backed AES encryption, authenticated MAC signatures, and generated application keys.
keywords: codefyphp-encryption,aes-encryption,authenticated-encryption
weight: 201
---

Codefy provides encryption and decryption of text via OpenSSL using AES-256 and AES-128 encryption. All encrypted values 
are signed using a message authentication code (MAC) to ensure encrypted values are neither modified nor tampered with.

Encryption is used in the application to encrypt/decrypt cookies. You can use encryption in other areas, but it is left 
to the developer to use it where he/she/they see fit. The best use case is to encrypt API keys or secret keys, 
especially those saved in a database. It is **not** recommended to use encryption for user passwords, 
that is best handled with [password hashing](passwords.md).

## Configuration

Before using encryption, you must set the `crypto_key` configuration option in your `./config/app.php` file. 
`crypto_key` actually pulls the key data from a file that you must generate. To generate the key file, run the 
following command.

```shell
php codex generate:key:file
```

You should not need to change/update this key once its set. But if you do end up 
changing the key, the change will make all cookies, including session cookies null and void.

## Encrypting a Value

You may encrypt a value using the `encrypt()` method provided by `Qubus\Http\Encryption\Adapter\QubusEncryption`.

    <?php
    
    use Defuse\Crypto\Key;
    use Qubus\Http\Encryption\Adapter\QubusEncryption;

    use function Codefy\Framework\Helpers\config;
    
    $key = config(key: 'app.crypto_key');
    $crypt = new QubusEncryption(key: Key::loadFromAsciiSafeString(saved_key_string: $key));
    
    $crypt->encrypt(value: 'Hello World!');
    // Similar result: def50200936879a278febf9d9f5bd90772a10f2e52f469fb584d05a941669e0139b439324a5dd5dd902c4b8382ef98a738344f5194f3b2db408fa4ed35260b400ec15b1cab9e9508a788b0a60558305bb7acc55689406d73182d622bd527c413

## Decrypting a Value

You may decrypt a value using the `decrypt()` method provided by `Qubus\Http\Encryption\Adapter\QubusEncryption`.

    <?php
    
    use Defuse\Crypto\Key;
    use Qubus\Http\Encryption\Adapter\QubusEncryption;
    
    $key = config(key: 'app.crypto_key');
    $crypt = new QubusEncryption(key: Key::loadFromAsciiSafeString(saved_key_string: $key));

    $encryptedText = "def50200936879a278febf9d9f5bd90772a10f2e52f469fb584d05a941669e0139b439324a5dd5dd902c4b8382ef98a738344f5194f3b2db408fa4ed35260b400ec15b1cab9e9508a788b0a60558305bb7acc55689406d73182d622bd527c413"
    
    $crypt->decrypt(value: $text);
    // result: Hello World!




