---
summary: Create immutable PHP value objects for aggregate data with Qubus StringLiteral, typed constructors, native conversion, and value equality.
keywords: php-value-objects,domain-driven-design,string-literal
---

In the previous section, we created our first value object, `PostId`. Before continuing on, we have a couple of other 
value objects to create: `Title` and `Content`. To keep it simple, we will have them extend a base value object, 
`Qubus\ValueObjects\StringLiteral\StringLiteral` and add a new `fromString` method.

Title
-----

```php
<?php

use Domain\Post\ValueObject\Title;
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
```

Content
-------

```php
<?php

use Domain\Post\ValueObject\Content;
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
```

`StringLiteral` has other methods to be aware of:

```php
<?php

/**
 * Returns a String object given a PHP native string as parameter.
 *
 * @param  string $value
 * @return ValueObject
 */
public static function fromNative(): ValueObject;

/**
 * Returns the value of the string.
 */
public function toNative(): mixed;

/**
 * Tells whether two strings are equal by comparing their values
 *
 * @param ValueObject $object
 */
public function equals(ValueObject $object): bool;
```

Both `Title` and `Content` inherit the above methods.
