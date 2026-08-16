---
title: Firewall
sidebar_title: Firewall
weight: 203
---

The CodefyPHP Firewall inspects incoming HTTP requests for common attack patterns, including SQL injection, cross-site scripting, remote code execution, file traversal, server-side request forgery, sensitive-file probes, PHP-file probes, and automated scanner activity.

When a threat is detected, the firewall can:

1. Log the threat.
2. Notify one or more external services.
3. Block the request.
4. Allow the request to continue when operating in monitoring-only mode.

The firewall is implemented as PSR-15 middleware and runs before the application request handler.

## Configuration

Create or update the firewall configuration file:

```text
./config/firewall.php
```

A complete configuration may look like this:

```php title="./config/firewall.php"
<?php

declare(strict_types=1);

use Application\Security\EmailThreatNotifier;

return [
    /*
     * Enable or disable firewall request inspection.
     *
     * When disabled, requests are passed directly to the next middleware
     * or request handler without being inspected.
     */
    'enabled' => true,

    /*
     * Block detected threats.
     *
     * Set this to false to use the firewall in monitoring-only mode.
     * Threats are still logged and may still trigger notifications.
     */
    'block' => true,

    /*
     * Include request query and parsed body data in threat logs.
     *
     * Request payloads may contain passwords, API tokens, personal data,
     * payment information, or other sensitive values.
     */
    'log_payload' => false,

    /*
     * Minimum severity required before notifications are sent.
     *
     * Supported values:
     *
     * low
     * medium
     * high
     * critical
     */
    'alert_min_severity' => 'high',

    /*
     * Associative entries configure named notifiers.
     *
     * Numeric entries containing ThreatNotifier objects provide
     * backwards compatibility with the legacy notifier format.
     */
    'notifiers' => [
        'email' => [
            'enabled' => true,
        ],

        'slack' => [
            'enabled' => false,
        ],

        /*
         * Legacy notifier registration remains supported.
         */
        new EmailThreatNotifier(),
    ],

    /*
     * Request paths that bypass firewall inspection.
     */
    'ignored_paths' => [
        '/favicon.ico',
        '/robots.txt',
        '/health',
    ],

    /*
     * Configure built-in and application-specific threat rules.
     */
    'rules' => [
        'sql_injection' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'xss' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'rce' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'file_traversal' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'ssrf' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'scanner_path_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'sensitive_file_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'php_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'wordpress_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],
    ],

    /*
     * Legacy rule additions.
     *
     * These remain supported for backwards compatibility.
     * New applications should use rules.<group>.add.
     */
    'sql_injection' => [],
    'xss' => [],
    'rce' => [],
    'file_traversal' => [],
    'ssrf' => [],
    'scanner_path_probe' => [],
    'sensitive_file_probe' => [],
    'php_probe' => [],
];
```

## How It Works

For every incoming HTTP request, the firewall middleware:

1. Checks whether the firewall is enabled.
2. Checks whether the request path is ignored.
3. Inspects supported request values for known threat patterns.
4. Returns the first matching threat that has not been excluded.
5. Logs the detected threat.
6. Sends notifications when the severity threshold is met.
7. Blocks the request when blocking is enabled.

If no threat is detected, the request is passed to the next middleware or request handler.

## Monitoring-Only Mode

The firewall can inspect requests without blocking them.

```php
return [
    'enabled' => true,
    'block' => false,
];
```

In monitoring-only mode, the firewall still:

- Detects threats
- Logs threats
- Evaluates notification severity
- Sends enabled notifications

It only skips the blocked response and allows the request to continue.

Monitoring-only mode is useful when introducing the firewall to an existing application because it allows you to identify false positives before enforcing blocking.

A recommended rollout process is:

1. Enable the firewall.
2. Set `block` to `false`.
3. Review logged threats.
4. Test application forms, APIs, editors, uploads, and import workflows.
5. Add narrowly scoped rule adjustments or ignored paths.
6. Set `block` to `true`.

## Threat Severity

The firewall supports the following severity levels:

```text
low
medium
high
critical
```

Severity ranking is:

| Severity   | Rank |
|------------|-----:|
| `low`      |    1 |
| `medium`   |    2 |
| `high`     |    3 |
| `critical` |    4 |

The `alert_min_severity` setting controls notification delivery.

```php
'alert_min_severity' => 'high',
```

With this setting, notifications are sent for:

```text
high
critical
```

Notifications are not sent for:

```text
low
medium
```

An unsupported `alert_min_severity` value falls back to `high`.

An unsupported threat severity is ranked below all supported values and does not trigger a notification.

The severity setting affects notifications only. It does not determine whether a threat is blocked.

## Ignored Paths

Use `ignored_paths` to bypass firewall inspection for specific request paths.

```php
'ignored_paths' => [
    '/favicon.ico',
    '/robots.txt',
    '/health',
],
```

Paths are normalized before comparison.

Ignoring:

```text
/health
```

also ignores descendant paths such as:

```text
/health/database
/health/cache
```

It does not ignore unrelated paths that only share the same prefix:

```text
/healthcare
```

Ignoring `/` only ignores the root path. It does not disable the firewall for the entire application.

Be conservative when adding ignored paths. An ignored route bypasses all firewall inspection.

## Threat Groups

### SQL Injection

Detects common SQL injection expressions and query fragments.

Examples include:

```text
' UNION SELECT * FROM users--
```

```text
1 OR 1=1
```

```text
admin'--
```

### Cross-Site Scripting

Detects common script and HTML injection attempts.

Examples include:

```html
<script>alert(1)</script>
```

```html
<img src=x onerror=alert(1)>
```

### Remote Code Execution

Detects expressions commonly associated with command execution.

Examples include:

```text
system('id')
```

```text
exec('whoami')
```

```text
shell_exec('ls -la')
```

### File Traversal

Detects attempts to move outside an expected directory.

Examples include:

```text
../../etc/passwd
```

```text
..\..\windows\system32
```

```text
%2e%2e%2fetc%2fpasswd
```

File traversal rules should primarily identify traversal mechanisms such as:

```text
../
..\
```

Sensitive destination filenames are generally classified separately as sensitive-file probes.

### Server-Side Request Forgery

Detects attempts to make the application access local, private, or restricted network resources.

Examples may include:

```text
127.0.0.1
```

```text
0.0.0.0
```

```text
169.254.169.254
```

```text
file:///etc/passwd
```

Applications that legitimately accept URLs, hostnames, or network addresses should test those workflows carefully for false positives.

### Scanner Path Probe

Detects common paths requested by automated vulnerability scanners.

Examples may include:

```text
/.git/config
```

```text
/vendor/phpunit/
```

```text
/cgi-bin/
```

### Sensitive File Probe

Detects direct requests for files that should not normally be publicly accessible.

Examples include:

```text
/.env
```

```text
/composer.json
```

```text
/id_rsa
```

```text
/credentials.json
```

### PHP Probe

Detects requests for suspicious or commonly probed PHP scripts.

Examples may include:

```text
/shell.php
```

```text
/phpinfo.php
```

```text
/adminer.php
```

### WordPress Probe

Detects WordPress-specific paths commonly requested by automated scanners.

Examples may include:

```text
/wp-login.php
```

```text
/wp-admin/
```

```text
/wp-content/
```

This can help identify automated probing when the application does not use WordPress.

## Customizing Rules

The recommended rule configuration format is:

```php
'rules' => [
    'group_name' => [
        'add' => [],
        'remove' => [],
        'replace' => [],
    ],
],
```

### Adding Rules

Use `add` to append custom rules while retaining the built-in rules.

For a regex-based threat group:

```php
'rules' => [
    'sql_injection' => [
        'add' => [
            '/custom\s+sql\s+expression/i',
        ],
    ],
],
```

For a value-based probe group:

```php
'rules' => [
    'sensitive_file_probe' => [
        'add' => [
            'custom-secret.json',
            'private-credentials.yml',
        ],
    ],
],
```

Value-based entries are escaped by the firewall when their regular expressions are created.

Use the raw filename or path value:

```php
'add' => [
    'custom-secret.json',
],
```

Do not pre-escape the value:

```php
'add' => [
    'custom\-secret\.json',
],
```

### Removing Rules

Use `remove` to remove a built-in or custom rule.

```php
'rules' => [
    'sensitive_file_probe' => [
        'remove' => [
            'composer.json',
        ],
    ],
],
```

Removal uses exact configured values.

The value in `remove` must match the original rule value exactly.

```php
'rules' => [
    'sensitive_file_probe' => [
        'add' => [
            'custom-secret.json',
        ],

        'remove' => [
            'custom-secret.json',
        ],
    ],
],
```

### Replacing Rules

Use `replace` when the application should use a completely custom rule set for a threat group.

```php
'rules' => [
    'php_probe' => [
        'replace' => [
            'internal-debug.php',
            'temporary-console.php',
        ],
    ],
],
```

When `replace` contains values, the built-in rules for that group are replaced.

Avoid combining `replace` with legacy additions unless the resulting merge behavior is intentional.

### Rule Processing Order

The effective rule list is assembled from:

1. Built-in rules, or `replace` rules when provided
2. Legacy top-level additions
3. Values in `rules.<group>.add`
4. Values removed by `rules.<group>.remove`
5. Duplicate removal

A value in `remove` can therefore remove a matching rule regardless of whether it came from:

- The framework defaults
- A legacy configuration entry
- A new `add` entry

## Legacy Rule Configuration

Earlier versions added custom rules through top-level keys:

```php
return [
    'sql_injection' => [
        '/custom-pattern/i',
    ],

    'sensitive_file_probe' => [
        'custom-secret.json',
    ],
];
```

This format remains supported for backwards compatibility.

New applications should use:

```php
return [
    'rules' => [
        'sql_injection' => [
            'add' => [
                '/custom-pattern/i',
            ],
        ],

        'sensitive_file_probe' => [
            'add' => [
                'custom-secret.json',
            ],
        ],
    ],
];
```

### Legacy Versus New Rule Configuration

| Capability                       | Legacy configuration | New configuration |
|----------------------------------|----------------------|-------------------|
| Add rules                        | Yes                  | Yes               |
| Remove built-in rules            | No                   | Yes               |
| Replace a complete group         | No                   | Yes               |
| Explicit operation names         | No                   | Yes               |
| Recommended for new applications | No                   | Yes               |

## Logging

Every detected threat is passed to the configured implementation of:

```php
Codefy\Framework\Security\Firewall\ThreatLogger
```

`ThreatLogger` is an interface.

Its contract is:

```php
public function log(
    ServerRequestInterface $request,
    ThreatMatch $match
): void;
```

A `ThreatMatch` contains information about the detected threat, such as:

- Threat group
- Threat type
- Severity
- Confidence
- Matching pattern
- Matching value
- Request source
- Input field
- Exclusion state

## Database Logger Example

### Create the Log Table

```sql
CREATE TABLE threat_logs (
    threat_id CHAR(36) PRIMARY KEY,
    ip_address VARCHAR(45) NOT NULL,
    method VARCHAR(10) NOT NULL,
    url TEXT NOT NULL,
    user_agent TEXT NULL,
    threat_group VARCHAR(64) NOT NULL,
    threat_type VARCHAR(64) NOT NULL,
    severity VARCHAR(20) NOT NULL,
    confidence_score DECIMAL(5, 2) NOT NULL DEFAULT 0.00,
    matched_source VARCHAR(64) NULL,
    matched_field VARCHAR(128) NULL,
    matched_pattern TEXT NULL,
    matched_value LONGTEXT NULL,
    request_payload LONGTEXT NULL,
    created_at DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP
);
```

### Implement `ThreatLogger`

```php
<?php

declare(strict_types=1);

namespace Application\Security;

use Codefy\Framework\Security\Firewall\ThreatLogger;
use Codefy\Framework\Security\Firewall\ThreatMatch;
use JsonException;
use PDO;
use Psr\Http\Message\ServerRequestInterface;
use Qubus\ValueObjects\Identity\Ulid;

final readonly class PdoThreatLogger implements ThreatLogger
{
    public function __construct(
        private PDO $pdo,
        private bool $logPayload = false,
    ) {
    }

    /**
     * @throws JsonException
     */
    public function log(
        ServerRequestInterface $request,
        ThreatMatch $match
    ): void {
        $statement = $this->pdo->prepare(
            <<<'SQL'
            INSERT INTO threat_logs (
                threat_id,
                ip_address,
                method,
                url,
                user_agent,
                threat_group,
                threat_type,
                severity,
                confidence_score,
                matched_source,
                matched_field,
                matched_pattern,
                matched_value,
                request_payload,
                created_at
            ) VALUES (
                :threat_id,
                :ip_address,
                :method,
                :url,
                :user_agent,
                :threat_group,
                :threat_type,
                :severity,
                :confidence_score,
                :matched_source,
                :matched_field,
                :matched_pattern,
                :matched_value,
                :request_payload,
                CURRENT_TIMESTAMP
            )
            SQL
        );

        $statement->execute([
            'threat_id' => Ulid::generateAsString(),
            'ip_address' => $this->ipAddress($request),
            'method' => $request->getMethod(),
            'url' => (string) $request->getUri(),
            'user_agent' => $request->getHeaderLine('User-Agent'),
            'threat_group' => $match->group,
            'threat_type' => $match->type,
            'severity' => $match->severity,
            'confidence_score' => $match->confidence,
            'matched_source' => $match->source,
            'matched_field' => $match->field,
            'matched_pattern' => $match->pattern,
            'matched_value' => $match->value,
            'request_payload' => $this->payload($request),
        ]);
    }

    /**
     * @throws JsonException
     */
    private function payload(
        ServerRequestInterface $request
    ): ?string {
        if (! $this->logPayload) {
            return null;
        }

        return json_encode(
            value: [
                'query' => $request->getQueryParams(),
                'body' => $request->getParsedBody(),
            ],
            flags: JSON_THROW_ON_ERROR
        );
    }

    private function ipAddress(
        ServerRequestInterface $request
    ): string {
        $server = $request->getServerParams();

        return $server['HTTP_CF_CONNECTING_IP']
            ?? $server['HTTP_X_FORWARDED_FOR']
            ?? $server['REMOTE_ADDR']
            ?? '0.0.0.0';
    }
}
```

### Register the Logger

Register the custom logger in the application firewall service provider:

```php
<?php

declare(strict_types=1);

namespace Application\Provider;

use Application\Security\PdoThreatLogger;
use Codefy\Framework\Security\Firewall\ThreatLogger;
use Codefy\Framework\Support\CodefyServiceProvider;

final class FirewallServiceProvider extends CodefyServiceProvider
{
    public function register(): void
    {
        $this->codefy->singleton(
            ThreatLogger::class,
            function (): ThreatLogger {
                return new PdoThreatLogger(
                    pdo: $this->codefy
                        ->getDbConnection()
                        ->pdo,
                    logPayload: $this->codefy
                        ->configContainer
                        ->boolean(
                            key: 'firewall.log_payload',
                            default: false
                        )
                );
            }
        );
    }
}
```

The exact database connection accessor may differ depending on the application.

## Payload Logging Warning

When `log_payload` is enabled, the logger may store:

- Passwords
- Authentication tokens
- API keys
- Session-related values
- Email addresses
- Private form submissions
- Personal data
- Payment-related values

Do not enable complete payload logging in production without considering:

- Field redaction
- Access controls
- Encryption
- Data-retention policies
- Privacy requirements
- Regulatory requirements

### Redactor

A logger can recursively redact known fields before storing a payload. For redaction, you will need to implement something 
similar to the following:

```php
<?php

declare(strict_types=1);

namespace Application\Security;

use function is_array;
use function is_object;
use function is_string;
use function strtolower;

final readonly class SensitiveDataRedactor
{
    private const string REDACTED_VALUE = '[REDACTED]';

    /**
     * @var array<string, true>
     */
    private array $sensitiveKeys;

    /**
     * @param list<string> $sensitiveKeys
     */
    public function __construct(array $sensitiveKeys = [])
    {
        $keys = $sensitiveKeys !== []
            ? $sensitiveKeys
            : self::defaultSensitiveKeys();

        $normalizedKeys = [];

        foreach ($keys as $key) {
            $normalizedKeys[$this->normalizeKey($key)] = true;
        }

        $this->sensitiveKeys = $normalizedKeys;
    }

    /**
     * Redact sensitive values recursively.
     */
    public function redact(mixed $value): mixed
    {
        if (is_array($value)) {
            return $this->redactArray($value);
        }

        if (is_object($value)) {
            return $this->redactArray(
                get_object_vars($value)
            );
        }

        return $value;
    }

    /**
     * @param array<array-key, mixed> $values
     *
     * @return array<array-key, mixed>
     */
    private function redactArray(array $values): array
    {
        foreach ($values as $key => $value) {
            if (
                is_string($key)
                && $this->isSensitiveKey($key)
            ) {
                $values[$key] = self::REDACTED_VALUE;

                continue;
            }

            $values[$key] = $this->redact($value);
        }

        return $values;
    }

    private function isSensitiveKey(string $key): bool
    {
        return isset(
            $this->sensitiveKeys[
                $this->normalizeKey($key)
            ]
        );
    }

    private function normalizeKey(string $key): string
    {
        return strtolower($key);
    }

    /**
     * @return list<string>
     */
    private static function defaultSensitiveKeys(): array
    {
        return [
            'password',
            'password_confirmation',
            'current_password',
            'new_password',
            'confirm_password',
            'passwd',
            'passphrase',
            'secret',
            'client_secret',
            'api_secret',
            'api_key',
            'apikey',
            'token',
            'access_token',
            'refresh_token',
            'auth_token',
            'authorization',
            'cookie',
            'session',
            'session_id',
            'csrf_token',
            '_token',
            'credit_card',
            'card_number',
            'card_cvc',
            'card_cvv',
            'cvv',
            'cvc',
            'pin',
            'private_key',
        ];
    }
}
```

This implementation:

* Redacts nested arrays recursively.
* Converts objects to arrays before inspecting them.
* Matches sensitive keys case-insensitively.
* Preserves non-sensitive values unchanged.
* Replaces complete sensitive values rather than partially masking them.
* Allows the default key list to be replaced through dependency injection.

```php
<?php

declare(strict_types=1);

namespace Application\Security;

use Application\Security\SensitiveDataRedactor;
use Codefy\Framework\Security\Firewall\ThreatLogger;
use Codefy\Framework\Security\Firewall\ThreatMatch;
use JsonException;
use PDO;
use Psr\Http\Message\ServerRequestInterface;
use Qubus\ValueObjects\Identity\Ulid;

final readonly class PdoThreatLogger implements ThreatLogger
{
    public function __construct(
        private PDO $pdo,
        private SensitiveDataRedactor $redactor,
        private bool $logPayload = false,
    ) {
    }

    /**
     * @throws JsonException
     */
    public function log(ServerRequestInterface $request, ThreatMatch $match): void
    {
        $statement = $this->pdo->prepare(
            <<<'SQL'
            INSERT INTO threat_logs (
                threat_id,
                ip_address,
                method,
                url,
                user_agent,
                threat_group,
                threat_type,
                severity,
                confidence_score,
                matched_source,
                matched_field,
                matched_pattern,
                matched_value,
                request_payload,
                created_at
            ) VALUES (
                :threat_id,
                :ip_address,
                :method,
                :url,
                :user_agent,
                :threat_group,
                :threat_type,
                :severity,
                :confidence_score,
                :matched_source,
                :matched_field,
                :matched_pattern,
                :matched_value,
                :request_payload,
                CURRENT_TIMESTAMP
            )
            SQL
        );

        $statement->execute([
            'threat_id' => Ulid::generateAsString(),
            'ip_address' => $this->ipAddress($request),
            'method' => $request->getMethod(),
            'url' => (string) $request->getUri(),
            'user_agent' => $request->getHeaderLine('User-Agent'),
            'threat_group' => $match->group,
            'threat_type' => $match->type,
            'severity' => $match->severity,
            'confidence_score' => $match->confidence,
            'matched_source' => $match->source,
            'matched_field' => $match->field,
            'matched_pattern' => $match->pattern,
            'matched_value' => $this->redactMatchedValue($match),
            'request_payload' => $this->payload($request),
        ]);
    }

    /**
     * @throws JsonException
     */
    private function payload(ServerRequestInterface $request): ?string
    {
        if (! $this->logPayload) {
            return null;
        }

        $payload = [
            'query' => $request->getQueryParams(),
            'body' => $request->getParsedBody(),
        ];

        return json_encode(
            value: $this->redactor->redact($payload),
            flags: JSON_THROW_ON_ERROR
        );
    }

    private function redactMatchedValue(ThreatMatch $match): mixed
    {
        if ($match->field === null) {
            return $match->value;
        }

        $redacted = $this->redactor->redact([
            $match->field => $match->value,
        ]);

        return $redacted[$match->field] ?? $match->value;
    }

    private function ipAddress(ServerRequestInterface $request): string
    {
        $server = $request->getServerParams();

        return $server['HTTP_CF_CONNECTING_IP']
            ?? $server['HTTP_X_FORWARDED_FOR']
            ?? $server['REMOTE_ADDR']
            ?? '0.0.0.0';
    }
}
```

This redacts both:

* The complete logged request payload.
* `ThreatMatch::$value` when the matching field itself is sensitive.

For example, if a threat is detected in a `password` field, the logger will not store the original password as 
`matched_value`.

```php title="./config/firewall.php"
return [
    'enabled' => true,

    'block' => true,

    'log_payload' => false,

    'redact_fields' => [
        'password',
        'password_confirmation',
        'current_password',
        'new_password',
        'secret',
        'client_secret',
        'api_key',
        'token',
        'access_token',
        'refresh_token',
        'authorization',
        'cookie',
        'session_id',
        'csrf_token',
        '_token',
        'credit_card',
        'card_number',
        'card_cvc',
        'card_cvv',
        'cvv',
        'cvc',
        'pin',
        'private_key',
    ],

    // Other firewall configuration...
];
```

Passing this list to the redactor replaces its default list. This makes the configured list the single source of 
truth for that application.

```php
<?php

declare(strict_types=1);

namespace Application\Provider;

use Application\Security\PdoThreatLogger;
use Application\Security\SensitiveDataRedactor;
use Codefy\Framework\Security\Firewall\ThreatLogger;
use Codefy\Framework\Support\CodefyServiceProvider;

final class FirewallServiceProvider extends CodefyServiceProvider
{
    public function register(): void
    {
        $this->codefy->singleton(
            SensitiveDataRedactor::class,
            function (): SensitiveDataRedactor {
                return new SensitiveDataRedactor(
                    sensitiveKeys: $this->codefy
                        ->configContainer
                        ->array(
                            key: 'firewall.redact_fields',
                            default: []
                        )
                );
            }
        );

        $this->codefy->singleton(
            ThreatLogger::class,
            function (): ThreatLogger {
                return new PdoThreatLogger(
                    pdo: $this->codefy
                        ->getDbConnection()
                        ->pdo,
                    redactor: $this->codefy->make(
                        SensitiveDataRedactor::class
                    ),
                    logPayload: $this->codefy
                        ->configContainer
                        ->boolean(
                            key: 'firewall.log_payload',
                            default: false
                        )
                );
            }
        );
    }
}
```

### Redactor Tests

If you implement the redactor, you may want to run some tests to make sure things are working properly. Use these as 
an example to get started.

```php title="SensitiveDataRedactorTest.php"
<?php

declare(strict_types=1);

use Application\Security\SensitiveDataRedactor;

it('redacts default sensitive fields', function (): void {
    $redactor = new SensitiveDataRedactor();

    $result = $redactor->redact([
        'username' => 'joshua',
        'password' => 'super-secret',
        'api_key' => 'abc123',
    ]);

    expect($result)->toBe([
        'username' => 'joshua',
        'password' => '[REDACTED]',
        'api_key' => '[REDACTED]',
    ]);
});

it('redacts sensitive keys case insensitively', function (): void {
    $redactor = new SensitiveDataRedactor();

    $result = $redactor->redact([
        'PASSWORD' => 'secret-one',
        'Access_Token' => 'secret-two',
        'Api_Key' => 'secret-three',
    ]);

    expect($result)->toBe([
        'PASSWORD' => '[REDACTED]',
        'Access_Token' => '[REDACTED]',
        'Api_Key' => '[REDACTED]',
    ]);
});

it('redacts nested sensitive fields', function (): void {
    $redactor = new SensitiveDataRedactor();

    $result = $redactor->redact([
        'user' => [
            'name' => 'Joshua',
            'credentials' => [
                'password' => 'secret',
                'token' => 'token-value',
            ],
        ],
    ]);

    expect($result)->toBe([
        'user' => [
            'name' => 'Joshua',
            'credentials' => [
                'password' => '[REDACTED]',
                'token' => '[REDACTED]',
            ],
        ],
    ]);
});

it('redacts sensitive fields inside indexed arrays', function (): void {
    $redactor = new SensitiveDataRedactor();

    $result = $redactor->redact([
        'users' => [
            [
                'email' => 'first@example.com',
                'password' => 'first-secret',
            ],
            [
                'email' => 'second@example.com',
                'password' => 'second-secret',
            ],
        ],
    ]);

    expect($result)->toBe([
        'users' => [
            [
                'email' => 'first@example.com',
                'password' => '[REDACTED]',
            ],
            [
                'email' => 'second@example.com',
                'password' => '[REDACTED]',
            ],
        ],
    ]);
});

it('converts and redacts object properties', function (): void {
    $redactor = new SensitiveDataRedactor();

    $payload = new stdClass();
    $payload->username = 'joshua';
    $payload->password = 'secret';

    $result = $redactor->redact($payload);

    expect($result)->toBe([
        'username' => 'joshua',
        'password' => '[REDACTED]',
    ]);
});

it('preserves scalar values', function (
    mixed $value
): void {
    $redactor = new SensitiveDataRedactor();

    expect($redactor->redact($value))->toBe($value);
})->with([
    'string' => 'value',
    'integer' => 42,
    'float' => 10.5,
    'boolean' => true,
    'null' => null,
]);

it('supports a custom sensitive field list', function (): void {
    $redactor = new SensitiveDataRedactor([
        'social_security_number',
        'security_answer',
    ]);

    $result = $redactor->redact([
        'password' => 'not-redacted-with-custom-list',
        'social_security_number' => '123-45-6789',
        'security_answer' => 'example answer',
    ]);

    expect($result)->toBe([
        'password' => 'not-redacted-with-custom-list',
        'social_security_number' => '[REDACTED]',
        'security_answer' => '[REDACTED]',
    ]);
});

it('does not modify the original array', function (): void {
    $redactor = new SensitiveDataRedactor();

    $original = [
        'password' => 'secret',
    ];

    $result = $redactor->redact($original);

    expect($original)->toBe([
        'password' => 'secret',
    ])->and($result)->toBe([
        'password' => '[REDACTED]',
    ]);
});

it('does not redact partial key matches', function (): void {
    $redactor = new SensitiveDataRedactor();

    $result = $redactor->redact([
        'password_hint' => 'Your first pet',
        'token_count' => 4,
        'secretary' => 'Jane',
    ]);

    expect($result)->toBe([
        'password_hint' => 'Your first pet',
        'token_count' => 4,
        'secretary' => 'Jane',
    ]);
});
```

```php title="PdoThreatLoggerTest.php"
<?php

declare(strict_types=1);

use Application\Security\PdoThreatLogger;
use Application\Security\SensitiveDataRedactor;
use Codefy\Framework\Security\Firewall\ThreatMatch;
use Laminas\Diactoros\ServerRequest;
use Laminas\Diactoros\Uri;
use PDO;

beforeEach(function (): void {
    $this->pdo = new PDO('sqlite::memory:');

    $this->pdo->setAttribute(
        PDO::ATTR_ERRMODE,
        PDO::ERRMODE_EXCEPTION
    );

    $this->pdo->exec(
        <<<'SQL'
        CREATE TABLE threat_logs (
            threat_id TEXT PRIMARY KEY,
            ip_address TEXT NOT NULL,
            method TEXT NOT NULL,
            url TEXT NOT NULL,
            user_agent TEXT NULL,
            threat_group TEXT NOT NULL,
            threat_type TEXT NOT NULL,
            severity TEXT NOT NULL,
            confidence_score REAL NOT NULL,
            matched_source TEXT NULL,
            matched_field TEXT NULL,
            matched_pattern TEXT NULL,
            matched_value TEXT NULL,
            request_payload TEXT NULL,
            created_at TEXT NOT NULL
        )
        SQL
    );
});

it('redacts sensitive values before logging payloads', function (): void {
    $request = new ServerRequest(
        serverParams: [
            'REMOTE_ADDR' => '127.0.0.1',
        ],
        uploadedFiles: [],
        uri: new Uri('https://example.test/login'),
        method: 'POST',
        body: 'php://memory',
        headers: [
            'User-Agent' => 'Pest',
        ]
    );

    $request = $request
        ->withQueryParams([
            'token' => 'query-token',
            'page' => '1',
        ])
        ->withParsedBody([
            'email' => 'joshua@example.com',
            'password' => 'super-secret',
        ]);

    $match = new ThreatMatch(
        type: 'script_tag',
        severity: 'high',
        confidence: 0.95,
        pattern: '/<script/i',
        value: '<script>',
        group: 'xss',
        source: 'body',
        field: 'comment',
        excluded: false
    );

    $logger = new PdoThreatLogger(
        pdo: $this->pdo,
        redactor: new SensitiveDataRedactor(),
        logPayload: true
    );

    $logger->log($request, $match);

    $row = $this->pdo
        ->query('SELECT * FROM threat_logs')
        ->fetch(PDO::FETCH_ASSOC);

    expect($row)->toBeArray();

    $payload = json_decode(
        json: $row['request_payload'],
        associative: true,
        flags: JSON_THROW_ON_ERROR
    );

    expect($payload)->toMatchArray([
        'query' => [
            'token' => '[REDACTED]',
            'page' => '1',
        ],
        'body' => [
            'email' => 'joshua@example.com',
            'password' => '[REDACTED]',
        ],
    ]);
});

it('does not store a payload when payload logging is disabled', function (): void {
    $request = new ServerRequest(
        serverParams: [
            'REMOTE_ADDR' => '127.0.0.1',
        ],
        uploadedFiles: [],
        uri: new Uri('https://example.test/login'),
        method: 'POST'
    );

    $request = $request->withParsedBody([
        'password' => 'super-secret',
    ]);

    $match = new ThreatMatch(
        type: 'script_tag',
        severity: 'high',
        confidence: 0.95,
        pattern: '/<script/i',
        value: '<script>',
        group: 'xss',
        source: 'body',
        field: 'comment',
        excluded: false
    );

    $logger = new PdoThreatLogger(
        pdo: $this->pdo,
        redactor: new SensitiveDataRedactor(),
        logPayload: false
    );

    $logger->log($request, $match);

    $payload = $this->pdo
        ->query(
            'SELECT request_payload FROM threat_logs'
        )
        ->fetchColumn();

    expect($payload)->toBeNull();
});

it('redacts the matched value when its field is sensitive', function (): void {
    $request = new ServerRequest(
        serverParams: [
            'REMOTE_ADDR' => '127.0.0.1',
        ],
        uploadedFiles: [],
        uri: new Uri('https://example.test/login'),
        method: 'POST'
    );

    $match = new ThreatMatch(
        type: 'union_select',
        severity: 'high',
        confidence: 0.95,
        pattern: '/union\s+select/i',
        value: "' UNION SELECT * FROM users--",
        group: 'sql_injection',
        source: 'body',
        field: 'password',
        excluded: false
    );

    $logger = new PdoThreatLogger(
        pdo: $this->pdo,
        redactor: new SensitiveDataRedactor(),
        logPayload: false
    );

    $logger->log($request, $match);

    $matchedValue = $this->pdo
        ->query(
            'SELECT matched_value FROM threat_logs'
        )
        ->fetchColumn();

    expect($matchedValue)->toBe('[REDACTED]');
});
```

## Notifications

Notifications are delivered through implementations of:

```php
Codefy\Framework\Security\Firewall\ThreatNotifier
```

The notifier contract is:

```php
public function notify(
    ServerRequestInterface $request,
    ThreatMatch $match
): void;
```

A notifier should perform one notification operation, such as:

- Sending an email
- Sending a Slack message
- Sending a Microsoft Teams message
- Publishing an incident-management event
- Calling an internal webhook

## Slack Notifier Example

```php
<?php

declare(strict_types=1);

namespace Application\Security;

use Codefy\Framework\Security\Firewall\ThreatMatch;
use Codefy\Framework\Security\Firewall\ThreatNotifier;
use JsonException;
use Psr\Http\Message\ServerRequestInterface;
use RuntimeException;

use function file_get_contents;
use function json_encode;
use function sprintf;
use function stream_context_create;

final readonly class SlackThreatNotifier implements ThreatNotifier
{
    public function __construct(
        private string $webhookUrl
    ) {
    }

    /**
     * @throws JsonException
     */
    public function notify(
        ServerRequestInterface $request,
        ThreatMatch $match
    ): void {
        if ($this->webhookUrl === '') {
            return;
        }

        $payload = json_encode(
            value: [
                'text' => sprintf(
                    "Firewall threat detected\n"
                    . "Group: %s\n"
                    . "Type: %s\n"
                    . "Severity: %s\n"
                    . "Confidence: %.2f\n"
                    . "Method: %s\n"
                    . "URL: %s",
                    $match->group,
                    $match->type,
                    $match->severity,
                    $match->confidence,
                    $request->getMethod(),
                    (string) $request->getUri()
                ),
            ],
            flags: JSON_THROW_ON_ERROR
        );

        $context = stream_context_create([
            'http' => [
                'method' => 'POST',
                'header' => "Content-Type: application/json\r\n",
                'content' => $payload,
                'timeout' => 2,
                'ignore_errors' => true,
            ],
        ]);

        $result = file_get_contents(
            filename: $this->webhookUrl,
            use_include_path: false,
            context: $context
        );

        if ($result === false) {
            throw new RuntimeException(
                'The Slack firewall notification could not be sent.'
            );
        }
    }
}
```

Notifier implementations should throw meaningful exceptions when delivery fails.

The firewall catches notifier exceptions so that one failed notifier does not prevent:

- Other notifiers from running
- The threat from being logged
- The request from being blocked

Avoid suppressing notifier errors with:

```php
@file_get_contents(...)
```

## New Notifier Registration

The new registration mechanism uses:

```php
Codefy\Framework\Security\Firewall\ThreatNotifierCollection
```

Register the notifier collection in a service provider:

```php
<?php

declare(strict_types=1);

namespace Application\Provider;

use Application\Security\EmailThreatNotifier;
use Application\Security\SlackThreatNotifier;
use Codefy\Framework\Security\Firewall\ThreatNotifierCollection;
use Codefy\Framework\Support\CodefyServiceProvider;

use function Codefy\Framework\Helpers\env;

final class FirewallServiceProvider extends CodefyServiceProvider
{
    public function register(): void
    {
        $this->codefy->singleton(
            ThreatNotifierCollection::class,
            function (): ThreatNotifierCollection {
                return new ThreatNotifierCollection([
                    new EmailThreatNotifier(
                        recipient: env(
                            key: 'FIREWALL_ALERT_EMAIL',
                            default: ''
                        )
                    ),

                    new SlackThreatNotifier(
                        webhookUrl: env(
                            key: 'FIREWALL_SLACK_WEBHOOK',
                            default: ''
                        )
                    ),
                ]);
            }
        );
    }
}
```

The collection is injected into `FirewallMiddleware`.

Collection-based notifiers are merged with legacy notifier objects registered directly in `firewall.notifiers`.

## Configuring New Notifiers

Named notifier settings are configured in `firewall.php`:

```php
return [
    'notifiers' => [
        'email' => [
            'enabled' => true,
        ],

        'slack' => [
            'enabled' => false,
        ],
    ],
];
```

The middleware derives the configuration key from the notifier class name with suffix (`ThreatNotifier`).

Examples:

| Notifier class                 | Configuration key |
|--------------------------------|-------------------|
| `EmailThreatNotifier`          | `email`           |
| `SlackThreatNotifier`          | `slack`           |
| `MicrosoftTeamsThreatNotifier` | `microsoft_teams` |
| `WebhookNotifier`              | `webhook`         |

A notifier without a matching configuration entry remains enabled for backwards compatibility.

For example, this notifier:

```php
new CustomSecurityThreatNotifier()
```

uses the derived key:

```text
custom_security
```

To disable it:

```php
'notifiers' => [
    'custom_security' => [
        'enabled' => false,
    ],
],
```

## Legacy Notifier Registration

Earlier versions placed notifier objects directly in `firewall.php`:

```php
<?php

declare(strict_types=1);

use Application\Security\EmailThreatNotifier;
use Application\Security\SlackThreatNotifier;

use function Codefy\Framework\Helpers\env;

return [
    'notifiers' => [
        new EmailThreatNotifier(),

        new SlackThreatNotifier(
            webhookUrl: env(
                key: 'FIREWALL_SLACK_WEBHOOK',
                default: ''
            )
        ),
    ],
];
```

This format remains supported.

Legacy entries must be objects that implement `ThreatNotifier`.

Supported:

```php
'notifiers' => [
    new SlackThreatNotifier(
        webhookUrl: env(
            key: 'FIREWALL_SLACK_WEBHOOK',
            default: ''
        )
    ),
],
```

The following are not valid notifier objects:

```php
'notifiers' => [
    SlackThreatNotifier::class,
    [$object, 'notify'],
    static function (): void {
    },
],
```

Invalid values do not satisfy the `ThreatNotifier` contract.

## Combining New and Legacy Notifiers

Named notifier settings and legacy notifier objects may coexist:

```php
<?php

declare(strict_types=1);

use Application\Security\EmailThreatNotifier;

return [
    'notifiers' => [
        'email' => [
            'enabled' => true,
        ],

        'slack' => [
            'enabled' => false,
        ],

        new EmailThreatNotifier(),
    ],
];
```

In this example:

- The `email` entry contains settings.
- The `slack` entry contains settings.
- The numeric entry contains an actual notifier.
- The associative arrays are not treated as notifier implementations.
- `EmailThreatNotifier` runs because `email.enabled` is `true`.
- A registered `SlackThreatNotifier` is skipped because `slack.enabled` is `false`.

The corrected middleware merges:

1. Notifiers from `ThreatNotifierCollection`
2. Legacy notifier objects from `firewall.notifiers`

An injected collection no longer replaces or hides the legacy notifier objects.

## Duplicate Notifier Registration

The middleware prevents the same notifier object from running twice when the exact same object is registered in both locations.

```php
$emailNotifier = new EmailThreatNotifier();

$collection = new ThreatNotifierCollection([
    $emailNotifier,
]);

$config = [
    'notifiers' => [
        $emailNotifier,
    ],
];
```

The same object is only included once.

However, these are separate objects:

```php
$collection = new ThreatNotifierCollection([
    new EmailThreatNotifier(),
]);

$config = [
    'notifiers' => [
        new EmailThreatNotifier(),
    ],
];
```

Because they are different instances, both may run and send duplicate notifications.

Avoid registering separate instances of the same delivery integration unless duplicate notifications are intentional.

## Notification Enablement

A notifier runs only when all of the following conditions are met:

1. The firewall is enabled.
2. The request is not ignored.
3. A non-excluded threat is detected.
4. The threat meets the minimum alert severity.
5. The notifier is registered.
6. The notifier's named `enabled` setting is not `false`.

Example:

```php
'notifiers' => [
    'email' => [
        'enabled' => true,
    ],

    'slack' => [
        'enabled' => false,
    ],
],
```

This enables the email notifier and disables the Slack notifier.

Setting:

```php
'block' => false,
```

does not disable notifications.

Monitoring-only mode can still log and notify.

## Notifier Failure Handling

Each notifier is called independently.

When a notifier throws an exception:

1. The failure is logged.
2. Remaining notifiers continue.
3. Blocking behavior continues normally.

Notifier implementations should use short network timeouts because notification delivery occurs during request processing.

A webhook timeout between one and three seconds is generally safer than a long timeout.

For high-volume applications, consider having the notifier dispatch a queue message instead of performing the external network call synchronously.

## Verification

You can verify that the firewall is working by triggering a threat.

Start the application:

```terminaloutput
php codex serve
```

Test a registered route.

Using a registered route ensures the request passes through the application's normal middleware stack.

Append a malicious query parameter to the route.

### SQL Injection

```text
http://localhost:8080/search?q=' UNION SELECT * FROM users--
```

Decoded value:

```text
' UNION SELECT * FROM users--
```

### Cross-Site Scripting

```text
http://localhost:8080/search?q=<script>alert(1)</script>
```

Decoded value:

```html
<script>alert(1)</script>
```

### File Traversal

```text
http://localhost:8080/download?file=../../etc/passwd
```

### Remote Code Execution

```text
http://localhost:8080/run?cmd=system('id')
```

### Sensitive File Probe

```text
http://localhost:8080/.env
```

### PHP Probe

```text
http://localhost:8080/phpinfo.php
```

Use only local, development, staging, or otherwise authorized systems for security testing.

## Testing Custom Rules

Given this configuration:

```php
'rules' => [
    'sensitive_file_probe' => [
        'add' => [
            'custom-secret.json',
        ],
    ],
],
```

test:

```text
http://localhost:8080/custom-secret.json
```

The internally generated regular expression may contain an escaped representation such as:

```text
custom\-secret\.json
```

Tests should verify detector behavior rather than relying on the exact internal regular expression string.

## Gotchas

### `block` Does Not Disable Inspection

This configuration:

```php
'enabled' => true,
'block' => false,
```

still performs:

- Threat detection
- Threat logging
- Notification severity checks
- Notification delivery

It only prevents the firewall from returning the blocked response.

### Associative Notifier Entries Are Settings

This is notifier configuration:

```php
'email' => [
    'enabled' => true,
],
```

It is not a notifier implementation.

This is a notifier implementation:

```php
new EmailThreatNotifier(),
```

Only objects implementing `ThreatNotifier` are executed.

### Legacy and New Notifiers Are Merged

The current middleware merges collection-based and legacy notifiers.

An empty `ThreatNotifierCollection` does not disable legacy notifier objects stored in `firewall.notifiers`.

When upgrading your applications, you should ensure your app has not registered separate, duplicate notifier instances.

### Enablement Keys Depend on Class Names

The notifier configuration key is derived from the notifier class name.

Renaming:

```php
EmailThreatNotifier
```

to:

```php
SecurityEmailThreatNotifier
```

changes the derived configuration key from:

```text
email
```

to:

```text
security_email
```

Update `firewall.notifiers` after renaming a notifier.

### Missing Notifier Settings Default to Enabled

A notifier without a corresponding configuration array remains enabled for backwards compatibility.

Registering:

```php
new CustomThreatNotifier()
```

without this configuration:

```php
'custom' => [
    'enabled' => false,
],
```

means the notifier is enabled.

### Parameter Names Should Not Be Relied Upon

A notifier implementation may use different parameter names while still satisfying the interface:

```php
public function notify(
    ServerRequestInterface $serverRequest,
    ThreatMatch $threat
): void {
}
```

The middleware calls notifier implementations with positional arguments so that concrete implementations are not 
required to retain the interface parameter names.

### Generator-Based Collections

`ThreatNotifierCollection` accepts an iterable.

An array is the safest option:

```php
new ThreatNotifierCollection([
    $emailNotifier,
    $slackNotifier,
]);
```

A generator may be exhausted after its first use in a long-running application.

Avoid:

```php
new ThreatNotifierCollection(
    notifierGenerator()
);
```

unless the collection materializes the iterable during construction.

### Path Probes Are Different From Query Parameter Rules

Sensitive-file and PHP probes commonly inspect the request path.

This request:

```text
/download?file=id_rsa
```

may not be classified the same way as:

```text
/id_rsa
```

Use traversal detection for malicious file parameters and sensitive-file probe rules for direct path requests.

### A Request Can Match More Than One Group

A single request may match multiple threat patterns.

The detector returns the first matching, non-excluded threat according to rule priority.

Changing rules or priorities may change:

- The reported threat group
- The reported threat type
- The severity
- Log classification
- Notification content
- Test expectations

A classification change does not necessarily mean the request is no longer blocked.

### False Positives Are Possible

Pattern-based request inspection can produce false positives.

Common sources include:

- Rich-text editors
- Code snippets
- SQL examples
- Debugging tools
- Network management forms
- URL import fields
- Serialized data
- Encoded content
- File managers
- Template editors

Prefer:

1. Narrow rule changes.
2. Specific `remove` entries.
3. Carefully scoped ignored paths.
4. Monitoring-only validation.

Avoid disabling an entire threat group unless necessary.

### Ignored Paths Bypass All Inspection

Adding a route to `ignored_paths` does not disable one specific rule. It bypasses the complete firewall inspection process for that path.

Use ignored paths only when rule-level customization cannot safely address the issue.

### Payload Logging Can Store Secrets

Enabling:

```php
'log_payload' => true,
```

can expose sensitive values in logs.

Implement redaction and retention policies before enabling payload logging in production.

### Notifications Run During the Request

A slow email server, webhook, or third-party API can delay the HTTP response.

Use short timeouts or queue-backed notifier implementations for production applications.

## Recommended Production Checklist

Before enabling blocking in production:

- Enable monitoring-only mode.
- Review threat logs.
- Test all forms and API endpoints.
- Test rich-text and code editors.
- Test file uploads and import workflows.
- Test URL fields and external integrations.
- Configure ignored paths narrowly.
- Validate custom rule additions.
- Verify notifier configuration keys.
- Confirm notifier timeout behavior.
- Prevent duplicate notifier registration.
- Redact sensitive payload fields.
- Define a threat-log retention policy.
- Confirm the blocked response does not expose internal details.
- Enable blocking only after reviewing false positives.

## Minimal Production Configuration

```php title="./config/firewall.php"
<?php

declare(strict_types=1);

return [
    'enabled' => true,

    'block' => true,

    'log_payload' => false,

    'alert_min_severity' => 'high',

    'notifiers' => [],

    'ignored_paths' => [
        '/favicon.ico',
        '/robots.txt',
    ],

    'rules' => [
        'sql_injection' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'xss' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'rce' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'file_traversal' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'ssrf' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'scanner_path_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'sensitive_file_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'php_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],

        'wordpress_probe' => [
            'add' => [],
            'remove' => [],
            'replace' => [],
        ],
    ],
];
```
