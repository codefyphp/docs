It is recommended to be explicit as possible when working with aggregates or domain models. Value Objects are highly 
recommended when identifying an aggregate or domain model. You can use any type of ID, but using UUIDs is best.

Implementation
--------------

If you were creating a `Post` aggregate, an identifier value object would be `PostId`. You can simply use the 
`AggregateId` interface and implement its methods. However, it is highly recommended that you extend the abstract 
implementation and implement AggregateId instead:

    <?php

    declare(strict_types=1);
    
    namespace App\Domain\Post\ValueObject;
    
    use App\Domain\Post\Post;
    use Codefy\Domain\Aggregate\AggregateId;
    use Qubus\Exception\Data\TypeException;
    use Qubus\ValueObjects\Identity\Uuid;
    
    final class PostId extends Uuid implements AggregateId
    {
        /**
         * @throws TypeException
         */
        public static function fromString(string $postId): self
        {
            return new self(value: $postId);
        }
    
        public function aggregateClassName(): string
        {
            return Post::className();
        }
    }

The method `aggregateClassName` will be explained when we get to the section on creating an aggregate. But an 
alternative to having `PostId` extend `Uuid`, you can use `Ulid` instead:

    <?php

    declare(strict_types=1);
    
    namespace App\Domain\Post\ValueObject;
    
    use App\Domain\Post\Post;
    use Codefy\Domain\Aggregate\AggregateId;
    use Qubus\Exception\Data\TypeException;
    use Qubus\ValueObjects\Identity\Ulid;
    
    final class PostId extends Ulid implements AggregateId
    {
        /**
         * @throws TypeException
         */
        public static function fromString(string $postId): self
        {
            return new self(value: $postId);
        }
    
        public function aggregateClassName(): string
        {
            return Post::className();
        }
    }

Sample Usage
------------

    <?php

    $postId = PostId::generateAsString(); //returns a string representation of Uuid
    //or
    $postId = PostId::fromString('760b7c16-b28e-4d31-9f93-7a2f0d3a1c51'); //returns a PostId object
    //or
    $postId = PostId::fromNative('760b7c16-b28e-4d31-9f93-7a2f0d3a1c51'); //returns a ValueObject

Testing
-------

    <?php

    it(description: 'should be an instance of AggregateId.', closure: function () use ($postId) {
        Assert::assertInstanceOf(expected: AggregateId::class, actual: $postId);
    });
    
    it(description: 'should be cast to a string.', closure: function () use ($postId) {
        Assert::assertEquals(expected: '760b7c16-b28e-4d31-9f93-7a2f0d3a1c51', actual: (string)$postId);
    });
    
    it('should equal instances of the same type and value.', function () use ($postId) {
        $id = PostId::fromNative($postId->toNative());
    
        expect(value: $postId)->toEqual(expected: $id);
    });
    
    it('should not equal instances of the same type and value.', function () use ($postId) {
        $id = PostId::fromNative('d5f77025-63d5-43a1-966e-cfe4d576ebd5');
    
        expect(value: $postId)->not()->toEqual(expected: $id);
    });

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.