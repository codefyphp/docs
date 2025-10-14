---
title: Arrays
sidebar_title: Arrays
order: 28
---

The `Qubus\Support\ArrayHelper` class is a set of helper functions for working with arrays. Instead of instantiating 
the class, you can use Codefy's global property:

    <?php
    
    $helper = Codefy\Framework\Codefy::$PHP->array;

## assocToKeyVal()

Converts a multidimensional associative array into an array of key => values with the provided field names.

    <?php

    use function print_r;

    $array = [
        ['type_id' => 'horror', 'book' => 'IT'],
        ['type_id' => 'sci-fi', 'book' => 'Dune'],
        ['type_id' => 'fantasy', 'book' => 'The Return of the King'],
    ];
    
    print_r($helper->assocToKeyVal($array, 'type_id', 'book'));

**Result:** 

```text
[
  "horror" => "IT"
  "sci-fi" => "Dune"
  "fantasy" => "The Return of the King"
]
```

!!! warning "Duplicate Keys"
    Please note that duplicate keys will get collapse and the last value in the key will be the one used.

## average()

The `average()` method takes all values of an array and returns the average value.

    <?php

    $array = [1, 2, 4, 8];
    
    echo $helper->average($array);

**Result:** `3.75`

## delete()

The `delete()` method deletes the element of the given array using dot-notation. Returns `true` if the key was deleted, 
`false` if the key didn't exist. If you pass an array of keys, the return value will be an array with the result of all 
requested deletes.

    <?php

    use function print_r;

    $person = [
        "name" => "Jack",
        "age" => "21",
        "location" => [
            "city" => "Pittsburgh",
            "state" => "PA",
            "country" => "US"
        ]
    ];
    
    print_r($helper->delete($person, 'age'));
    // deleted $person['name'] from the array, returns true

    print_r($helper->delete($person, 'location.state'));
    // deleted $person['location']['state'] from the array, returns true

    print_r($helper->delete($person, ['name', 'location.nowhere']));
    // returns ['name' => true, 'location.nowhere' => false]

## flatten()

The `flatten()` method flattens a multidimensional array (both associative and indexed) down into a 1 dimensional array.

    <?php

    use function print_r;

    $indexed = [
        ["a"],
        ["b"],
        ["c"],
    ];

    print_r($helper->flatten($indexed));

**Result:**
```text
[
    [0:0] => a
    [0:1] => b
    [0:2] => c
]
```

## flattenAssoc()

The `flattenAssoc()` method flattens a multi-dimensional associative array down into a 1 dimensional associative array.

    <?php

    use function print_r;

    $array = [
        [
            "name" => "Jack",
            "age"  => 21
        ],
        [
            "name" => "Jill",
            "age"  => 23
        ]
    ];

    print_r($helper->flattenAssoc($array));

**Result:**

```text
[
    [0:name] => Jack
    [0:age]  => 21
    [1:name] => Jill
    [1:age]  => 23
]
```

## filterKeys()

The `filterKeys()` method filters a given array to a set of keys. It returns an array that contains only the items 
whose keys are in the `$keys` array. Can also remove the specified `$keys` from an array.

    <?php

    use function print_r;

    $array = [
        "fname" => "Joshua",
        "lname" => "Parker",
        "project_name" => "CodefyPHP",
        "project_type" => "Framework",
    ];

    print_r($helper->filterKeys(array: $array, keys: ['project_name', 'fname']));

**Result:**

```text
[
  "project_name" => "CodefyPHP"
  "fname" => "Joshua"
]
```

    <?php

    // remove some keys
    print_r($helper->filterKeys(array: $array, keys: ['fname', 'lname'], remove: true));

**Result:**

```text
[
  "project_name" => "CodefyPHP"
  "project_type" => "Framework"
]
```

## filterPrefixed()

The `filterPrefixed()` method filters the array on a prefix. It returns an array where the key starts with the 
specified prefix.

    <?php

    use function print_r;

    $array = [
        "fname" => "Joshua",
        "lname" => "Parker",
        "project_name" => "CodefyPHP",
        "project_type" => "Framework",
    ];

    print_r($helper->filterPrefixed(array: $array, prefix: 'project_'));

**Result:**

```text
[
  "name" => "CodefyPHP"
  "type" => "Framework"
]
```

    <?php

    // keep the prefix
    print_r($helper->filterPrefixed(array: $array, prefix: 'project_', removePrefix: false));

**Result:**

```text
[
  "project_name" => "CodefyPHP"
  "project_type" => "Framework"
]
```

## filterRecursive()

The `filterRecursive()` method provides a recursive version of PHP's 
[`array_filter()`](https://www.php.net/manual/en/function.array-filter.php) function. Like its counterpart, you can 
optionally pass a callback function to determine what should be filtered.

    <?php

    use function print_r;

    $array = [
        "project_name" => "CodefyPHP",
        "project_type" => "Framework",
        'info' => [
            0 => ['data' => 'a value'],
            1 => ['data' => ''],
            2 => ['data' => 0],
        ],
    ];

    print_r($helper->filterRecursive(array: $array));

**Result:**

```text
[
  "project_name" => "CodefyPHP"
  "project_type" => "Framework"
  "info" => [
    0 => [
      "data" => "a value"
    ]
  ]
]
```

    <?php
    
    print_r($helper->filterRecursive(array: $array, callback: fn($item) => $item !== ''));

**Result:**

```text
[
  "project_name" => "CodefyPHP"
  "project_type" => "Framework"
  "info" => [
    0 => [
      "data" => "a value"
    ]
    1 => [
      "data" => ""
    ]
    2 => [
      "data" => 0
    ]
  ]
]
```

## filterSuffixed()

The `filterSuffixed` method filters the array on a suffix. It returns an array where the key ends with the specified 
suffix.

    <?php

    use function print_r;

    $array = [
        "name_1" => "Joshua",
        "surname_1" => "Parker",
        "name_2" => "Johnnie",
        "surname_2" => "Lee",
    ];

    print_r($helper->filterSuffixed(array: $array, suffix: '_1'));

**Result:**

```text
[
  "name" => "Joshua"
  "surname" => "Parker"
]
```

    <?php
    
    // keep the suffix
    print_r($helper->filterSuffixed(array: $array, suffix: '_1', removeSuffix: false));

**Result:**

```text
[
  "name_1" => "Joshua"
  "surname_1" => "Parker"
]
```

## get()

The `get()` method returns the element of the given array using dot-notation, or a default if it is not set.

    <?php

    $person = [
        "name" => "Jack",
        "age" => "21",
        "location" => [
            "city" => "Pittsburgh",
            "state" => "PA",
            "country" => "US"
        ]
    ];

    echo $helper->get(array: $person, key: 'name', default: 'Unknown name.');
    // Result: Jack
    echo $helper->get(array: $person, key: 'job', default: 'Unknown job.');
    // Result: Unknown Job.

    // use dot notation
    echo $helper->get(array: $person, key: 'location.city', default: 'Unknown city.');
    // Result: Pittsburgh

## inArrayRecursive()

The `inArrayRecursive()` method checks whether a value is in an array recursively.

    <?php

    $array = ['one' => 1, 2, 3, [56], 87];

    echo $helper->inArrayRecursive(needle: 56, haystack: $array);
    // Result: true
    echo $helper->inArrayRecursive(needle: '87', haystack: $array, strict: true);
    // Result: false
    echo $helper->inArrayRecursive(needle: 87, haystack: $array, strict: true);
    // Result: true

## insert()

The `insert()` method is mainly an [`array_splice`](https://www.php.net/manual/en/function.array-splice.php) alias with 
added error checking.

    <?php

    use function print_r;

    $array = ['CodefyPHP', 'Symfony'];

    // Add one value starting at position `0`
    $helper->insert($array, ['Codeigniter'], 0);
    print_r($array);

**Result:**

```text
[
  0 => "Codeigniter"
  1 => "CodefyPHP"
  2 => "Symfony"
]
```

    <?php
    
    // Add mutiliple values starting at position `1`
    $helper->insert($array, ['CakePHP', 'Yii2'], 1);
    print_r($array);

**Result:**

```text
[
  0 => "Codeigniter"
  1 => "CakePHP"
  2 => "Yii2"
  3 => "CodefyPHP"
  4 => "Symfony"
]
```

    <?php
    
    // Add an array starting at position `0`
    $helper->insert($array, [ ['Laminas', 'FuelPHP'] ], 0);
    print_r($array);

**Result:**

```text
[
  0 => [
    0 => "Laminas"
    1 => "FuelPHP"
  ]
  1 => "Codeigniter"
  2 => "CakePHP"
  3 => "Yii2"
  4 => "CodefyPHP"
  5 => "Symfony"
]
```
!!! warning "Bool Return"
    The original array is edited by reference, only boolean success is returned.

## insertAssoc()

The `insertAssoc()` method inserts elements into an associative array, at the specified position.

    <?php

    use function print_r;

    $array = ['name' => 'Jack', 'surname' => 'Reacher'];

    // Add one value starting at position `1`
    $helper->insertAssoc($array, ['middle' => 'P.'], 1);
    print_r($array);

**Result:**

```text
[
  "name" => "Jack"
  "middle" => "P."
  "surname" => "Reacher"
]
```

!!! warning "Bool Return"
    The original array is edited by reference, only boolean success is returned.

## insertAfterKey()

The `insertAfterKey()` method adds an element to an array after the key specified.

    <?php

    use function print_r;

    $array = ['CodefyPHP', 'Symfony'];

    $helper->insertBeforeKey($array, ['Codeigniter'], 1);
    print_r($array);

**Result:**

```text
[
  0 => "CodefyPHP"
  1 => "Symfony"
  2 => "Codeigniter"
]
```

!!! warning "Bool Return"
    The original array is edited by reference, only boolean success is returned.

## insertAfterValue()

The `insertAfterValue()` method adds an element to an array after the value specified.

    <?php

    use function print_r;

    $array = ['CodefyPHP', 'Symfony'];

    $helper->insertAfterValue($array, ['Codeigniter'], 'CodefyPHP');
    print_r($array);

**Result:**

```text
[
  0 => "CodefyPHP"
  1 => "Codeigniter"
  2 => "Symfony"
]
```

## insertBeforeKey()

The `insertBeforeKey()` method adds an element to an array before the key specified.

    <?php

    use function print_r;

    $array = ['CodefyPHP', 'Symfony'];

    $helper->insertBeforeKey($array, ['Codeigniter'], 1);
    print_r($array);

**Result:**

```text
[
  0 => "CodefyPHP"
  1 => "Codeigniter"
  2 => "Symfony"
]
```

!!! warning "Bool Return"
    The original array is edited by reference, only boolean success is returned.
    
## insertBeforeValue()

The `insertBeforeValue()` method adds an element to an array before the value specified.

    <?php

    use function print_r;

    $array = ['CodefyPHP', 'Symfony'];

    $helper->insertBeforeValue($array, ['Codeigniter'], 'CodefyPHP');
    print_r($array);

**Result:**

```text
[
  0 => "Codeigniter"
  1 => "CodefyPHP"
  2 => "Symfony"
]
```

!!! warning "Bool Return"
    The original array is edited by reference, only boolean success is returned.

## keyExists()

The `keyExists()` method checks if a dot-notated key exists in an array.

    <?php

    $person = [
        "name" => "Jack",
        "age" => "21",
        "location" => [
            "city" => "Pittsburgh",
            "state" => "PA",
            "country" => "US"
        ]
    ];

    echo $helper->keyExists(array: $person, key: 'location.city');
    // Result: true

    echo $helper->keyExists(array: $person, key: 'location.nowhere');
    // Result: false

## keyValToAssoc()

The `keyValToAssoc()` method converts an array of key => values into a multidimensional associative array with the 
provided field names.

    <?php

    use function print_r;

    $array = ['Jack' => 21, 'Jill' => 23];

    print_r($helper->keyValToAssoc(array: $array, keyField: 'name', valField: 'age'));

**Result:**

```text
[
  0 => [
    "name" => "Jack"
    "age" => 21
  ]
  1 => [
    "name" => "Jill"
    "age" => 23
  ]
]
```

## merge()

The `merge()` method merges 2 arrays recursively, differs in 2 important ways from [`array_merge_recursive()`](https://www.php.net/manual/en/function.array-merge-recursive.php):

- When there's 2 different values and not both arrays, the latter value overwrites the earlier instead of merging both into an array. 
- Numeric keys that don't conflict aren't changed, only when a numeric key already exists is the value added using 
[`array_push()`](https://www.php.net/manual/en/function.array-push.php).

```php
<?php

use function print_r;

$arr1 = [
    'one' => 1,
    2,
    3,
    [
        56
    ],
    87
];

$arr2 = [
    27,
    90,
    [
        'give_me' => 'bandwidth'
    ],
    '90',
    'php',
];

print_r($helper->merge($arr1, $arr2));
```

**Result:**

```text
[
  "one" => 1
  0 => 2
  1 => 3
  2 => [
    0 => 56
  ]
  3 => 87
  4 => 27
  5 => 90
  6 => [
    "give_me" => "bandwidth"
  ]
  7 => "90"
  8 => "php"
]
```

## mergeAssoc()

The `mergeAssoc()` method merges 2 or more arrays recursively, differs in 2 important ways from [`array_merge_recursive()`](https://www.php.net/manual/en/function.array-merge-recursive.php):

- When there's 2 different values and not both arrays, the latter value overwrites the earlier instead of merging both into an array.
- Numeric keys aren't changed.

```php
<?php

use function print_r;

$arr1 = [
    'one' => 1,
    2 => 2,
    3 => 3,
    4 => [
        56
    ],
    5 => 87
];

$arr2 = [
    1 => 27,
    2 => 90,
    4 => [
        'give_me' => 'bandwidth'
    ],
    6 => '90',
    7 => 'php',
];

print_r($helper->mergeAssoc($arr1, $arr2));
```

**Result:**

```text
[
  "one" => 1
  2 => 90
  3 => 3
  4 => [
    0 => 56
    "give_me" => "bandwidth"
  ]
  5 => 87
  1 => 27
  6 => "90"
  7 => "php"
]
```

## multiSort()

The `multiSort()` method sorts a multi-dimensional array by multiple values.

    <?php

    use function print_r;

    $collection = [
        'i5' => [
            'name' => 'Carl',
            'age' => 17,
            'points' => 30,
            'arr' => [
                    'key' => 10,
            ],
        ],
        'i7' => [
            'name' => 'carl',
            'age' => 17,
            'points' => 20,
            'arr' => [
                    'key' => 10,
            ],
        ],
        'i2' => [
            'name' => 'Bert',
            'age' => 20,
            'points' => 30,
            'arr' => [
                    'key' => 10,
            ],
        ],
    ];

    $collection = $helper->multisort(
        array: $collection,
        conditions: [
            'name' => SORT_ASC,
            'points' => [SORT_ASC, SORT_NUMERIC],
            'age' => [SORT_ASC, SORT_NUMERIC]
        ],
        ignoreCase: true
    );

    print_r($collection);

**Result:**

```text
[
  "i2" => [
    "name" => "Bert"
    "age" => 20
    "points" => 30
    "arr" => [
      "key" => 10
    ]
  ]
  "i7" => [
    "name" => "carl"
    "age" => 17
    "points" => 20
    "arr" => [
      "key" => 10
    ]
  ]
  "i5" => [
    "name" => "Carl"
    "age" => 17
    "points" => 30
    "arr" => [
      "key" => 10
    ]
  ]
]
```

## nextByKey()

The `nextByKey()` method allows you to fetch the key or the value of the next element of an array, given an existing 
key value.

    <?php

    $array = [2 => 'A', 4 => '2', 6 => 'C'];

    echo $helper->nextByKey(array: $array, key: 1);
    // returns false, there is no key `1` in the array

    echo $helper->nextByKey(array: $array, key: 6);
    // returns null, there is no next key after `6`

    echo $helper->nextByKey(array: $array, key: '2', getValue: false, strict: true);
    // returns false, there is no key '2' in the array, only 2

    echo $helper->nextByKey(array: $array, key: 4);
    // returns 6, it's the key in the array after key `4`

    echo $helper->nextByKey(array: $array, key: 4, getValue: true);
    // returns 'C', it's the value the next key in the array points to

## nextByValue()

The `nextByValue()` method allows you to fetch the key or the value of the next element of an array, given an existing 
element value.

    <?php

    $array = [2 => 'A', 4 => '2', 6 => 'C'];

    echo $helper->nextByValue(array: $array, value: 'Z');
    // returns false, there is no value `Z` in the array

    echo $helper->nextByValue(array: $array, value: 'C');
    // returns null, there is no next value after `C`

    echo $helper->nextByValue(array: $array, value: 2, getValue: false, strict: true);
    // returns false, there is no value 2 in the array, only '2'

    echo $helper->nextByValue(array: $array, value: '2');
    // returns 'C', it's the value the next key in the array points to

    echo $helper->nextByValue(array: $array, value: '2', getValue: false);
    // returns 6, it's the key of the next array element

## pluck()

The `pluck()` method plucks values from a collection of arrays or objects.

    <?php

    use function print_r;

    $person = [
        [
            'id' => 1,
            "name" => "Jack",
            "age" => "21",
        ],
        [
            'id' => 2,
            'name' => "Jill",
            "age" => "23",
        ],
    ];

    // Get an array of id's
    print_r($helper->pluck(array: $person, key: 'id'));
    // Result: [0 => 1, 1 => 2]

    // Get an array of names with the id as the index
    print_r($helper->pluck(array: $person, key: 'name', index: 'id'));
    // Result: [1 => "Jack", 2 => "Jill"]

## previousByKey()

The `previousByKey()` method allows you to fetch the key or the value of the previous element of an array, 
given an existing key value.

    <?php

    $array = [2 => 'A', 4 => '2', 6 => 'C'];

    echo $helper->previousByKey(array: $array, key: 1);
    // returns false, there is no key 1 in the array

    echo $helper->previousByKey(array: $array, key: 2);
    // returns null, there is no previous key

    echo $helper->previousByKey(array: $array, key: '2', getValue: false, strict: true);
    // returns false, there is no key '2' in the array, only 2

    echo $helper->previousByKey(array: $array, key: 4);
    // returns 2, it's the key in the array before key 4

    echo $helper->previousByKey(array: $array, key: 4, getValue: true);
    // returns 'A', it's the value the previous key in the array points to

## previousByValue()

The `previousByValue()` method allows you to fetch the key or the value of the previous element of an array, given an 
existing element value.

    <?php

    $array = [2 => 'A', 4 => '2', 6 => 'C'];

    echo $helper->previousByValue(array: $array, value: 'Z');
    // returns false, there is no value 'Z' in the array

    echo $helper->previousByValue(array: $array, value: 'A');
    // returns null, there is no previous value

    echo $helper->previousByValue(array: $array, value: 2, getValue: false, strict: true);
    // returns false, there is no value 2 in the array, only '2'

    echo $helper->previousByValue(array: $array, value: '2');
    // returns 'A', it's the value the previous key in the array points to

    echo $helper->previousByValue(array: $array, value: '2', getValue: false);
    // returns 2, it's the key of the previous array element

## reindex()

The `reindex()` method recursively re-indexes the numeric keys of an array. It will not alter string keys.

    <?php

    use function print_r;

    $array = [2 => 'A', 'three' => '7', 4 => '2', 6 => 'C'];

    print_r($helper->reindex(arr: $array));

**Result:**

```text
[
  0 => "A"
  "three" => "7"
  1 => "2"
  2 => "C"
]
```

## removePrefixed()

The `removePrefixed()` method removes values from an array if they match a given prefix.

    <?php

    use function print_r;

    $array = [
        "fname" => "Joshua",
        "lname" => "Parker",
        "project_name" => "CodefyPHP",
        "project_type" => "Framework",
    ];

    print_r($helper->removePrefixed(array: $array, prefix: 'project'));

**Result:**

```text
[
  "fname" => "Joshua"
  "lname" => "Parker"
]
```

## removeSuffixed()

The `removeSuffixed()` method removes values from an array if they match a given suffix.

    <?php

    use function print_r;

    $array = [
        "name_1" => "Joshua",
        "surname_1" => "Parker",
        "name_2" => "Johnnie",
        "surname_2" => "Lee",
    ];

    print_r($helper->removeSuffixed(array: $array, suffix: '_1'));

**Result:**

```text
[
  "name_2" => "Johnnie"
  "surname_2" => "Lee"
]
```

## replaceKey()

The `replaceKey()` method replaces key names in an array by names in the `$replace` parameter.

    <?php

    use function print_r;

    $array = [
        "name_1" => "Joshua",
        "surname_1" => "Parker",
        "name_2" => "Johnnie",
        "surname_2" => "Lee",
    ];

    print_r($helper->replaceKey(source: $array, replace: ['surname_1' => 'lname_1', 'surname_2' => 'lname_2']));

**Result:**

```text
[
  "name_1" => "Joshua"
  "lname_1" => "Parker"
  "name_2" => "Johnnie"
  "lname_2" => "Lee"
]
```

## reverseFlatten()

The `reverseFlatten()` method unflattens a flattened multidimensional array (both associative and indexed) into 
its original form.

    <?php

    use function print_r;

    $array = [
        '0_name' => 'James',
        '0_age'  => 24,
        '1_name' => 'John',
        '1_age'  => 34,
    ];

    print_r($helper->reverseFlatten(array: $array, glue: '_'));

**Result:**

```text
[
  0 => [
    "name" => "James"
    "age" => 24
  ]
  1 => [
    "name" => "John"
    "age" => 34
  ]
]
```

## search()

The `search()` method searches the array for a given value and returns the corresponding key or default value.

- If `$recursive` is set to true, then the search method will return a delimiter-notated key using `$delimiter`.

```php
<?php

use function var_dump;

$array = [
    'one' => 1,
    'two' => 2,
    'three' => [
        'a' => 4,
        'b' => 'foo'
    ],
    'four',
    [
        null,
        [
            null,
            null,
            null,
            ['deep']
        ]
    ],
];

echo $helper->search(array: $array, value: 1);
// return: one

echo $helper->search(array: $array, value: 'four');
// return: 0

var_dump($helper->search(array: $array, value: 5));
// return: null

echo $helper->search(array: $array, value: 4, default: null, recursive: true);
// return: three.a

var_dump($helper->search(array: $array, value: '4', default: null, recursive: true, delimiter: '.', strict: true));
// return: null

echo $helper->search(array: $array, value: 'deep', default: null, recursive: true);
// return: 1.1.3.0
```

## set()

The `set()` method sets the element of the given array using dot-notation.

    <?php

    use function print_r;

    $person = [
        "name" => "Jack",
        "age" => "21",
        "location" => [
            "city" => "Pittsburgh",
            "state" => "PA",
            "country" => "US"
        ]
    ];

    $helper->set($person, 'name', 'John');

    print_r($person);

**Result:**

```text
[
  "name" => "John"
  "age" => "21"
  "location" => [
    "city" => "Pittsburgh"
    "state" => "PA"
    "country" => "US"
  ]
]
```

    <?php
    
    $helper->set($person, 'location.city', 'Philadelphia');
    
    print_r($person);

**Result:**

```text
[
  "name" => "John"
  "age" => "21"
  "location" => [
    "city" => "Philadelphia"
    "state" => "PA"
    "country" => "US"
  ]
]
```

    <?php
    
    // or set multiple values in one go
    $helper->set($person, ["name" => "John", "location.city" => "Philadelphia"]);

!!! warning
    The original array is edited by reference.

## sort()

The `sort()` method sorts a multidimensional array by its values.

    <?php

    use function print_r;

    $array = [
        [
            'info' => [
                'pet' => [
                    'type' => 'dog',
                ]
            ],
        ],

        [
            'info' => [
                'pet' => [
                    'type' => 'fish',
                ]
            ],
        ],

        [
            'info' => [
                'pet' => [
                    'type' => 'cat',
                ]
            ],
        ]
    ];

    print_r($helper->sort(array: $array, key: 'info.pet.type', order: 'asc', sortFlags: SORT_REGULAR));

**Result:**

```text
[
  0 => [
    "info" => [
      "pet" => [
        "type" => "cat"
      ]
    ]
  ]
  1 => [
    "info" => [
      "pet" => [
        "type" => "dog"
      ]
    ]
  ]
  2 => [
    "info" => [
      "pet" => [
        "type" => "fish"
      ]
    ]
  ]
]
```

## subset()

Similar to [`filterKeys()`](#filterkeys), the `subset()` method uses the values in `$keys` to access this array and return the 
associated values. The difference is that `subset()` returns all requested keys, providing `$default` for any missing keys.

This method uses [`get()`](#get) and [`set()`](#set) internally, so `$keys` may contain dotted notation.

    <?php

    use function print_r;

    $array = [
        'user' => [
            'fname' => 'Joshua',
            'lname' => 'Parker',
        ],
        'project' => [
            "name" => "CodefyPHP",
            "type" => "Framework",
        ]
    ];

    print_r($helper->subset(array: $array, keys: ['project.name', 'user.fname']));

**Result:**

```text
[
  "project" => [
    "name" => "CodefyPHP"
  ]
  "user" => [
    "fname" => "Joshua"
  ]
]
```

or:

    <?php
    
    print_r($helper->subset(array: $array, keys: ['project.name', 'project.manager']));

**Result:**

```text
[
  "project" => [
    "name" => "CodefyPHP"
    "manager" => null
  ]
]
```

or

    <?php
    
    print_r(
        $helper->subset(
            array: $array,
            keys: ['project.name', 'project.manager', 'user', 'not_provided'],
            default: 'Not Provided'
        )
    );

**Result:**

```text
[
  "project" => [
    "name" => "CodefyPHP"
    "manager" => "Not Provided"
  ]
  "user" => [
    "fname" => "Joshua"
    "lname" => "Parker"
  ]
  "not_provided" => "Not Provided"
]
```

## sum()

The `sum()` method calculate the sum of values in an array plucked by the `$key`.

    <?php

    $array = [
        [
            'age' => 20,
            'name' => 'Bill',
            'scores' => [
                'math' => 10,
            ],
        ],
        [
            'age' => 25,
            'name' => 'Chris',
            'scores' => [
                'math' => 15,
            ],
        ],
        [
            'age' => 38,
            'name' => 'Bert',
            'scores' => [
                'math' => 5,
            ],
        ],
    ];

    echo $helper->sum(array: $array, key: 'age');
    // Return: 83

    echo $helper->sum(array: $array, key: 'scores.math');
    // Return: 30

## toAssoc()

The `toAssoc()` method turns a non-associative array into an associative array if it has an even number of segments.

    <?php

    use function print_r;

    $array = ['foo', 'bar', 'baz', 'yay'];

    print_r($helper->toAssoc(arr: $array));

**Result:**

```text
[
  "foo" => "bar"
  "baz" => "yay"
]
```

## unique()

The `unique()` method returns an array with all unique values in the source array. The first value matched will be kept, 
duplicates will be discarded. Keys will be preserved. This method works like 
[`array_unique()`](https://www.php.net/manual/en/function.array-unique.php), but doesn't sort the array first, 
and allows you to dedupe arrays that contain objects or closures.

    <?php

    use function print_r;

    $array = ['val1' => 'hello', 'val2' => 'hello', 'val3' => 'bye'];

    print_r($helper->unique(arr: $array));

**Result:**

```text
[
  "val1" => "hello"
  "val3" => "bye"
]
```








