---
title: Query Bus
sidebar_title: Query Bus
summary: Build read-side CQRS workflows with the CodefyPHP query bus, typed query messages, dedicated handlers, database lookups, and application services.
keywords: query-bus,cqrs,php-query-handler
order: 3
---

As explained in the Busses section, a query bus signals a question to the database. To keep things separated, use the 
query bus for lookups or reads. The command bus along with projections are used for writes. 

Let's say we need to ask the database for a user's ID. We would first Create our query class and then our query handler class:

### Query

```php
<?php

declare(strict_types=1);

namespace Domain\User\Query;

use Codefy\CommandBus\PropertyCommand;
use Codefy\QueryBus\Query;
use Qubus\ValueObjects\StringLiteral\StringLiteral;

final class FindUserByIdQuery extends PropertyCommand implements Query
{
    public StringLiteral $userId;
}
```

Our query is a simple DTO. Next, the query will need a query handler.

### Query Handler

```php
<?php

declare(strict_types=1);

namespace Domain\User\Query;

use Codefy\QueryBus\Query;
use Codefy\QueryBus\QueryHandler;
use Domain\User\Query\FindUserByIdQuery;
use Qubus\Expressive\Database;

final class FindUserByIdQueryHandler implements QueryHandler
{
    public function __construct(private Database $db)
    {
    }
    
    public function handle(FindUserByIdQuery|Query $query): mixed
    {
        $this->db->setStructure(primaryKeyName: 'user_id');
        
        return $this->db
            ->table(tableName: 'users')
            ->where(condition: 'user_id = ?', parameters: $query->userId->toNative())
            ->findOne();
    }
}
```

### Using a Service

Now that we have our query and query handler, we can use it in our controller or a repository. But instead, I will show 
you how to create a service that you can then use in your controller:

```php
<?php

declare(strict_types=1);

namespace Domain\User\Service;

use Codefy\QueryBus\UnresolvableQueryHandlerException;
use Domain\User\Query\FindUserByIdQuery;
use Qubus\ValueObjects\StringLiteral\StringLiteral;
use ReflectionException;

use function Codefy\Framework\Helpers\ask;

final readonly class UserService
{
    /**
     * @throws ReflectionException
     * @throws UnresolvableQueryHandlerException
     */
    public static function findUserById(string $userId): mixed
    {
        return ask(
            new FindUserByIdQuery(
                [
                    'userId' => new StringLiteral($userId)
                ]
            )
        );
    }
}
```

Now we will call this service in our `UserController`:

```php
<?php

declare(strict_types=1);

namespace Application\Http\Controller;

use Codefy\Framework\Codefy;
use Codefy\Framework\Http\BaseController;
use Domain\User\Service\UserService;
use Psr\Http\Message\ResponseInterface;

use function Qubus\Support\Helpers\is_false__;
use function Codefy\Framework\Helpers\trans;
use function Codefy\Framework\Helpers\user;
use function Codefy\Framework\Helpers\view;

final class UserController extends BaseController
{
    public function dashboard(): ResponseInterface|string
    {
        $user = UserService::findUserById(userId: user()->user_id);

        if(is_false__($user)) {
            Codefy::$PHP->flash->error(
                message: 'You must be logged in.'
            );

            return $this->redirect(
                url: $this->router->url(
                    name: 'auth.login'
                )
            );
        }
        
        return view(
            template: 'framework::user',
            data: [
                'title' => trans('Dashboard')
            ]
        );
    }
}
```

In the above example, we call the `UserService` class in our `UserController` to check if the specific user is 
authenticated. If true, the user will continue on to the dashboard, if false, the user will be redirected to the login 
page.
