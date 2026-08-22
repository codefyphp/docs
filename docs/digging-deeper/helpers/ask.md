---
title: ask
sidebar_title: ask
summary: Dispatch a CodefyPHP Query object through the query bus with the ask helper and return the result produced by its matching query handler.
keywords: ask-helper,query-bus,cqrs
---


Description
-----------

Queries the given query and returns a result if any.

Usage
-----

```php
<?php

use function Codefy\Framework\Helpers\ask;

function ask(Query $query): mixed;
```

Parameters
----------

**$query** (`Codefy\QueryBus\Query`) (required) Query to pass through the query bus.

## Example

```php
<?php

use Domain\User\Query\FindUserByIdQuery;

use function Codefy\Framework\Helpers\ask;

$userId = '01KFRYWSVYEFS9MHXHZR0JDF59';

$query = new FindUserByIdQuery(data: [
    'userId' => $userId,
]);

$user = ask($query);
```
