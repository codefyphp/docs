---
summary: Persist and reconstitute event-sourced PHP aggregates with a CodefyPHP AggregateRepository, EventStore, projection, and repository-aware trait.
keywords: aggregate-repository,event-sourcing,domain-driven-design
---

Since our domain will have multiple `Post` instances, they will need to be collected into an `AggregateRepository`.

TDD
---

But first, let’s write out our tests:

```php
<?php

declare(strict_types=1);

use Codefy\Domain\EventSourcing\InMemoryEventStore;
use Codefy\Tests\Domain\InMemoryPostProjection;
use Domain\Post\Post;
use Domain\Post\Repository\PostRepository;
use Domain\Post\ValueObject\PostId;
use Domain\Post\ValueObject\Title;
use Domain\Post\ValueObject\Content;
use PHPUnit\Framework\Assert;

use function expect;
use function it;

it('should reconstitute a Post to its state after persisting it.', function () {
    $postId = new PostId(value: '01K5EJ40GKE3G9WEZAH277N1AY');

    $post = Post::createPost(
        postId: $postId,
        title: new Title(value: 'Second Post Title'),
        content: new Content(value: 'Another short form content.')
    );

    $posts = new PostRepository(
        eventStore: new InMemoryEventStore(),
        projection: new InMemoryPostProjection()
    );

    $posts->saveAggregateRoot(aggregate: $post);

    $reconstitutedPost = $posts->loadAggregateRoot(aggregateId: $postId);

    expect(value: $post)->toEqual(expected: $reconstitutedPost);
});
```

Implementation
--------------

```php
<?php

declare(strict_types=1);

namespace Infrastructure\Persistence\Repository;

use Codefy\Domain\Aggregate\AggregateId;
use Codefy\Domain\Aggregate\AggregateNotFoundException;
use Codefy\Domain\Aggregate\AggregateRepository;
use Codefy\Domain\Aggregate\RecordsEvents;
use Codefy\Domain\EventSourcing\EventStore;
use Codefy\Domain\EventSourcing\Projection;
use Domain\Post\Post;

final class PostRepository implements AggregateRepository
{
    public function __construct(
        public readonly EventStore $eventStore,
        public readonly Projection $projection
    ) {
    }

    /**
     * Record the aggregate's latest events to
     * the event store.
     *
     * @param RecordsEvents $aggregate
     * @return void
     */
    public function saveAggregateRoot(RecordsEvents $aggregate): void
    {
        $events = $aggregate->getRecordedEvents();

        $this->eventStore->commit(events: $events);

        $aggregate->clearRecordedEvents();
    }

    /**
     * Fetch a single Post.
     *
     * @param AggregateId $aggregateId
     * @return RecordsEvents
     * @throws AggregateNotFoundException
     */
    public function loadAggregateRoot(AggregateId $aggregateId): RecordsEvents
    {
        $aggregateHistory = $this->eventStore->getAggregateHistoryFor(aggregateId: $aggregateId);
            
        return Post::reconstituteFromEventStream(
            aggregateHistory: $aggregateHistory
        );
    }
}
```

Now with our repository implemented, our tests should pass.

An example of a complete implementation of [PostRepository](https://github.com/codefyphp/domain-driven-core/blob/master/tests/Domain/PostRepository.php) can be found on [Github](https://github.com/codefyphp/domain-driven-core).

You can use that as an example for an implementation of `Codefy\Domain\Aggregate\AggregateRepository`, or you can use 
the `Codefy\Traits\EventSourcedRepositoryAware` trait which implements the methods `saveAggregateRoot` and `loadAggregateRoot`.

```php
<?php

declare(strict_types=1);

namespace Infrastructure\Persistence\Repository;

use Codefy\Domain\Aggregate\AggregateRepository;
use Codefy\Domain\EventSourcing\EventStore;
use Codefy\Domain\EventSourcing\Projection;
use Codefy\Traits\EventSourcedRepositoryAware;

final class PostRepository implements AggregateRepository
{
    use EventSourcedRepositoryAware;

    public function __construct(
        public readonly EventStore $eventStore,
        public readonly Projection $projection
    ) {
    }
}
```

Instead of using `Codefy\Domain\EventSourcing\Projection` as a type-hint, it is better to use an explicit interface to 
type-hint against when you add the `alias` in `config/commandbus.php`:

```php
<?php

declare(strict_types=1);

namespace Domain\Post\Service;

use Codefy\Domain\EventSourcing\Projection;

interface PostProjection extends Projection
{
}
```

Then you can type-hint against an implementation of `PostProjection`, since you will need an implementation for each 
aggregate:

```php
<?php

declare(strict_types=1);

namespace Infrastructure\Persistence\Repository;

use Codefy\Domain\Aggregate\AggregateRepository;
use Codefy\Domain\EventSourcing\EventStore;
use Codefy\Traits\EventSourcedRepositoryAware;
use Domain\Post\Service\PostProjection;

final class PostRepository implements AggregateRepository
{
    use EventSourcedRepositoryAware;

    public function __construct(
        public readonly EventStore $eventStore,
        public readonly PostProjection $projection
    ) {
    }
}
```
