# Status

***

* Full name: `\Qubus\Http\Status`

## Constants

| Constant                               | Visibility | Type | Value |
|----------------------------------------|------------|------|-------|
| `CONTINUE`                             | public     |      | 100   |
| `SWITCHING_PROTOCOLS`                  | public     |      | 101   |
| `PROCESSING`                           | public     |      | 102   |
| `EARLY_HINTS`                          | public     |      | 103   |
| `OK`                                   | public     |      | 200   |
| `CREATED`                              | public     |      | 201   |
| `ACCEPTED`                             | public     |      | 202   |
| `NON_AUTHORITATIVE_INFORMATION`        | public     |      | 203   |
| `NO_CONTENT`                           | public     |      | 204   |
| `RESET_CONTENT`                        | public     |      | 205   |
| `PARTIAL_CONTENT`                      | public     |      | 206   |
| `MULTI_STATUS`                         | public     |      | 207   |
| `ALREADY_REPORTED`                     | public     |      | 208   |
| `THIS_IS_FINE`                         | public     |      | 218   |
| `IM_USED`                              | public     |      | 226   |
| `MULTIPLE_CHOICES`                     | public     |      | 300   |
| `MOVED_PERMANENTLY`                    | public     |      | 301   |
| `FOUND`                                | public     |      | 302   |
| `SEE_OTHER`                            | public     |      | 303   |
| `NOT_MODIFIED`                         | public     |      | 304   |
| `USE_PROXY`                            | public     |      | 305   |
| `TEMPORARY_REDIRECT`                   | public     |      | 307   |
| `PERMANENT_REDIRECT`                   | public     |      | 308   |
| `BAD_REQUEST`                          | public     |      | 400   |
| `UNAUTHORIZED`                         | public     |      | 401   |
| `PAYMENT_REQUIRED`                     | public     |      | 402   |
| `FORBIDDEN`                            | public     |      | 403   |
| `NOT_FOUND`                            | public     |      | 404   |
| `METHOD_NOT_ALLOWED`                   | public     |      | 405   |
| `NOT_ACCEPTABLE`                       | public     |      | 406   |
| `PROXY_AUTHENTICATION_REQUIRED`        | public     |      | 407   |
| `REQUEST_TIMEOUT`                      | public     |      | 408   |
| `CONFLICT`                             | public     |      | 409   |
| `GONE`                                 | public     |      | 410   |
| `LENGTH_REQUIRED`                      | public     |      | 411   |
| `PRECONDITION_FAILED`                  | public     |      | 412   |
| `PAYLOAD_TOO_LARGE`                    | public     |      | 413   |
| `URI_TOO_LONG`                         | public     |      | 414   |
| `UNSUPPORTED_MEDIA_TYPE`               | public     |      | 415   |
| `RANGE_NOT_SATISFIABLE`                | public     |      | 416   |
| `EXPECTATION_FAILED`                   | public     |      | 417   |
| `I_AM_A_TEAPOT`                        | public     |      | 418   |
| `PAGE_EXPIRED`                         | public     |      | 419   |
| `MISDIRECTED_REQUEST`                  | public     |      | 421   |
| `UNPROCESSABLE_ENTITY`                 | public     |      | 422   |
| `LOCKED`                               | public     |      | 423   |
| `FAILED_DEPENDENCY`                    | public     |      | 424   |
| `TOO_EARLY`                            | public     |      | 425   |
| `UPGRADE_REQUIRED`                     | public     |      | 426   |
| `PRECONDITION_REQUIRED`                | public     |      | 428   |
| `TOO_MANY_REQUESTS`                    | public     |      | 429   |
| `REQUEST_HEADER_FIELDS_TOO_LARGE`      | public     |      | 431   |
| `LOGIN_TIME_OUT`                       | public     |      | 440   |
| `NO_RESPONSE`                          | public     |      | 444   |
| `RETRY_WITH`                           | public     |      | 449   |
| `BLOCKED_BY_WINDOWS_PARENTAL_CONTROL`  | public     |      | 450   |
| `UNAVAILABLE_FOR_LEGAL_REASONS`        | public     |      | 451   |
| `CLIENT_CLOSED_THE_CONNECTION`         | public     |      | 460   |
| `X_FORWARDED_FOR_TOO_LARGE`            | public     |      | 463   |
| `REQUEST_HEADER_TOO_LARGE`             | public     |      | 494   |
| `SSL_CERTIFICATE_ERROR`                | public     |      | 495   |
| `SSL_CERTIFICATE_REQUIRED`             | public     |      | 496   |
| `HTTP_REQUEST_SENT_TO_HTTPS_PORT`      | public     |      | 497   |
| `INVALID_TOKEN`                        | public     |      | 498   |
| `TOKEN_REQUIRED`                       | public     |      | 499   |
| `INTERNAL_SERVER_ERROR`                | public     |      | 500   |
| `NOT_IMPLEMENTED`                      | public     |      | 501   |
| `BAD_GATEWAY`                          | public     |      | 502   |
| `SERVICE_UNAVAILABLE`                  | public     |      | 503   |
| `GATEWAY_TIMEOUT`                      | public     |      | 504   |
| `HTTP_VERSION_NOT_SUPPORTED`           | public     |      | 505   |
| `VARIANT_ALSO_NEGOTIATES`              | public     |      | 506   |
| `INSUFFICIENT_STORAGE`                 | public     |      | 507   |
| `LOOP_DETECTED`                        | public     |      | 508   |
| `BANDWIDTH_LIMIT_EXCEEDED`             | public     |      | 509   |
| `NOT_EXTENDED`                         | public     |      | 510   |
| `NETWORK_AUTHENTICATION_REQUIRED`      | public     |      | 511   |
| `WEB_SERVER_RETURNED_AN_UNKNOWN_ERROR` | public     |      | 520   |
| `WEB_SERVER_IS_DOWN`                   | public     |      | 521   |
| `CONNECTION_TIMED_OUT`                 | public     |      | 522   |
| `ORIGIN_IS_UNREACHABLE`                | public     |      | 523   |
| `A_TIMEOUT_OCCURRED`                   | public     |      | 524   |
| `SSL_HANDSHAKE_FAILED`                 | public     |      | 525   |
| `INVALID_SSL_CERTIFICATE`              | public     |      | 526   |
| `RAILGUN_ERROR`                        | public     |      | 527   |
| `SITE_IS_OVERLOADED`                   | public     |      | 529   |
| `SITE_IS_FROZEN`                       | public     |      | 530   |
| `NETWORK_READ_TIMEOUT_ERROR`           | public     |      | 598   |

## Properties

### messages

```php
private static array $messages
```

* This property is **static**.

***

## Methods

### getMessageForCode

```php
public static getMessageForCode(int $code): string
```

* This method is **static**.
**Parameters:**

| Parameter | Type    | Description |
|-----------|---------|-------------|
| `$code`   | **int** |             |

***

### isError

```php
public static isError(mixed $code): bool
```

* This method is **static**.
**Parameters:**

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `$code`   | **mixed** |             |

***
