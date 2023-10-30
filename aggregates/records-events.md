Domain events describe what has happened, but they originate from an aggregate or domain model. With our value objects 
and domain events in place, we are now ready to build out our aggregate.

TDD
---

Let’s do a simple test by using TDD.

    <?php

    declare(strict_types=1);
    
    use App\Domain\Post\Events\PostWasCreated;
    use App\Domain\Post\Events\TitleWasChanged;
    use App\Domain\Post\Post;
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use App\Domain\Post\ValueObject\Content;
    use Codefy\Domain\Aggregate\AggregateId;
    use Codefy\Domain\Aggregate\RecordsEvents;
    use Codefy\Domain\EventSourcing\DomainEvent;
    use Codefy\Domain\EventSourcing\DomainEvents;
    use PHPUnit\Framework\Assert;
    
    use function expect;
    use function it;
    
    it('should have recorded 2 events.', function () {
        $post = Post::createPost(
            postId: new PostId(value: '760b7c16-b28e-4d31-9f93-7a2f0d3a1c51'),
            title: new Title(value: 'New Post Title'),
            content: new Content(value: 'This is short form content.')
        );
        $post->changeTitle(title: new Title(value: 'Updated Post Title'));
        $events = $post->getRecordedEvents();
    
        Assert::assertTrue(condition: $post->hasRecordedEvents());
    
        expect(value: PostId::fromString(postId: '760b7c16-b28e-4d31-9f93-7a2f0d3a1c51'))
            ->toEqual(expected: $post->aggregateId())
            ->and(value: 2)->toEqual(expected: $post->playhead());
    
        Assert::assertCount(expectedCount: 2, haystack: $events);
    
        $post->clearRecordedEvents();
    
        Assert::assertFalse(condition: $post->hasRecordedEvents());
        Assert::assertCount(expectedCount: 0, haystack: $post->getRecordedEvents());
    });

In our test, a new post is created, and the title has been changed which equals 2 events.

`$post->clearRecordedEvents()` clears the events so that next time we call the `createPost` method on `Post`, we don’t 
retrieve a list of old data mixed with new data in our results.

Post Implementation
-------------------

Now we are at the point where we can create our `Post` aggregate or domain model. We will keep it simple in order to 
satisfy the tests. Let’s take it one step/method at a time:

    <?php

    final class Post implements RecordsEvents
    {
    }

> Reading the class in natural language we have a Post that records events.

### Private Constructor

    <?php

    private function __construct(private PostId $postId)
    {
    }

The constructor is private to make it immutable. So we will have to instantiate the class by using a named constructor.

### createPost Method

    <?php

    public static function createPost(PostId $postId, Title $title, Content $content): Post
    {
        $post = new Post(postID: $postId);

        $post->record(
            event: PostWasCreated::withData($postId, $title, $content)
        );

        return $post;
    }

Our named constructor also records an event.

> Record that a post was created.

### changeTitle Method

    <?php

    public function changeTitle(Title $title): void
    {
        $this->record(
            event: TitleWasChanged::withData(postId: $this->postId, title: $title)
        );
    }

Our second method also records an event.

> Record that a post title was changed.

### record and Other Methods

Now let’s implement a `record` method along with some other methods implemented from `RecordsEvents` (the `record` 
method is not part of the `RecordsEvents` interface). It depends on how you want to implement these methods. They can 
be implemented in the aggregate or via a trait.

    <?php

    private function record(DomainEvent $event)
    {
        $this->recordedEvents[] = $event;
    }

    public function aggregateId(): PostId|AggregateId
    {
        return $this->postId;
    }

    public function hasRecordedEvents(): bool
    {
        return !empty($this->recordedEvents);
    }

    public function getRecordedEvents(): DomainEvents
    {
        return DomainEvents::fromArray(events: $this->recordedEvents);
    }

    public function clearRecordedEvents()
    {
        $this->recordedEvents = [];
    }

`recordedEvents` keeps a list of newly created events since the last `clearRecordedEvents()`.

`aggregateId()` is the unique identifier of the `Post` aggregate.

We can use `hasRecordedEvents()` to check if there are any uncommitted events since the last time it was cleared or persisted.

`getRecordedEvents()` is a list of domain events that were recorded since the last time they were cleared or persisted.

`DomainEvents` is an immutable array or `DomainEvent` objects.

So, let’s put all the pieces together to make up our `Post` aggregate/domain model:

    <?php

    final class Post implements RecordsEvents
    {
        protected array $recordedEvents = [];
    
        private function __construct(private PostId $postId)
        {
        }
    
        public static function createPost(PostId $postId, Title $title, Content $content): Post
        {
            $post = new Post(postID: $postId);
    
            $post->record(
                event: PostWasCreated::withData($postId, $title, $content)
            );
    
            return $post;
        }
    
        public function changeTitle(Title $title): void
        {
            $this->record(
                event: TitleWasChanged::withData(postId: $this->postId, title: $title)
            );
        }
    
        private function record(DomainEvent $event)
        {
            $this->recordedEvents[] = $event;
        }
    
        public function hasRecordedEvents(): bool
        {
            return !empty($this->recordedEvents);
        }
    
        public function getRecordedEvents(): DomainEvents
        {
            return DomainEvents::fromArray(events: $this->recordedEvents);
        }
    
        public function clearRecordedEvents()
        {
            $this->recordedEvents = [];
        }
    }

Now that the Post class is fully defined, our test should run as expected.

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).