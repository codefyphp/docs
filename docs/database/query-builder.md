---
title: QueryBuilder
sidebar_title: QueryBuilder
weight: 2
---

An alternative to DBAL, you can use the Dbal query builder. The query builder is ORM like, but not a true full featured ORM.
It's ORM like because you can call your database tables as methods:

    <?php

    use Qubus\Exception\Exception;
    use Codefy\Framework\Proxy\Codefy;
    
    try {
        $queryBuilder = Codefy::$PHP->getDb();
    } catch (Exception $e) {
        return $e->getMessage();
    }

    $posts = $queryBuilder->table('posts');
    // similar to above (ORM like)
    $posts = $queryBuilder->posts();

### Transactions

You may use the `transactional()` method provided to run a set of operations within a database transaction. 
If an exception is thrown within the transaction closure, the transaction will automatically be rolled back. If the 
closure executes successfully, the transaction will automatically be committed.

    <?php
    
    $this->db->transactional(callback: function () {
        $this->db
            ->table(tableName: 'user')
            ->set([
                // data to save
            ])
            ->save();
    });

### Insert

When calling the `insert(array $data)` method, `$data` can be passed as one dimensional array to insert one new record or
multiple arrays to insert multiple records.

#### Single Entry

    <?php

    $post = $posts->insert([
        "title" => "CodefyPHP Framework",
        "content" => "The CodefyPHP framework is for domain driven development.",
        "authorID" => 1,
        "timestamp" => $orm->now()
    ]);

#### Multiple Entries

    <?php

    $massPosts = $posts->insert([
        [
            "title" => "Domain Driven Frameworks",
            "content" => "Domain Driven frameworks started...",
            "authorID" => 1,
            "timestamp" => $orm->now()
        ],
        [
            "title" => "PHP 8.2",
            "content" => "The new features in 8.2 are...",
            "authorID" => 1,
            "timestamp" => $orm->now()
        ],
        [
            "title" => "Event Sourcing",
            "content" => "Event sourcing is great for...",
            "authorID" => 1,
            "timestamp" => $orm->now()
        ],
    ]);

### Update

There are two ways to update a record, by using the active record pattern or by using the where clause.

    <?php

    $post->update([
        "title" => "PHP 8.4"
    ]);

The above can also be written as:

    <?php

    $post->title = "PHP 8.4";
    $post->update();

You can use the alternative `save()` instead of `update()`.

Or you can use the `set(array $data)` or `set($key, $value)`:

    <?php

    $post->set('title','PHP 8.4')->update();

For multiple entries using `set(array $data)` and `where($key, $value)`:

    <?php

    $post->set([
        "content" => "PHP 8.4 is the greatest because..."
    ])
        ->where("title", "PHP 8.4")
        ->update();

### Save

`save()` is a shortcut to `insert()` or `update()`.

#### Insert

    <?php

    $post = $orm->posts();
    $post->title = "PHP 8.4";
    $post->content = "PHP 8.4 is the greatest because...";
    $post->save();

#### Update

    <?php

    $post = $posts->findOne(3847);
    $post->title = "PHP 8.4 Update";
    $post->save();

### Delete

#### Single Entry

    <?php

    $post = $posts->reset()->findOne(3847);
    $post->delete();

#### Multiple Entries

    <?php

    $posts->where("title", "PHP 8.4")->delete();

## Count

Count all the entries based on `where()` filter:

    <?php

    $allPosts = $posts->count();
     
    $count = $posts->where($x, $y)->count();

Use count for a specific column name:

    <?php

    $count = $posts->where($x, $y)->count('columnName');

## Max

Max based on `where()` filter:

    <?php

    $max = $posts->where($x, $y)->max('columnName');

## Min

Min based on where() filter:

    <?php

    $min = $posts->where($x, $y)->min('columnName');

## Sum

Sum based on `where()` filter:

    <?php

    $sum = $posts->where($x, $y)->sum('columnName');

## Avg

Avg based on `where()` filter:

    <?php

    $avg = $posts->where($x, $y)->avg('columnName');

### Aggregate

    <?php

    $agg = $posts->where($x, $y)->aggregate('GROUP_CONCAT columnName');

## Querying

The fluent query feature of the ORM query builder allows you to write simple queries without having to write SQL.

### FindOne

Returns a single record is found otherwise it will return false.

    <?php

    $post = $posts->where(condition: 'postID', parameters: 364)
        ->findOne();

You can achieve the same above by using only the primary key and dropping the where filter.

    <?php

    $post = $posts->findOne(364);

Retrieving the entry:

    <?php

    if ($post) {
        echo " $post->title";
    
        // On a retrieved entry you can perform update and delete
        $post->last_viewed = $posts->now();
        $post->save();
    }

### Find

Find returns and ArrayIterator of rows found, otherwise it will return false.

    <?php

    $allPosts = $posts->where(condition: 'title', parameters: 'PHP 8.4')
        ->find();
    
    foreach ($allPosts as $post) {
        echo "{$post->content}";
    
        // On a retrieved entry you can perform update and delete
        $post->last_viewed = $posts->now();
        $post->save();
    }

Find also accepts a closure ( find(Closure $callback) ) to perform data manipulation.

    <?php

    $posts->where(condition: 'title', parameters: 'PHP 8.4');
    
    $results = $posts->find(function ($data) {
        $newResults = array();
    
        foreach ($data as $d) {
            $d["new_title"] = "{$data["title"]}";
            $newResults[] = $d;
        }
    
        return $newResults;
    });

## Fluent Query Builder

### Select All

    <?php

    $posts->select()

### Select Columns

    <?php

    $posts->select(columns: "title, content")
        ->select(columns: "last_viewed");

## Where

Where can be used to setup the where clauses and they work with `find()`, `findOne()`, `update()`, and `delete()`.
This is the same for the where aliases as well. Repetitive call to where and it’s aliases will append to each other
using the AND operator. Use `or()` to mimic the OR operator.

### Examples:

```php
<?php

$posts->where(condition: "title", parameters: "PHP 8.4");

$posts->where(condition: "authorID > ?", parameters: 25);

$posts->where(
    condition: "name in (?, ?, ?)",
    parameters: "PHP 8.4", "HTML 5", "ROR"
);

$posts->where(condition: "(field1, field2)", parameters: [[1, 2], [3, 4]]);
```

### Primary Key:

    <?php

    $posts->wherePK(456);

### Not Equal To:

    <?php

    $posts->whereNot('postID', 24);

### Like:

    <?php

    $posts->whereLike('title', 'PH%');

### Not Like:

    <?php

    $posts->whereNotLike('title', 'PH%');

### Greater Than:

    <?php

    $posts->whereGt('timestamp', 2014-09-14);

### Greater Than Equal To:

    <?php

    $posts->whereGte('timestamp', 2014-09-14);

### Less Than:

    <?php

    $posts->whereLt('timestamp', 2014-09-14);

### Less Than Equal To:

    <?php

    $posts->whereLte('timestamp', 2014-09-14);

### Where In:

    <?php

    $posts->whereIn('authorID', ['2', '24']);

### Where Not In:

    <?php

    $posts->whereNotIn('authorID', ['2', '24']);

### Where Null:

    <?php

    $posts->whereNull('content');

### Where Not Null:

    <?php

    $posts->whereNotNull('timestamp');

## Where with OR and AND

Use `and()` / `or()` chained to any where clauses:

    <?php

    $posts->where(condition: "authorID", parameters: 24)
        ->and()->whereGte(columnName: "timestamp", value: '2014-09-14');
    
    $posts->where(condition: "authorID", parameters: 24)
        ->or()->whereGte(columnName: "authorID", value: 24)
        ->or()->where(condition: "category", parameters: "Programming");

## Order, Group, Limit, Offset

    <?php

    $posts->orderBy(columnName: 'postID', ordering: 'DESC');
    
    $posts->groupBy(columnName: 'category');
    
    $posts->limit(limit: 10);
    
    $posts->offset(offset: 10);

## Joins

```php
<?php

/**
 * Defaults to LEFT JOIN, for others, use INNER, RIGHT, etc. as the
 * $joinOperator
 *
 * join( $tablename, $constraint, $table_alias , $joinOperator )
 */

$posts->join(
    tableName: 'category',
    constraint: 'c.catID = posts.catID',
    tableAlias: 'c'
);
```

