---
title: ask
sidebar_title: ask
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
