An invariant is something that holds true about your domain no matter what. Invariants ensure consistency within the 
domain.

As an example using our Post aggregate, an invariant we could probably protect is that on insert, a title should not 
be empty or null.

TDD
---

First, let’s write out a test to prove that a `TitleWasNullException` is thrown when we violate the invariant.

    <?php

    use App\Domain\Post\Post;
    use App\Domain\Post\TitleWasNullException;
    use App\Domain\Post\ValueObject\PostId;
    use App\Domain\Post\ValueObject\Title;
    use App\Domain\Post\ValueObject\Content;
    
    it('should not allow a null title.', function () use ($event) {
        return Post::createPost(
            postId: new PostId(value: '760b7c16-b28e-4d31-9f93-7a2f0d3a1c51'),
            title: new Title(value: ''),
            content: new Content(value: 'A null title is not allowed'),
        );
    })->throws(exception: TitleWasNullException::class, exceptionMessage: 'Title cannot be null.');

Method Updates
--------------

In the last section, we introduced the `Post` aggregate. We will now update the methods `createPost` and `changeTitle` 
to meet our invariant exception. As mentioned in the previous section when we created some value objects, the `Title` 
value object inherits a few methods from the base class `StringLiteral`. One of those methods is `isEmpty()`. We can 
use this method to protect our invariant.

    <?php

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

Now that our methods have been updated, our tests should now pass.

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).