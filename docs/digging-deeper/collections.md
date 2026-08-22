---
title: Collections
sidebar_title: Collections
summary: Create and transform PHP collections with fluent methods for filtering, mapping, sorting, grouping, reducing, pagination, and array conversion.
keywords: php-collections,arraylist,collection-methods
order: 21
---

## Installation

```shell
composer require qubus/support
```

The `Qubus\Support\Collection\ArrayCollection` class provides a fluent way of working with arrays of data. We'll use 
the `Qubus\Support\Helpers\collect` helper to create a new collection instance from the array, run the `strtoupper` 
function on each element, and then remove all empty elements:

    <?php

    use function print_r;
    use Qubus\Support\Helpers\collect;

    $collect = new collect(['jim', 'dixon', '']);
    $data = $collect
        ->map(fn($item) => strtoupper($item))
        ->reject(fn ($item, $key) => empty($item));

    print_r($data->items());

**Result:** `[0 => "JIM", 1 => "DIXON"]`

## Creating Collections

Creating a collection is super easy by use the `collect` helper to create a new 
`Qubus\Support\Collection\ArrayCollection` instance and passing in an array like so:

    <?php
    
    use function Qubus\Support\Helpers\collect;
    
    $collect = new collect(['jim', 'dixon', '']);
    
    // or
    
    $collect = collect(['fname' => 'jim', 'lname' => 'dixon', 'mname' => '']);

## Methods

These are the following methods you can use to manipulate a collection:

### add()

The `add()` method adds an item to the end of a collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
    
    $collect = collect(['jim', 'dixon', '']);

    $collect->add('david');

    print_r($collect->all());

**Result:** `[0 => "jim", 1 => "dixon", 2 => "", 3 => "david"]`

### all()

The `all()` method returns the underlying array represented by the collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $collect = collect(['jim', 'dixon', '']);

    print_r($collect->all());

**Result:** `[0 => "jim", 1 => "dixon", 2 => ""]`

### column()

The `column()` method returns the values from the given property or method:

```php
<?php

use function print_r;
use Domain\User\ValueObject\UserId;

$userId = new UserId();

$collect = collect([$userId]);

print_r($collect->column('toNative'));
```

**Result:** `[0 => "01K5M0J9WZEF9R612J06QV05K8"]`

### contains()

The `contains()` method returns true if the collection contains the specified element:

    <?php

    return $collect->contains(element: 'dixon');

**Return Value:** `true`

### count()

The `count()` method returns the total number of items in the collection:

    <?php
    
    return $collect->count();

**Return Value:** `3`

### each()

The `each()` method applies the callback function to each item in the collection.

    <?php
    
    $collect->each(function (string $item, int $key) {
        // ...
    });

### filter()

The `filter()` method filters the collection items through the callable:

    <?php
    
    $data = $collect->filter(fn ($item, $key) => $item !== '');
    
    print_r($data->all());

**Result:** `[0 => "jim", 1 => "dixon"]`

### first()

The `first()` method gets the first item from the collection:

    <?php
    
    return $collect->first();

**Return Value:** `"jim"`

!!! warning "Empty Collection"
    `first()` will return null if the collection is empty.

### items()

The `items()` method is similar to [`all()`](#all) and [`toArray()`](#toarray):

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $collect = collect(['jim', 'dixon', '']);

    print_r($collect->items());

**Result:** `[0 => "jim", 1 => "dixon", 2 => ""]`

### last()

The `last()` method gets the last item from the collection:

    <?php
    
    return $collect->last();

**Return Value:** `""`

!!! warning "Empty Collection"
    `last()` will return null if the collection is empty.

### flip()

The `flip()` method swaps the collection's keys with their corresponding values:

    <?php
    
    print_r($collect->flip());

**Result:** `["jim" => 0, "dixon" => 1, "" => 2]`

### get()

The `get()` method retrieves the specified item from the collection by a given key. If the key does not exist, a 
`Qubus\Exception\Data\TypeException` is thrown:

    <?php
    
    return $collect->get(1);

**Return Value:** `"dixon"`

### flatten()

The `flatten()` method returns a new Collection instance containing a flattened array of items:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $collect = collect(['jane', ['john', 'frank']]);

    $data = $collect->flatten();

    print_r($data->all());

**Result:** `[0 => "jane", 1:0 => "john", 1:1 => "frank"]`

### groupBy()

The `groupBy()` method groups the collection's items by a given callback. The callback should return the value you wish to key the group by:

    <?php
    
    $collect = collect([
        ['type_id' => 'horror', 'book' => 'IT'],
        ['type_id' => 'horror', 'book' => 'The Shining'],
        ['type_id' => 'fantasy', 'book' => 'The Return of the King'],
    ]);

    $data = $collect->groupBy(fn($items) => $items['type_id']);

    print_r($data->all());

**Result:**

```text
 [
  "horror" => [
    0 => [
      "type_id" => "horror"
      "book" => "IT"
    ]
    1 => [
      "type_id" => "horror"
      "book" => "The Shining"
    ]
  ]
  
  "fantasy" => [
    2 => [
      "type_id" => "fantasy"
      "book" => "The Return of the King"
    ]
  ]
]
```

### isEmpty()

The `isEmpty()` method returns `true` if the collection is empty; otherwise, `false` is returned:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $collect = collect([]);

    return $collect->isEmpty();

**Return Value:** `true`

### keys()

The `keys()` method returns all the collection's keys:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $collect = collect([
        'book-100' => ['type_id' => 'horror', 'book' => 'IT'],
        'book-200' => ['type_id' => 'horror', 'book' => 'The Shining'],
        'book-300' => ['type_id' => 'fantasy', 'book' => 'The Return of the King'],
    ]);

    $keys = $collect->keys();

    print_r($keys->all());

**Result:** `[0 => "book-100", 1 => "book-200", 2 => "book-300"]`

### map()

The `map()` method iterates through the collection and passes each value to the given callback. The callback is free 
to modify the item and return it, thus forming a new collection of modified items:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $collect = collect([1, 2, 3, 4, 5]);

    $multiplied = $collect->map(function (int $item) {
        return $item * 2;
    });

    print_r($multiplied->all());

**Result:** `[0 => 2, 1 => 4, 2 => 6, 3 => 8, 4 => 10]`

### merge()

The `merge()` method merges the given array or collection with the original collection. If a string key in the given 
items matches a string key in the original collection, the given item's value will overwrite the value in the original 
collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['cat' => 'lion', 'dog' => 'german shepherd', 'feline' => 'minx'];

    $collect = collect($array);

    $merge = $collect->merge(['dog' => 'golden retriever', 'duck' => 'mallard']);

    print_r($merge->all());

**Result:** `["cat" => "lion", "dog" => "golden retriever", "feline" => "minx", "duck" => "mallard"]`

If the given item's keys are numeric, the values will be appended to the end of the collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['lion', 'german shepherd'];

    $collect = collect($array);

    $merge = $collect->merge(['golden retriever', 'mallard']);

    print_r($merge->all());

**Result:** `[0 => "lion", 1 => "german shepherd", 2 => "golden retriever", 3 => "mallard"]`

### nth()

The `nth()` method creates a new collection consisting of every n-th element:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    $collect = collect($array);

    $data = $collect->nth(step: 4);

    print_r($data->all());

**Result:** `[0 => 1, 1 => 5, 2 => 9]`

You may optionally pass a starting offset as the second argument:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    $collect = collect($array);

    $data = $collect->nth(step: 4, offset: 2);

    print_r($data->all());

**Result:** `[0 => 3, 1 => 7]`

### pop()

The `pop()` method removes and returns the last item from the collection. If the collection is empty, `null` will be returned:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    $collect = collect($array);

    return $collect->pop();

**Return Value:** `9`

    <?php
    
    print_r($collect->all());

**Return Value:** `[0 => 1, 1 => 2, 2 => 3, 3 => 4, 4 => 5, 5 => 6, 6 => 7, 7 => 8]`

### push()

The `push()` method appends an item to the end of the collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    $collect = collect($array);

    $push = $collect->push(10);

    print_r($push->all());

**Result:** `[0 => 1, 1 => 2, 2 => 3, 3 => 4, 4 => 5, 5 => 6, 6 => 7, 7 => 8, 8 => 9, 9 => 10]`

### put()

The `put()` method sets the given key and value in the collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['canine' => 'german shepherd', 'feline' => 'cat'];

    $collect = collect($array);

    $put = $collect->put('fowl', 'duck');

    print_r($put->all());

**Result:** `["canine" => "german shepherd", "feline" => "cat", "fowl" => "duck"]`

### reject()

The `reject()` method filters the collection using the given closure. The closure should return `true` if the item 
should be removed from the resulting collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['canine' => 'german shepherd', 'feline' => 'cat', 'fowl' => 'duck'];

    $collect = collect($array);

    $filtered = $collect->reject(fn(string $item, string $key) => $key === 'feline');

    print_r($filtered->all());

**Result:** `[0 => "german shepherd", 1 => "duck"]`

!!! note
    For the inverse of the `reject()` method, see the [`filter`](#filter) method.

### reverse()

The `reverse` method reverses the order of the collection's items, preserving the original keys:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['canine' => 'german shepherd', 'feline' => 'cat', 'fowl' => 'duck'];

    $collect = collect($array);

    $reversed = $collect->reverse();

    print_r($reversed->all());

**Result:** `["fowl" => "duck", "feline" => "cat", "canine" => "german shepherd"]`

### search()

The `search()` method searches the collection for the given value and returns its key if found. If the item is not found, 
`false` is returned:

    <?php
    
    use function Qubus\Support\Helpers\collect;
        
    $array = ['canine' => 'german shepherd', 'feline' => 'cat', 'fowl' => 'duck'];

    $collect = collect($array);

    return $collect->search('cat');

**Return Value:** `"feline"`

### shift()

The `shift()` method removes and returns the first item from the collection:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['canine' => 'german shepherd', 'feline' => 'cat', 'fowl' => 'duck'];

    $collect = collect($array);

    return $collect->shift();

**Return Value:** `"german shepherd"`

    <?php

    print_r($collect->all());

**Result:** `['feline' => 'cat', 'fowl' => 'duck']`

### slice()

The `slice()` method returns a slice of the collection starting at the given index:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['canine' => 'german shepherd', 'feline' => 'cat', 'fowl' => 'duck'];

    $collect = collect($array);

    $slice = $collect->slice(1);

    print_r($slice->all());

**Result:** `['feline' => 'cat', 'fowl' => 'duck']`

If you would like to limit the size of the returned slice, pass the desired size as the second argument to the method:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['canine' => 'german shepherd', 'feline' => 'cat', 'fowl' => 'duck'];

    $collect = collect($array);

    $slice = $collect->slice(1, 1);

    print_r($slice->all());

**Result:** `['feline' => 'cat']`

### sort()

The `sort()` method sorts the collection. The sorted collection keeps the original array keys, so in the following 
example, we will use the [`values()`](#values) method to reset the keys to consecutively numbered indexes:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = [9, 5, 8, 7, 3, 6, 2, 1, 0, 4];

    $collect = collect($array);

    $sorted = $collect->sort();

    print_r($sorted->values()->all());

**Result:** `['feline' => 'cat']`

!!! warning "Advanced Sorting"
    If your sorting needs are more advanced, you may pass a `callback` to sort with your own algorithm. Refer to the 
    PHP documentation on [`uasort`](https://www.php.net/manual/en/function.uasort.php), which is what the collection's 
    sort method utilizes internally.

### sortByKey()

The `sortByKey` method sorts the collection by keys. The sorted collection keeps the original array keys, so in the 
following example we will use the [`values()`](#values) method to reset the keys to consecutively numbered indexes:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = [9, 5, 8, 7, 3, 6, 2, 1, 0, 4];

    $collect = collect($array);

    $sorted = $collect->sortByKey();

    print_r($sorted->values()->all());

**Result:** `[0 => 9, 1 => 5, 2 => 8, 3 => 7, 4 => 3, 5 => 6, 6 => 2, 7 => 1, 8 => 0, 9 => 4]`

In addition, you can pass in a `callback`:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = ['id' => '01K5KW3982E68BYVJX5HNWJ4MS', 'lname' => 'Elroy', 'fname' => 'John', 'mname' => 'Edward'];

    $collect = collect($array);

    $sorted = $collect->sortByKey('strnatcasecmp');

    print_r($sorted->all());

**Result:** `["fname" => "John", "id" => "01K5KW3982E68BYVJX5HNWJ4MS", "lname" => "Elroy", "mname" => "Edward"]`

!!! warning "Callback With `uksort`"
    The `callback` must be a comparison function that returns an integer less than, equal to, or greater than zero. 
    Refer to the PHP documentation on [`uksort`](https://www.php.net/manual/en/function.uksort.php), which is what the 
    collection's `sortByKey` method utilizes internally.

### sum()

The `sum()` method returns the sum of all items in the collection:

    <?php
    
    use function Qubus\Support\Helpers\collect;
        
    $array = [8, 9, 10, 11];

    $collect = collect($array);

    return $collect->sum();

**Return Value:** `38`

If the collection contains nested arrays, you may pass your own closure to determine which values of the collection 
to sum:

    <?php
    
    use function Qubus\Support\Helpers\collect;
        
    $array = [
        ['name' => 'Chair', 'colors' => ['Black']],
        ['name' => 'Desk', 'colors' => ['Black', 'Mahogany']],
        ['name' => 'Bookcase', 'colors' => ['Red', 'Beige', 'Brown']],
    ];

    $collect = collect($array);

    return $collect->sum(fn (array $products) => count($products['colors']));

**Return Value:** `6`

### toArray()

The `toArray()` method returns the same as both the [`all()`](#all) and [`items()`](#items) methods:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $collect = collect(['jim', 'dixon', '']);

    print_r($collect->toArray());

**Result:** `[0 => "jim", 1 => "dixon", 2 => ""]`

### values()

The `values()` method returns a new collection with the keys reset to consecutive integers:

    <?php
    
    use function print_r;
    use function Qubus\Support\Helpers\collect;
        
    $array = [
        ['name' => 'Chair', 'colors' => ['Black']],
        ['name' => 'Desk', 'colors' => ['Black', 'Mahogany']],
        ['name' => 'Bookcase', 'colors' => ['Red', 'Beige', 'Brown']],
    ];

    $collect = collect($array);

    $values = $collect->values();

    print_r($values->all());

**Result:**

```text
[
  0 => [
    "name" => "Chair"
    "colors" => [
      0 => "Black"
    ]
  ]
  1 => [
    "name" => "Desk"
    "colors" => [
      0 => "Black"
      1 => "Mahogany"
    ]
  ]
  2 => [
    "name" => "Bookcase"
    "colors" => [
      0 => "Red"
      1 => "Beige"
      2 => "Brown"
    ]
  ]
]
```


