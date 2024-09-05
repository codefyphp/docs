In the previous section, we created our first value object, `PostId`. Before continuing on, we have a couple of other 
value objects to create: `Title` and `Content`. To keep it simple, we will have them extend a base value object, 
`Qubus\ValueObjects\StringLiteral\StringLiteral` and add a new `fromString` method.

Title
-----

    <?php

    use Qubus\Exception\Data\TypeException;
    use Qubus\ValueObjects\StringLiteral\StringLiteral;
    
    final class Title extends StringLiteral
    {
        /**
         * @throws TypeException
         */
        public static function fromString(string $title): self
        {
            return new self(value: $title);
        }
    }

Content
-------

    <?php

    use Qubus\Exception\Data\TypeException;
    use Qubus\ValueObjects\StringLiteral\StringLiteral;
    
    final class Content extends StringLiteral
    {
        /**
         * @throws TypeException
         */
        public static function fromString(string $content): self
        {
            return new self(value: $content);
        }
    }

`StringLiteral` has other methods to be aware of:

    <?php

    /**
     * Returns a String object given a PHP native string as parameter.
     *
     * @param  string $value
     * @return StringLiteral|ValueObject
     */
    public static function fromNative(): ValueObject;

    /**
     * Returns the value of the string.
     */
    public function toNative(): string;

    /**
     * Tells whether two strings are equal by comparing their values
     *
     * @param  ValueObject $string
     */
    public function equals(ValueObject $stringLiteral): bool;

    /**
     * Tells whether the String is empty
     */
    public function isEmpty(): bool;

Both `Title` and `Content` inherit the above methods.

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.