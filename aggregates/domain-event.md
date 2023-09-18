An event is something that has happened in the past. A domain event is something that has happened and affects the 
state of the application. To take it a bit further beyond that, here is how Martin Fowler explains a domain event:

> The essence of a Domain Event is that you use it to capture things that can trigger a change to the state of the 
> application you are developing. These event objects are then processed to cause changes to the system, and stored 
> to provide an [Audit Log](https://www.martinfowler.com/eaaDev/AuditLog.html).
> 
> Fowler, M. (2005, December 12). _Domain Event_. Martin fowler. https://www.martinfowler.com/eaaDev/DomainEvent.html

Before coding out your aggregates or domain models, you need to discover the domain events you will need. You should 
work closely with a Domain expert to figure out what is important to the business.

In a blogging system, you might have different blogs or categories broken down by departments. For the sake of getting 
too technical, we construct a simple definition of the needed domain events. To define a domain event, you can create 
your own implementation by implementing the interface `Codefy\Domain\EventSourcing\DomainEvent`.

    <?php
    
    declare(strict_types=1);
    
    namespace App\Domain\Post\Events;
    
    use Codefy\Domain\EventSourcing\DomainEvent;
    
    final class PostWasCreated implements DomainEvent
    {
    }

Define A Domain Event
---------------------

Alternatively, you can define your domain event by extending the abstract class `Codefy\Domain\EventSourcing\AggregateChanged`.

    <?php
    
    declare(strict_types=1);
    
    namespace App\Domain\Post\Events;
    
    use Codefy\Domain\EventSourcing\AggregateChanged;
    use Codefy\Domain\EventSourcing\DomainEvent;
    
    final class PostWasCreated extends AggregateChanged implements DomainEvent
    {
    }

Domain Events
-------------

For a `Post` aggregate, there may be two domain events: `PostWasCreated` and `TitleWasChanged`. Below are their 
definitions by extending the class `AggregateChanged`.

### Post Was Created

    <?php
    
    declare(strict_types=1);
    
    namespace App\Domain\Post\Events;
    
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use App\Domain\Post\ValueObject\Content;
    use Codefy\Domain\Aggregate\AggregateId;
    use Codefy\Domain\EventSourcing\AggregateChanged;
    use Codefy\Domain\EventSourcing\DomainEvent;
    use Codefy\Domain\Metadata;
    use Qubus\Exception\Data\TypeException;
    
    use function Qubus\Support\Helpers\is_null__;
    
    final class PostWasCreated extends AggregateChanged implements DomainEvent
    {
        private PostId $postId;
    
        private Title $title;
    
        private Content $content;
    
        public static function withData(
            PostId $postId,
            Title $title,
            Content $content
        ): PostWasCreated|DomainEvent|AggregateChanged {
            $event = self::occur(
                aggregateId: $postId,
                payload: [
                    'title' => $title,
                    'content' => $content,
                ],
                metadata: [
                    Metadata::AGGREGATE_TYPE => 'post',
                    Metadata::EVENT_TYPE => 'post-was-created',
                ]
            );
    
            $event->postId = $postId;
            $event->title = $title;
            $event->content = $content;
    
            return $event;
        }
    
        /**
         * @throws TypeException
         */
        public function postId(): PostId|AggregateId
        {
            if (is_null__(var: $this->postId)) {
                $this->postId = PostId::fromString(postId: $this->aggregateId()->__toString());
            }
    
            return $this->postId;
        }
    
        /**
         * @throws TypeException
         */
        public function title(): Title
        {
            if (is_null__(var: $this->title)) {
                $this->title = Title::fromString(title: $this->payload()['title']->__toString());
            }
    
            return $this->title;
        }
    
        /**
         * @throws TypeException
         */
        public function content(): Content
        {
            if (is_null__(var: $this->content)) {
                $this->content = Content::fromString(content: $this->payload()['content']->__toString());
            }
    
            return $this->content;
        }
    }


### Title Was Changed

    <?php
    
    declare(strict_types=1);
    
    namespace App\Domain\Post\Events;
    
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use Codefy\Domain\Aggregate\AggregateId;
    use Codefy\Domain\EventSourcing\AggregateChanged;
    use Codefy\Domain\EventSourcing\DomainEvent;
    use Codefy\Domain\Metadata;
    use Qubus\Exception\Data\TypeException;
    
    use function Qubus\Support\Helpers\is_null__;
    
    final class TitleWasChanged extends AggregateChanged implements DomainEvent
    {
        private PostId $postId;
    
        private Title $title;
    
        public static function withData(PostId $postId, Title $title): TitleWasChanged|DomainEvent|AggregateChanged
        {
            $event = self::occur(
                aggregateId: $postId,
                payload: [
                    'title' => $title,
                ],
                metadata: [
                    Metadata::AGGREGATE_TYPE => 'post',
                    Metadata::EVENT_TYPE => 'title-was-changed',
                ]
            );
    
            $event->postId = $postId;
            $event->title = $title;
    
            return $event;
        }
    
        /**
         * @throws TypeException
         */
        public function postId(): PostId|AggregateId
        {
            if (is_null__($this->postId)) {
                $this->postId = PostId::fromString(postId: $this->aggregateId()->__toString());
            }
            return $this->postId;
        }
    
        /**
         * @throws TypeException
         */
        public function title(): Title
        {
            if (is_null__($this->title)) {
                $this->title = Title::fromString(title: $this->payload()['title']->__toString());
            }
    
            return $this->title;
        }
    }

There are several things to note about the above domain events.

**One** is that they are in the past tense and specify what has happened in the domain.

**Two**, we are explicit by stating that they implement `DomainEvent` noting that it satisfies the implementation.

**Three**, they extend `AggregateChanged` which has a private constructor which in turn makes them immutable. History 
should not be altered, only appended.

**Four**, the events are self-validating. If something is null, we make sure that some data is returned.

**Five**, notice the metadata array. `AGGREGATE_TYPE` categorizes the event and is recommended to be the name of the 
aggregate root or domain model. If `EVENT_TYPE` is not set, Codefy will automatically generate it. For example, if your 
event was called `BasketWasPickedUp`, then the `EVENT_TYPE` would be `basket-was-picked-up`.

**Lastly**, `$this->postId()` returns a `PostId|AggregateId` object, but you could also call `$this->aggregateId()` 
which returns an `AggregateId` object.

Testing
-------

    $event = PostWasCreated::withData(
        postId: PostId::fromNative('760b7c16-b28e-4d31-9f93-7a2f0d3a1c51'),
        title: new Title(value: 'New Post Title'),
        content: new Content(value: 'Short content for this new post.')
    );
    
    it('should be an instance of DomainEvent', function () use ($event) {
        Assert::assertInstanceOf(expected: DomainEvent::class, actual: $event);
    });
    
    it('should equal another instance with the same value.', function () use ($event) {
        expect(value: $event->aggregateId())->toEqual(expected: PostId::fromNative('760b7c16-b28e-4d31-9f93-7a2f0d3a1c51'));
    });
    
    it('should expose a title.', function () use ($event) {
        expect(value: $event->title())->toEqual(expected: new Title(value: 'New Post Title'));
    });
    
    it('should expose content.', function () use ($event) {
        expect(value: $event->content())->toEqual(expected: new Content(value: 'Short content for this new post.'));
    });

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).