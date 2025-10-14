---
title: Rate Limiting
sidebar_title: Rate Limiting
order: 27
---

With Rate Limiting, you can limit the number of requests a client can make to your app in a given time frame.

## Configuration

In your `./config/throttle.php`, add a `max_attempts` limit as well as a `ttl` time period.

```php title="./config/throttle.php"
<?php

declare(strict_types=1);

return [
    'max_attempts' => 5,
    'ttl' => 600,
];
```

The above example would allow `5` requests within a timespan of `10` minutes (600 seconds). If 5 attempts were reached 
during the time period, the client would be blocked for `10` minutes before continuing. The release time is cached by 
whatever caching adapter you've set for your app.

## Middleware

Codefy comes with a `Codefy\Framework\Http\Middleware\ThrottleMiddleware`. You can use the alias `rate.limiter` on your 
routes or controllers.