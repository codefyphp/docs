---
title: Passwords
sidebar_title: Passwords
summary: Hash and verify CodefyPHP user passwords securely with Bcrypt or Argon2id, inspect algorithms, tune costs, and rehash outdated credentials.
keywords: php-password-hashing,argon2id,bcrypt
weight: 202
---

The `Codefy\Framework\Support\Password` class is a wrapper for PHP's native [password functions](https://www.php.net/manual/en/ref.password.php). 
`Password` provides secure `Bcrypt` and `Argon2id` hashing for storing user passwords.

## Configuration

By default, Codefy uses `Bcrypt` hashing if `Argon2id` (recommended) is not available. You can specify what algorithm your 
application should use by overriding the `password.hash.algo` filter:

```php
<?php

use Codefy\Framework\Codefy;

use const PASSWORD_ARGON2I;

Codefy::$PHP->hook->filter->addFilter(
    hook: 'password.hash.algo',
    callback: fn(string $algo) => PASSWORD_ARGON2I
);
```

## Basic Usage

### Hashing a Password

You can hash a password by calling the static method `hash`:

```php
<?php

use Codefy\Framework\Support\Password;

$password = 'd0L5u08VU!UY$proh$$2YE_ri+';

$hashedPassword = Password::hash($password);

echo $hashedPassword;
```

The above example will output something similar to:

`$argon2id$v=19$m=4096,t=2,p=2$ZGpmRXZRRjNzRW5TRlpBWQ$n674h+oL66mauWOwZ4nZ7U9PLlRsFkbU6uUlPNw00Tg`

### Verify Password

The `verify()` method verifies that the given hash matches the given password.

```php
<?php

use Codefy\Framework\Support\Password;
    
$password = 'd0L5u08VU!UY$proh$$2YE_ri+';

if(Password::verify($password, $hashedPassword)) {
    // The passwords matched
}
```

### Get Algorithm ID's

The `algos()` static method returns available password hashing algorithm IDs.

```php
<?php

use Codefy\Framework\Support\Password;

use function dd;

dd(Password::algos());
```

The above example will output something similar to:

```text
array:3 [▼
  0 => "2y"
  1 => "argon2i"
  2 => "argon2id"
]
```

### Get Info

The `getInfo()` static method returns information about the given hash.

```php
<?php

use Codefy\Framework\Support\Password;

use function dd;

$password = 'd0L5u08VU!UY$proh$$2YE_ri+';

$hashedPassword = Password::hash($password);

dd(Password::getInfo($hashedPassword));
```

The above example will output something similar to:

```text
array:3 [▼
  "algo" => "argon2id"
  "algoName" => "argon2id"
  "options" => array:3 [▼
    "memory_cost" => 4096
    "time_cost" => 2
    "threads" => 2
  ]
]
```

## Change Algorithm and Set Cost

Below is an example of changing the algorithm to `Bcrypt` from `Argon2id`, and then setting the cost.

```php
<?php

use Codefy\Framework\Codefy;
use Codefy\Framework\Support\Password;

use const PASSWORD_BCRYPT;

$password = 'd0L5u08VU!UY$proh$$2YE_ri+';

Codefy::$PHP->hook->filter->addFilter(
    hook: 'password.hash.algo',
    callback: fn(string $algo) => PASSWORD_BCRYPT
);
// algo changed from argon2id to bcrypt

Codefy::$PHP->hook->filter->addFilter(
    hook: 'password.hash.options',
    callback: fn(array $options) => ['cost' => 13]
);
// cost changed from 12 to 13

echo Password::hash($password);
```

The above example will output something similar to:

`$2y$13$Vb17pv/QnjoWZhjR83akjeORRV0EElA2e/NywTd6Nq41po9d5rgU6`

### Password Rehashing

The `needsRehash()` method allows you to determine if the algorithm used has changed since the password was hashed. 
Some applications choose to perform this check during the application's authentication process:

```php
<?php

use Codefy\Framework\Support\Password;

$password = 'd0L5u08VU!UY$proh$$2YE_ri+';

if(Password::needsRehash($hashedPassword)) {
    $hashedPassword = Password::hash($password);
}
```



