---
title: ask
sidebar_title: ask
---


Description
-----------

Queries the given query and returns a result if any.

Usage
-----

    <?php

    use function Codefy\Framework\Helpers\ask;
    
    function ask(Query $query): mixed;

## Example

    <?php
    
    use App\Domain\User\Query\FindUserByIdQuery;
    
    use function Codefy\Framework\Helpers\ask;
    
    $query = new FindUserByIdQuery(data: [
        'userId' => $userId ?? '',
    ]);
    
    $user = ask($query);

Parameters
----------

**$query** (`Codefy\QueryBus\Query`) (required) Query to pass through the query bus.