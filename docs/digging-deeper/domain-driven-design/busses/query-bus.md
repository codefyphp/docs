---
title: Query Bus
sidebar_title: Query Bus
order: 3
---

As explained in the Busses section, a query bus signals a question to the database. To keep things separated, use the query bus for lookups or reads. The command bus along with projections are used for writes. 

Let's say we need to ask the database for a user's ID. We would first Create our query class and then our query handler class:

### Query

    <?php

    declare(strict_types=1);

    namespace App\Domain\User\Query;

    use Codefy\CommandBus\PropertyCommand;
    use Codefy\QueryBus\Query;

    final class FindUserByIdQuery extends PropertyCommand implements Query
    {
        public ?string $userId;
    }

Our query is a simple DTO. Next, the query will need a query handler.

### Query Handler

    <?php

    declare(strict_types=1);

    namespace App\Domain\User\Query;

    use Codefy\QueryBus\Query;
    use Codefy\QueryBus\QueryHandler;
    use Qubus\Expressive\Database;

    final class FindUserByIdQueryHandler implements QueryHandler
    {
        public function __construct(private Database $db)
        {
        }
        public function handle(Query $query): mixed
        {
            $this->db->setStructure(primaryKeyName: 'user_id');
            return $this->db->table(tableName: 'users')->where(condition: 'user_id = ?', parameters: $query->userId)->findOne();
        }
    }

### Using a Service

Now that we have our query and query handler, we can use it in our controller or a repository. But instead, I will show you how to create a service that you can then use in your controller:

    <?php

    declare(strict_types=1);

    namespace App\Domain\User\Services;

    use App\Domain\User\Query\FindUserByIdQuery;
    use Codefy\CommandBus\Containers\ContainerFactory;
    use Codefy\QueryBus\Busses\SynchronousQueryBus;
    use Codefy\QueryBus\Enquire;
    use Codefy\QueryBus\Resolvers\NativeQueryHandlerResolver;
    use Psr\Http\Message\ServerRequestInterface;

    final class UserAuth
    {
        public static function findUserById(?string $userId): mixed
        {
            $resolver = new NativeQueryHandlerResolver(container: ContainerFactory::make(config: []));
            $enquirer = new Enquire(bus: new SynchronousQueryBus($resolver));

            $query = new FindUserByIdQuery(data: [
                'userId' => $userId ?? '',
            ]);

            $user = $enquirer->execute($query);

            return $user;
        }
    }

Now we will call this service in our `UserController`:

    <?php

    declare(strict_types=1);

    namespace App\Infrastructure\Http\Controllers;

    use App\Domain\User\Services\UserAuth;
    use Codefy\Framework\Codefy;
    use Codefy\Framework\Http\BaseController;
    use Psr\Http\Message\ResponseInterface;
    use Qubus\Http\ServerRequest;
    use Qubus\View\Native\Exception\InvalidTemplateNameException;
    use Qubus\View\Native\Exception\ViewException;

    use function Codefy\Framework\Helpers\config;
    use function Qubus\Support\Helpers\is_false__;

    final class UserController extends BaseController
    {
        /**
        * @throws ViewException
        * @throws InvalidTemplateNameException
        */
        public function dashboard(ServerRequest $request): ResponseInterface|string
        {
            $user = UserAuth::findUserById(request: $request->get('userId'));

            if(is_false__($user)) {
                Codefy::$PHP->flash->error(
                    message: 'You must be logged in.'
                );

                return $this->redirect((string) config('auth.login_url'));
                exit();
            }
            return $this->view->render(template: 'framework::user', data: ['title' => 'Dashboard']);
        }
    }

In the above example, we call the `UserAuth` service  in our `UserController` to check if the specific user is logged 
in by using `ServerRequest`. The example isn't a typical real world example because you would most likely check for 
the `userId` in a cookie, but this gives you a basic example on how to use the query bus.

