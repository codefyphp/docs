Since our domain will have multiple `Post` instances, they will need to be collected into an AggregateRepository.

TDD
---

But first, let’s write out our tests:

    <?php

    use App\Domain\Post\Post;
    use App\Domain\Post\Repository\PostRepository;
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use App\Domain\Post\ValueObject\Content;
    use Codefy\Domain\EventSourcing\InMemoryEventStore;
    use PHPUnit\Framework\Assert;
    
    use function expect;
    use function it;
    
    it('should reconstitute a Post to its state after persisting it.', function () {
        $postId = new PostId(value: '1cf57c2c-5c82-45a0-8a42-f0b725cfc42f');
    
        $post = Post::createPost(
            postId: $postId,
            title: new Title(value: 'Second Post Title'),
            content: new Content(value: 'Another short form content.')
        );
    
        $posts = new PostRepository(eventStore: new InMemoryEventStore());
    
        $posts->saveAggregateRoot(aggregate: $post);
    
        $reconstitutedPost = $posts->loadAggregateRoot(aggregateId: $postId);
    
        expect(value: $post)->toEqual(expected: $reconstitutedPost);
    });

Implementation
--------------

    <?php

    use App\Domain\Post\Post;
    use Codefy\Domain\Aggregate\AggregateId;
    use Codefy\Domain\Aggregate\AggregateNotFoundException;
    use Codefy\Domain\Aggregate\AggregateRepository;
    use Codefy\Domain\Aggregate\RecordsEvents;
    use Codefy\Domain\EventSourcing\EventStore;
    
    final class PostRepository implements AggregateRepository
    {
        public function __construct(public readonly EventStore $eventStore)
        {
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
            return Post::reconstituteFromEventStream(aggregateHistory: $aggregateHistory);
        }
    }

Now with our repository implemented, our tests should pass.

Github
------

A complete implementation of [PostRepository](https://github.com/codefyphp/domain-driven-core/blob/master/tests/Domain/PostRepository.php) and [InMemoryEventStore](https://github.com/codefyphp/domain-driven-core/blob/master/Domain/EventSourcing/InMemoryEventStore.php) can be found on [Github](https://github.com/codefyphp/domain-driven-core).

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.