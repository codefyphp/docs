---
title: NoSQL
sidebar_title: NoSQL
order: 41
---

## Installation

```shell
composer require qubus/nosql
```

## Introduction

`NoSQL` is a small, schemaless database library that stores collections in JSON files. It provides fluent 
filtering, sorting, projection, mapping, aggregation, relations, transactions, events, and macros without requiring 
a database server.

## Quick start

```php
<?php

require __DIR__ . '/vendor/autoload.php';

use Qubus\NoSql\Node;

// Opens storage/users.json. The storage directory must already exist.
$users = Node::open(__DIR__ . '/storage/users');

$user = $users->insert([
    'email'  => 'ada@example.com',
    'name'   => 'Ada',
    'active' => true,
    'score'  => 95,
]);

$activeUsers = $users
    ->where('active', true)
    ->sortBy('name')
    ->get();

$users->where('_id', $user['_id'])->update(['score' => 100]);
$users->where('_id', $user['_id'])->delete();
```

Each inserted record receives a ULID in its `_id` field. The JSON document is keyed by those IDs:

```json
{
    "01K7A51H9EE1PSAQ3TW8897XTG": {
        "_id": "01K7A51H9EE1PSAQ3TW8897XTG",
        "name": "Ada"
    }
}
```

## Opening collections

Use `Node` when you want the same `Collection` instance to be reused for the same resolved filename:

```php
use Qubus\NoSql\Node;

$users = Node::open(__DIR__ . '/storage/users');
```

Alternatively, construct a collection directly:

```php
use Qubus\NoSql\Collection;

$users = new Collection(__DIR__ . '/storage/users');
```

The filename extension and JSON encoding flags are configurable:

```php
$users = new Collection(__DIR__ . '/storage/users', [
    'file_extension' => '.data',
    'save_format'    => JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE,
]);
```

This example writes `storage/users.data`. The defaults are `.json` and `JSON_PRETTY_PRINT`. The library creates the file on its first write, but it does not create missing directories.

`Node::clear()` removes all cached collection instances. Global macros remain registered. When the same resolved filename is opened more than once, the first instance and its options are reused until the cache is cleared.

## Reading data

```php
$all = $users->all();                  // All records, numerically indexed.
$one = $users->find($id);              // One record or null.
$all = $users->query()->get();         // Fluent-query equivalent of all().
$one = $users->query()->first();       // First matching record or null.
$raw = $users->loadData();             // Associative array keyed by record ID.
```

`all()` and `get()` return record values without the document's storage keys. Use `find()` or `loadData()` when those keys matter.

## Filtering

`where()` accepts a field and value, a field/operator/value triplet, or a closure:

```php
use Qubus\NoSql\ArrayExtra;

$exact = $users->where('email', 'ada@example.com')->get();
$highScores = $users->where('score', '>=', 80)->get();

$custom = $users->where(
    fn (ArrayExtra $row): bool => $row['profile.country'] === 'US'
)->get();
```

The supported operators are:

| Operator             | Meaning                                              |
|----------------------|------------------------------------------------------|
| `=`                  | Strict equality; this is the default                 |
| `!=`, `<>`           | Strict inequality                                    |
| `>`, `>=`, `<`, `<=` | Comparison                                           |
| `in`                 | Value occurs in the supplied array                   |
| `not in`             | Value does not occur in the supplied array           |
| `between`            | Inclusive range using an array of exactly two values |
| `match`              | PHP PCRE pattern match                               |

```php
$users->where('role', 'in', ['admin', 'editor'])->get();
$users->where('score', 'between', [80, 100])->get();
$users->where('email', 'match', '/@example\.com$/i')->get();
```

Operator names are case-insensitive. `in` and `not in` use PHP's non-strict `in_array()` behavior; use a closure when strict membership is required.

Combine filters with `where()` and `orWhere()`:

```php
$users
    ->where('role', 'admin')
    ->orWhere('score', '>=', 90)
    ->where('active', true)
    ->get();
```

Filters are evaluated from left to right. The example is equivalent to `((role = admin OR score >= 90) AND active = true)`.

`filter()` is a readable closure-only alias:

```php
$users->filter(fn (ArrayExtra $row): bool => $row['score'] % 2 === 0)->get();
```

Fields support dot notation through `ArrayExtra`, including nested fields such as `profile.country`.

## Selecting columns

Pass selected fields to `get()` or `first()`:

```php
$rows = $users->query()->get(['email', 'name']);
$user = $users->where('active', true)->first(['email', 'profile.country']);
```

Use `field:alias` to rename a selected value:

```php
$rows = $users->query()->get([
    'email',
    'profile.country:country',
]);
```

The same behavior is available as a chainable `select()` call.

## Sorting and pagination

Sort by a field in ascending or descending order:

```php
$ascending = $users->sortBy('score')->get();
$descending = $users->sortBy('score', 'desc')->get();
```

Use a closure to calculate the sort value:

```php
$rows = $users->sort(
    fn (ArrayExtra $row): string => strtolower($row['name']),
    'asc'
)->get();
```

Skip and limit records with `skip()` and `take()`:

```php
$page = $users->sortBy('name')->take(limit: 20, offset: 40)->get();
$afterFirstTen = $users->skip(10)->get();
```

`take(0)` returns no records. Apply sorting before pagination when deterministic pages are required.

## Inserting records

Insert one record:

```php
$record = $users->insert([
    'email' => 'grace@example.com',
    'name'  => 'Grace',
]);

$id = $users->lastInsertId();
```

`insert()` returns the inserted record on success. `lastInsertId()` returns its normalized ULID, or `null` when no insert has succeeded.

Insert several records in one transaction:

```php
$users->inserts([
    ['name' => 'Ada'],
    ['name' => 'Grace'],
    ['name' => 'Linus'],
]);
```

You may provide `_id` yourself, but it must be a valid ULID. Omitting it is recommended. A supplied ID that already exists replaces that record, so enforce uniqueness before accepting application-provided IDs.

## Updating and deleting

Update every matching record:

```php
$affected = $users
    ->where('active', false)
    ->update(['status' => 'archived']);
```

Delete every matching record:

```php
$affected = $users
    ->where('status', 'archived')
    ->delete();
```

Calling `$users->update(...)` or `$users->delete()` without a filter affects every record. Use `truncate()` when the intention is explicitly to empty the collection:

```php
$users->truncate();
```

`insert()` returns the stored record or `null`. `update()` and `delete()` return the matched row count, or `true` when nothing matched. `save()` returns its processed row count. Direct persistence and transaction methods return the number of bytes written, or `true` while staging data or when no commit is needed.

## Mapping and saving transformations

`map()` transforms query results. Return an array or `ArrayExtra` from the mapper:

```php
$summaries = $users
    ->where('active', true)
    ->map(fn (ArrayExtra $row): array => [
        'name'  => $row['name'],
        'score' => $row['score'],
    ])
    ->get();
```

`get()` leaves the file unchanged. Call `save()` to persist mapped rows:

```php
$users
    ->where('active', true)
    ->map(function (ArrayExtra $row): ArrayExtra {
        $row['profile.reviewed'] = true;
        return $row;
    })
    ->save();
```

Only rows selected by the preceding pipeline are replaced. If a mapper changes `_id`, `save()` moves the record to the new storage key automatically.

## Aggregates and lists

Aggregate methods are available on collections and queries:

```php
$count = $users->where('active', true)->count();
$total = $users->sum('score');
$average = $users->avg('score');
$lowest = $users->min('score');
$highest = $users->max('score');
```

For an empty result, `count()`, `sum()`, and `avg()` return `0`; `min()` and `max()` return `null`.

Build a list of values, optionally keyed by another field:

```php
$scores = $users->lists('score');
$scoresByEmail = $users->lists('score', 'email');

// pluck() is a Query alias of lists().
$namesById = $users->query()->pluck('name', '_id');
```

## Relations

Relations perform a lookup for each parent row and add the result under the chosen field.

```php
$users = Node::open(__DIR__ . '/storage/users');
$posts = Node::open(__DIR__ . '/storage/posts');

// Attach the author whose _id matches each post's user_id.
$postsWithAuthors = $posts
    ->withOne($users, 'author', '_id', '=', 'user_id')
    ->get();

// Attach every post whose user_id matches each user's _id.
$usersWithPosts = $users
    ->withMany($posts, 'posts', 'user_id')
    ->get();
```

The complete signature is:

```php
withOne(Collection|Query $relation, string $as, string $otherKey, string $operator = '=', string $thisKey = '_id')
withMany(Collection|Query $relation, string $as, string $otherKey, string $operator = '=', string $thisKey = '_id')
```

Pass a prefiltered `Query` when the related rows need additional constraints:

```php
$publishedPosts = $posts->where('published', true);
$users->withMany($publishedPosts, 'posts', 'user_id')->get();
```

The relation query is cloned for each lookup and is not modified by the relation.

## Transactions

Use `transaction()` to stage writes in memory and commit them together:

```php
$result = $users->transaction(function (Collection $users): string {
    $users->insert(['name' => 'Ada']);
    $users->insert(['name' => 'Grace']);

    return 'created';
});
```

The callback's return value is returned. If any `Throwable` escapes the callback or commit, staged data is rolled back and the original throwable is rethrown.

Manual transaction control is also available:

```php
$users->begin();

try {
    $users->update(['reviewed' => true]);
    $users->commit();
} catch (Throwable $exception) {
    $users->rollback();
    throw $exception;
}
```

Useful state methods are `isModeTransaction()`, `begin()`, `commit()`, and `rollback()`. Nested calls to `transaction()` join the active transaction. `inserts()` also respects an already active outer transaction.

Transactions are process-local. See [Operational and security notes](#operational-and-security-notes) for concurrent-writer guidance.

## Events

Register collection callbacks with `on()` and one of these constants:

| Event                   | Callback arguments             | Timing                                   |
|-------------------------|--------------------------------|------------------------------------------|
| `Collection::INSERTING` | `ArrayExtra $record`           | Before an insert is persisted            |
| `Collection::INSERTED`  | `array $record`                | After an insert succeeds                 |
| `Collection::UPDATING`  | `Query $query, array $changes` | Before an update                         |
| `Collection::UPDATED`   | `array $records`               | After an update succeeds                 |
| `Collection::DELETING`  | `Query $query`                 | Before a delete                          |
| `Collection::DELETED`   | `array $records`               | After a delete succeeds                  |
| `Collection::CHANGED`   | `array $database`              | After insert, update, or delete succeeds |

```php
use Qubus\NoSql\ArrayExtra;
use Qubus\NoSql\Collection;

$users->on(Collection::INSERTING, function (ArrayExtra $record): void {
    $record['created_at'] = date(DATE_ATOM);
});

$users->on(Collection::CHANGED, function (array $database): void {
    // Invalidate a cache, write an audit entry, and so on.
});
```

The `INSERTING` record is mutable. If it changes `_id`, the new value must be a valid ULID. Inside a transaction, events run when each operation is staged rather than after the final disk commit.

## Macros

Macros add reusable query methods. A collection macro receives its current `Query` as the first argument:

```php
use Qubus\NoSql\Query;

$users->macro('active', function (Query $query): Query {
    return $query->where('active', true);
});

$activeAdmins = $users->active()->where('role', 'admin')->get();
```

Macros work from both the collection and an existing query chain:

```php
$users->active()->get();
$users->where('role', 'admin')->active()->get();
```

Register a macro for collections opened through `Node` by calling `Node::macro()` before `Node::open()`:

```php
Node::macro('active', fn (Query $query): Query => $query->where('active', true));

$users = Node::open(__DIR__ . '/storage/users');
$users->active()->get();
```

Use `hasMacro()` and `getMacro()` to inspect collection macros. Calling an unknown method or macro throws `UndefinedMethodException`.

## Persistence resolver

A resolver transforms every record immediately before a full document is written:

```php
$users->setResolver(function (array $record): array {
    unset($record['temporary']);
    return $record;
});
```

The resolver applies to `persists()` and all normal writes that pass through it. It should return an array and preserve `_id` unless it also deliberately maintains storage-key consistency. Retrieve the callback with `getResolver()`.

Advanced callers can replace the complete keyed document with `persists()`:

```php
$users->persists([
    $id => ['_id' => $id, 'name' => 'Ada'],
]);
```

## ArrayExtra and dot notation

Query closures receive an `ArrayExtra`, an `ArrayAccess` wrapper with dot-notation support:

```php
use Qubus\NoSql\ArrayExtra;

$row = new ArrayExtra([
    'profile' => ['name' => 'Ada'],
]);

$name = $row['profile.name'];
$row['profile.active'] = true;
unset($row['profile.name']);
$array = $row->toArray();
```

Its static helpers work on ordinary arrays:

```php
$data = ['profile' => ['name' => 'Ada']];

ArrayExtra::arrayHas($data, 'profile.name');       // true
ArrayExtra::arrayGet($data, 'profile.name');       // Ada
ArrayExtra::arraySet($data, 'profile.active', true);
ArrayExtra::arrayRemove($data, 'profile.name');
```

`arraySet()` supports `*` to update each member at a level:

```php
$data = ['items' => [['active' => false], ['active' => false]]];
ArrayExtra::arraySet($data, 'items.*.active', true);
```

`merge()` merges an array into the wrapper and interprets its keys using dot notation.

## Error handling

The library throws exceptions rather than terminating the PHP process. Common exceptions include:

| Exception                                                  | Cause                                                             |
|------------------------------------------------------------|-------------------------------------------------------------------|
| `Qubus\NoSql\Exceptions\InvalidJsonException`              | Invalid JSON, non-collection JSON, or data that cannot be encoded |
| `Qubus\Exception\Data\TypeException`                       | Invalid query operator, sort direction, query type, or range      |
| `Qubus\Exception\IO\FileSystem\DirectoryNotFoundException` | The collection directory does not exist                           |
| `Qubus\Exception\IO\FileSystem\FileNotReadableException`   | The JSON file cannot be read                                      |
| `Qubus\Exception\IO\FileSystem\FileNotWritableException`   | The JSON file cannot be written                                   |
| `Qubus\NoSql\Exceptions\UndefinedMethodException`          | An unknown method or macro was called                             |

```php
use Qubus\NoSql\Exceptions\InvalidJsonException;

try {
    $users->where('active', true)->get();
} catch (InvalidJsonException $exception) {
    // Report or recover from a damaged collection file.
}
```

Encoding completes before the destination file is opened for writing, so unencodable data does not overwrite the existing JSON document.

## Method reference

### Collection

| Area            | Methods                                                                                             |
|-----------------|-----------------------------------------------------------------------------------------------------|
| Construction    | `__construct()`, `Node::open()`, `Node::clear()`                                                    |
| Reading         | `all()`, `find()`, `loadData()`, `query()`                                                          |
| Query shortcuts | `where()`, `filter()`, `map()`, `sortBy()`, `sort()`, `skip()`, `take()`, `withOne()`, `withMany()` |
| Aggregates      | `count()`, `sum()`, `avg()`, `min()`, `max()`, `lists()`                                            |
| Writes          | `insert()`, `inserts()`, `update()`, `delete()`, `truncate()`, `persists()`                         |
| Transactions    | `transaction()`, `begin()`, `commit()`, `rollback()`, `isModeTransaction()`                         |
| Extension hooks | `on()`, `macro()`, `hasMacro()`, `getMacro()`, `setResolver()`, `getResolver()`                     |
| IDs             | `generateKey()`, `lastInsertId()`, `getKeyId()`, `getKeyOldId()`                                    |

`Collection::execute()` is the low-level dispatcher used by `Query`. It validates that the query belongs to that collection and accepts the `Query::TYPE_*` constants.

### Query

| Area       | Methods                                                             |
|------------|---------------------------------------------------------------------|
| Filters    | `where()`, `orWhere()`, `filter()`                                  |
| Transforms | `select()`, `map()`, `sortBy()`, `sort()`, `skip()`, `take()`       |
| Relations  | `withOne()`, `withMany()`                                           |
| Reads      | `get()`, `first()`                                                  |
| Aggregates | `count()`, `sum()`, `avg()`, `min()`, `max()`, `lists()`, `pluck()` |
| Writes     | `update()`, `delete()`, `save()`                                    |
| Advanced   | `getCollection()`, `setCollection()`, `getPipes()`                  |

Query objects are mutable builders. Clone a query when you need an independent copy.

### Pipeline extension

Queries internally compose classes implementing `Qubus\NoSql\Pipes\Pipe`:

```php
interface Pipe
{
    public function process(array $data): array;
}
```

The supplied implementations are `FilterPipe`, `MapperPipe`, `SorterPipe`, and `LimiterPipe`. `Query::addPipe()` is protected; a custom query subclass can expose domain-specific pipelines while retaining the standard execution model.

## Operational and security notes

- Treat collection paths, custom regex patterns, callbacks, and mapped data as trusted application input.
- Enforce uniqueness before supplying or changing `_id`; moving a record onto an existing ID replaces the existing record.
- Writes use an exclusive lock while the JSON file is written. A complete read-modify-write query is not locked across multiple PHP processes, so applications with concurrent writers should serialize mutations externally.
- Transactions stage data only inside the current `Collection` instance; they are not cross-process transactions.
- Keep backups for important data and avoid using this flat-file store for workloads that require high write concurrency.
- The `_old` field is reserved internally while a mapped record ID is being changed. Do not use it as application data.
