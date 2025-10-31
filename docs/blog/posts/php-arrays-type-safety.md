---
title: How to Implement Type Safety for PHP Arrays
date:
  created: 2025-10-28 09:30:00
  updated: 2025-10-29 07:30:00
authors: [nomadicjosh]
slug: type-safety-php-arrays
description: Implement type safety in PHP arrays with a custom ArrayList class. Enforce strict types, reduce bugs, and write cleaner, more reliable code.
---

# How to Implement Type Safety for PHP Arrays

I think about code often. Sometimes, I just close my eyes, think about the code I've written and the many 
ways to make it better. Just the other day, I started wondering about using DTO's and Value Objects 
as an option for better strict typing. Here is some of the code that popped up in my head:

<!-- more -->

## Example #1

```php
<?php

class UserObject
{
    public function __construct(
        protected string $id,
        protected string $email,
        protected string $firstName,
        protected string $middleName,
        protected string $lastName,
        protected string $address,
        protected string $city,
        protected string $state,
        protected string $postalCode
    ) {
    }
}
```

!!! note
    If you are interested in testing the code found in this article, or want to expand on it to use in your own projects, 
    you will need to install the following packages: `composer require qubus/support qubus/valueobjects`

Then, another thought came to mind on making this better using value objects:

## Example #2

```php
<?php

use Qubus\ValueObjects\Geography\Address;
use Qubus\ValueObjects\Person\Name;
use Qubus\ValueObjects\Web\EmailAddress;
use UserId;

class UserObject
{
    public function __construct(
        protected UserId $id,
        protected EmailAddress $email,
        protected Name $name,
        protected Address $address
    ) {
    }
}
```

Well, that seemed easy enough I thought, but then I started thinking about arrays. I remembered creating a class to 
handle arrays, but wondered if it was good enough.

This is the code I created for a previous project:

## Example #3

```php
<?php

declare(strict_types=1);

namespace App\Shared\ValueObject;

use JsonException;
use Qubus\ValueObjects\Util;
use Qubus\ValueObjects\ValueObject;

use function func_get_arg;
use function is_array;
use function json_encode;
use function sprintf;

use const JSON_THROW_ON_ERROR;

class ArrayLiteral implements ValueObject
{
    private array $value = [];

    public function __construct(array $data = [])
    {
        $this->value = $data;
    }

    /**
     * Returns an array object.
     */
    public static function fromNative(): self
    {
        $meta = func_get_arg(0);
        return new self($meta);
    }

    /**
     * Returns the value of the array.
     *
     * @return array
     */
    public function toNative(): array
    {
        return $this->value;
    }

    /**
     * Tells whether two arrays are equal by comparing their values.
     *
     * @param ArrayLiteral|ValueObject $object
     * @return bool
     */
    public function equals(ArrayLiteral|ValueObject $object): bool
    {
        if (false === Util::classEquals($this, $object)) {
            return false;
        }

        return $this->toNative() === $object->toNative();
    }

    /**
     * Tells whether the array is empty.
     *
     * @return bool
     */
    public function isEmpty(): bool
    {
        return empty($this->value);
    }

    /**
     * Returns the array value itself.
     *
     * @throws JsonException
     */
    public function __toString(): string
    {
        return json_encode($this->value, JSON_THROW_ON_ERROR);
    }
}
```

This code works well for the project I needed to create it for. But, in some circumstances, it is still lacking.

As I was doing some research, I came across the article entitled,
[Type Safety Done Right - PHP Array Hacking](https://developer.vonage.com/en/blog/type-safety-done-right-php-array-hacking).

As I read through this article several times, this stood out to me:

> I want to update the `ID` of something. And then... I have `$options`. Because they are options. But it's a plain PHP array. 
> What's in it? The function has no idea.

The author went on to explain:

> What's wrong with this code? If personal experience is anything to go by, four hours of 
> `xdebug` stepping to find out where an array key came from. We've got no idea what it's supposed to look like.

This resonated with me immediately. I can’t count the number of times I've tried to figure out which 
array the IoC container was complaining about when it couldn’t resolve a dependency. It was often a silly mistake on 
my part, but still incredibly frustrating not knowing exactly which dependency was causing the issue.

Needless to say, this sent me down a rabbit trail exploring how other languages handle arrays. PHP’s current approach 
works well enough, but at times it could benefit from a little more type safety.

In the `ArrayLiteral` class  posted above, the arrays passed into the constructor can contain anything — strings, integers, 
value objects, or even a mix of them. But what if you need an array that strictly contains elements of the same type?

## Array Objects and Primitive Types

That led me to the idea of using the `ArrayLiteral` class as a base, which could then be extended with more 
explicit typing. For example, what if we wanted to ensure that our code only accepted arrays of the `string` type? We 
could design something that looks like this:

### Example #4

```php
<?php

declare(strict_types=1);

namespace App\Shared\ValueObject;

use Qubus\Exception\Data\TypeException;

use function is_string;
use function sprintf;

class ArrayString extends ArrayLiteral
{
    /**
     * @param array<string, string> $values
     * @throws TypeException
     */
    public function __construct(array $values)
    {
        foreach ($values as $value) {
            if (!is_string($value)) {
                throw new TypeException(sprintf('%s must be a string.', $value));
            }
        }
        parent::__construct($values);
    }
}
```

#### Usage

```php
<?php

$strings = new ArrayString(['cat', 'dog', 'fish']);

print_r($strings->toNative());
```

#### Result

```terminaloutput
Array
(
    [0] => cat
    [1] => dog
    [2] => fish
)
```

Our `ArrayString` class still accepts an array of values, but the difference is that it does an extra check to make sure 
that the array only contains values of the `string` type. If not, it will throw a `TypeException`.

We can even be more explicit with our `ArrayString` class be declaring the type of values expected using a 
`variable-length argument`:

### Example #5

```php
<?php

declare(strict_types=1);

namespace App\Shared\ValueObject;

use function is_string;
use function sprintf;

class ArrayString extends ArrayLiteral
{
    /**
     * @param string ...$values
     */
    public function __construct(string ...$values)
    {
        parent::__construct($values);
    }
}
```

!!! note
    In this way, you can create the classes you need with the strict type or types that should be accepted (i.e. `stdClass ...$values`, `int ...$values`)

#### Usage

```php
<?php

$strings = new ArrayString('banana', 'orange', 'kiwi');

print_r($strings->toNative());
```

#### Result

```terminaloutput
Array
(
    [0] => banana
    [1] => orange
    [2] => kiwi
)
```

I think the best use case for something like this is to validate user input. Hopefully, this gives you some ideas on 
how to take this further.

## Jave's ArrayList

As I looked further into Java's `ArrayList` class, I really liked the type safety it provided. Here is an example of 
using `ArrayList` in Java:

```java
public class Main {

	public static void main(String[] args) {
		
		ArrayList<String> food = new ArrayList<String>();
		
		food.add("pizza");
		food.add("hamburger");
		food.add("hotdog");
		
		//food.set(0, "sushi");
		//food.remove(2);
		//food.clear();
		
		for(int i=0; i<food.size(); i++) {
			System.out.println(food.get(i));
		}
	}
}
```

When using the `ArrayList` class in Java, you must pass in an object type. In the example above, the object type is 
`String`, which means, the array must only contain elements that are `strings`. I was inspired by this and decided to 
mimic this functionality in PHP:

### Example #6

```php
<?php

declare(strict_types=1);

use OutOfRangeException;
use Qubus\Exception\Data\TypeException;
use Qubus\Support\Collection\ArrayCollection;

use function sprintf;

class ArrayList
{
    /** @var string */
    private string $type;

    /** @var array */
    private array $items = [];

    /**
     * Constructor.
     *
     * @param string $type The expected type of elements
     *                     (e.g. 'string', 'int', 'float', 'bool', 'array', 'object', 'MyClass').
     */
    public function __construct(string $type)
    {
        $this->type = $type;
    }

    /**
     * Add an element to the list.
     *
     * @param mixed $element
     * @throws TypeException
     */
    public function add(mixed $element): void
    {
        $this->assertType($element);
        $this->items[] = $element;
    }

    /**
     * Set an element at a specific index.
     *
     * @param int $index
     * @param mixed $element
     * @throws TypeException
     */
    public function set(int $index, mixed $element): void
    {
        $this->assertType($element);
        if (!isset($this->items[$index])) {
            throw new OutOfRangeException(sprintf("Index %s does not exist.", $index));
        }
        $this->items[$index] = $element;
    }

    /**
     * Get an element at a specific index.
     *
     * @param int $index
     * @return mixed
     */
    public function get(int $index): mixed
    {
        if (!isset($this->items[$index])) {
            throw new OutOfRangeException(sprintf("Index %s does not exist.", $index));
        }
        return $this->items[$index];
    }

    /**
     * Remove an element at a specific index.
     *
     * @param int $index
     */
    public function remove(int $index): void
    {
        if (!isset($this->items[$index])) {
            throw new OutOfRangeException(sprintf("Index %s does not exist.", $index));
        }
        array_splice($this->items, $index, 1);
    }

    /**
     * Get the size of the list.
     *
     * @return int
     */
    public function size(): int
    {
        return count($this->items);
    }

    /**
     * Type check helper.
     *
     * @param mixed $value
     * @throws TypeException
     */
    private function assertType(mixed $value): void
    {
        $expected = $this->type;
        $actual = get_debug_type($value);

        // Handle primitive types
        if (
                ($expected === 'int' && is_int($value)) ||
                ($expected === 'string' && is_string($value)) ||
                ($expected === 'float' && is_float($value)) ||
                ($expected === 'bool' && is_bool($value)) ||
                ($expected === 'array' && is_array($value)) ||
                ($expected === 'object' && is_object($value))
        ) {
            return;
        }

        // Handle specific class names
        if (class_exists($expected) && $value instanceof $expected) {
            return;
        }

        throw new TypeException(
            sprintf("Invalid type: expected %s, got %s.", $expected, $actual)
        );
    }
    
    /**
     * Clears the collection.
     * 
     * @return void
     */
    public function clear(): void
    {
        $this->items = [];
    }

    /**
     * Returns the items in the collection.
     *
     * @return ArrayCollection
     */
    public function collection(): ArrayCollection
    {
        return new ArrayCollection($this->items);
    }
}
```

With our `ArrayList` class in place, we can use it in the similar way to Java's class:

#### Usage

```php
<?php

use ArrayList;

$food = new ArrayList('string');

$food->add("pizza");
$food->add("hamburger");
$food->add("hotdog");

print_r($food->get(1));
```

#### Result

```terminaloutput
hamburger
```

Since Java's `ArrayList` returns a collection, we also mimic that functionality by adding the [`collection()`](../../digging-deeper/collections.md) method in 
our `ArrayList` class. I am still experimenting with the code and not sure if it is something I would implement in 
production - not as it stands anyway, but it was a great exercise in stretching my coding brain.

## Further Reading

If the article has either caused you angst or made you go, hmm, then I have some other resources you can check out to see 
what other developers have been thinking and writing about the subject.

* [PHP arrays have driven me mad](https://lukasrotermund.de/posts/php-array-object-benchmarking/)
* [The array anti-pattern](https://davegebler.com/post/php/the-array-anti-pattern)