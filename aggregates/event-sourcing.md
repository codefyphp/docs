Up to this point, we’ve kept our `Post` aggregate in memory. In the end, we will want to persist it and load it back 
into memory for later use. Loading an aggregate back into memory involves reconstituting its previously recorded 
history. This concept is called **Event Sourcing**. The events are the single source of reference that make up the 
aggregate.

TDD
---

Let’s write out a test when events are stored and then retrieved from the store.

    use App\Domain\Post\Post;
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use App\Domain\Post\ValueObject\Content;
    use Codefy\Domain\Aggregate\EventStream;
    
    use function expect;
    use function it;
    use function iterator_to_array;
    
    it('should be the same after reconstitution.', function () {
        $postId = new PostId(value: '1cf57c2c-5c82-45a0-8a42-f0b725cfc42f');
        $post = Post::createPost(
            postId: $postId,
            title: new Title(value: 'Second Post Title'),
            content: new Content(value: 'Another short form content.')
        );
        $post->changeTitle(title: new Title(value: 'Reconstitute From History'));
        $events = $post->getRecordedEvents();
        $post->clearRecordedEvents();
    
        $reconstitutedPost = Post::reconstituteFromEventStream(
            aggregateHistory: new EventStream(
                aggregateId: $postId,
                events: iterator_to_array(
                    iterator: $events->getIterator()
                )
            )
        );
    
        expect(value: $post)->toEqual(expected: $reconstitutedPost);
    });

Implement Interface
-------------------

We need to start updating our `Post` aggregate so that it can now be event sourced.

    declare(strict_types=1);
    
    namespace App\Domain\Post;
    
    use App\Domain\Post\Event\PostWasCreated;
    use App\Domain\Post\Event\TitleWasChanged;
    use App\Domain\Post\Exceptions\TitleWasNullException;
    use BadMethodCallException;
    use Codefy\Domain\Aggregate\EventStream;
    use Codefy\Domain\Aggregate\IsEventSourced;
    use Codefy\Domain\Aggregate\RecordsEvents;
    use Codefy\Domain\EventSourcing\DomainEvent;
    use Codefy\Domain\EventSourcing\DomainEvents;
    use ReflectionClass;
    
    use function method_exists;
    use function sprintf;
    
    final class Post implements RecordsEvents, EventSourcing
    {
    }

We declare that `Post` `isEventSourced` and that it can be rebuilt from events.

Reconstitute
------------

The `isEventSourced` interface requires us to implement the static method, `reconstituteFromEventStream(EventStream $aggregateHistory)`.

    public static function reconstituteFromEventStream(EventStream $aggregateHistory): RecordsEvents
    {
        $postId = $aggregateHistory->aggregateId();
        $post = new Post(new PostId($postId->__toString()));

        foreach ($aggregateHistory as $event) {
            $post->when($event);
        }
        
        return $post;
    }

Reconstitution implies that `Post` exists in some form and that it can be retrieved. The `EventStream` is a list of 
chronological (very important) `DomainEvents`. We start off by fetching the aggregate’s identifier: `$postId`. Then we 
instantiate the `Post` aggregate and remember the constructor is private.

Apply Method
------------

Now we need to iterate through the historical events and rebuild the aggregate’s state until we get to the current 
state. We cannot the methods `createPost` or `changeTitle`, otherwise, we will be calling the `record` method, causing 
events to be recorded a second time.

Instead, we need a new private method called `when`. The method `when` helps apply the events instead of record them. 
Therefore, our aggregate needs a couple of new methods for this to work. Since our aggregate records two events named 
`PostWasCreated` and `TitleWasChanged`, the `when` method will automatically look for methods `whenPostWasCreated` and 
`whenTitleWasChanged`. These methods manipulate state.

    protected function whenPostWasCreated(PostWasCreated $event): void
    {
        $this->postId = $event->aggregateId();
        $this->title = $event->title();
        $this->content = $event->content();
    }

    protected function whenTitleWasChanged(TitleWasChanged $event): void
    {
        $this->postId = $event->aggregateId();
        $this->title = $event->title();
    }

Update record Method
--------------------

Lastly, we need to make sure that newly recorded events are also applied to state. Therefore, we need to update our 
`record` method:

    protected function recordThat(DomainEvent $event): void
    {
        $this->recordedEvents[] = $event;

        $this->when($event);
    }

Below is the new state of our aggregate class:

    final class Post implements RecordsEvents, IsEventSourced
    {
        protected array $recordedEvents = [];
    
        private function __construct(private PostId $postId)
        {
        }
    
        /**
         * @throws TitleWasNullException
         */
        public static function createPost(PostId $postId, Title $title, Content $content): Post
        {
            if ($title->isEmpty()) {
                throw new TitleWasNullException(message: 'Title cannot be null.');
            }
    
            $post = self::root(aggregateId: $postId);
    
            $post->recordApplyAndPublishThat(
                event: PostWasCreated::withData($postId, $title, $content)
            );
    
            return $post;
        }
    
        /**
         * @throws TitleWasNullException
         */
        public function changeTitle(Title $title): void
        {
            if ($title->isEmpty()) {
                throw new TitleWasNullException(message: 'Title cannot be null.');
            }
            if ($title->__toString() === $this->title->__toString()) {
                return;
            }
            $this->recordApplyAndPublishThat(
                event: TitleWasChanged::withData(postId: $this->postId, title: $title)
            );
        }
    
        private function recordThat(DomainEvent $event): void
        {
            $this->recordedEvents[] = $event;
    
            $this->when($event);
        }
    
        protected function when(DomainEvent $event): void
        {
            $method = sprintf('when%s', (new ReflectionClass($event))->getShortName());
    
            if (!method_exists($this, $method)) {
                throw new BadMethodCallException(
                    sprintf("There is no method named '%s' that can be called in '%s'.", $method, static::class)
                );
            }
    
            $this->$method($event);
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

Github
------

An advanced version of this `Post` aggregate can be found on [Github](https://github.com/codefyphp/domain-driven-core/blob/master/tests/Domain/Post.php).

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).