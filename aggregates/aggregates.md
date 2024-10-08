Aggregates are the most important part of Domain-Driven Design. They are not just plain old PHP objects (POPO), but 
rich models that help with the complexity of business rules and invariants.

Throughout the aggregates section, you will learn how to build a domain rich eventsourced aggregate. Here is an example 
of an eventsourced `Post` aggregate:

    <?php

    use App\Domain\Post\Exceptions\TitleWasNullException;
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use App\Domain\Post\ValueObject\Content;
    use Codefy\Domain\Aggregate\AggregateRoot;
    use Codefy\Domain\Aggregate\EventSourcedAggregate;
    use Qubus\Exception\Data\TypeException;
    
    use function Qubus\Inheritance\Helpers\tap;
    
    final class Post extends EventSourcedAggregate implements AggregateRoot
    {
        private PostId $postId;
    
        private Title $title;
    
        private Content $content;
    
        /**
         * @throws TitleWasNullException
         */
        public static function createPostWithoutTap(PostId $postId, Title $title, Content $content): Post
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
        public static function createPostWithTap(PostId $postId, Title $title, Content $content): Post
        {
            if ($title->isEmpty()) {
                throw new TitleWasNullException(message: 'Title cannot be null.');
            }
    
            return tap(
                value: self::root($postId),
                callback: fn($post) => $post->recordApplyAndPublishThat(
                    PostWasCreated::withData(postId: $postId, title: $title, content: $content)
                )
            );
        }
    
        public static function fromNative(PostId $postId): Post
        {
            return self::root(aggregateId: $postId);
        }
    
        /**S
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
    
        public function title(): Title
        {
            return $this->title;
        }
    
        public function content(): Content
        {
            return $this->content;
        }
    
        /**
         * @throws TypeException
         */
        protected function whenPostWasCreated(PostWasCreated $event): void
        {
            $this->postId = $event->aggregateId();
            $this->title = $event->title();
            $this->content = $event->content();
        }
    
        /**
         * @throws TypeException
         */
        protected function whenTitleWasChanged(TitleWasChanged $event): void
        {
            $this->postId = $event->aggregateId();
            $this->title = $event->title();
        }
    }
            
        
There is a lot to unpack in the Post aggregate, but as you go through the rest of this section, you will begin to 
understand its parts as it's broken down and explained.

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.