A full-blown event store is beyond the scope of this documentation, but Codefy has an `InMemoryEventStore` we can use. 
It implements the `EventStore` interface that consists of two methods: `append`, `getAggregateHistoryFor`, and 
`loadFromPlayhead`. We won’t be concerning ourselves with the third method in this documentation.

An append/commit should always be transactional. The whole set of `DomainEvents` should be persisted, or none at all.

The `EventStore` supports two read operations. One that fetches an aggregates complete history and the other that 
fetches a history from a version point.

TDD
---

Let’s test it out:

    use App\Domain\Post\Post;
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use App\Domain\Post\ValueObject\Content;
    use Codefy\Domain\EventSourcing\InMemoryEventStore;
    
    use function expect;
    use function it;
    use function iterator_to_array;
    
    it('should retrieve all events from the event store based on aggregate id.', function () {
        $postId = new PostId(value: '1cf57c2c-5c82-45a0-8a42-f0b725cfc42f');
    
        $post = Post::createPost(
            postId: $postId,
            title: new Title(value: 'Second Post Title'),
            content: new Content(value: 'Another short form content.')
        );
    
        $events = $post->getRecordedEvents();
        $eventStore = new InMemoryEventStore();
    
        foreach ($events as $event) {
            $eventStore->append(event: $event);
        }
    
        $iterator = $eventStore->getAggregateHistoryFor(
            aggregateId: PostId::fromString(
                postId: '1cf57c2c-5c82-45a0-8a42-f0b725cfc42f'
            )
        );
        $aggregateHistory = iterator_to_array(iterator: $iterator->getIterator());
    
        foreach ($aggregateHistory as $event) {
            expect(value: $post->title())->toEqual(expected: $event->title());
            expect(value: $post->aggregateId())->toEqual(expected: $event->aggregateId());
        }
    });

Github
------

An in-memory implementation of `EventStore` is on [Github](https://github.com/codefyphp/domain-driven-core/blob/master/Domain/EventSourcing/InMemoryEventStore.php).

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).