CodefyPHP comes with two database instances. One is an [ORM Query Builder](https://github.com/QubusPHP/expressive/blob/master/OrmBuilder.php) 
and the other is a [Dbal Query Builder](https://github.com/QubusPHP/dbal). The ORM query builder isn’t a true ORM. 
What makes this one different is that you can call your database tables as methods:

    use Qubus\Exception\Exception;
    
    use function Codefy\Framework\Helpers\orm;
    
    try {
        $orm = orm();
    } catch (Exception $e) {
        return $e->getMessage();
    }
    
    $posts = $orm->table('posts')->find();
    // similar to above
    $posts = $orm->posts()->find();

Alternatively, you can use the Dbal query builder:

    use Qubus\Exception\Exception;
    
    use function Codefy\Framework\Helpers\dbal
    
    try {
        $dbal = dbal();
    } catch (Exception $e) {
        return $e->getMessage();
    }
    
    $posts = $dbal->select()->from('posts)->execute();

Another difference between the two is that the ORM Query Builder will work with code completion via an IDE.

The documentation for the **Dbal Query Builder** can be found at the [Qubus Components Docs](https://docs.qubusphp.com/dbal/). 
Below is the documentation for the **ORM query builder**.

Insert
------

When calling the insert(array $data) method, $data can be passed as one dimensional array to insert one new record or 
multiple arrays to insert multiple records.

### Single Entry

    $post = $posts->insert([
        "title" => "CodefyPHP Framework",
        "content" => "The CodefyPHP framework is for domain driven development.",
        "authorID" => 1,
        "timestamp" => $orm->now()
    ]);

### Multiple Entries

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

Update
------

There are two ways to update a record, by using the active record pattern or by or by using the where clause.

    $post->update([
        "title" => "PHP 8.3"
    ]);

The above can also be written as:

    $post->title = "PHP 8.3";
    $post->update();

You can use the alternative `save()` instead of `update()`.

Or you can use the `set(array $data)` or `set($key, $value)`:

    $post->set('title','PHP 8.3')->update();

For multiple entries using `set(array $data)` and `where($key, $value)`:

    $post->set([
        "content" => "PHP 8.3 is the greatest because..."
    ])
        ->where("title", "PHP 8.3")
        ->update();

Save
----

`save()` is a shortcut to `insert()` or `update()`.

### Insert

    $post = $orm->posts();
    $post->title = "PHP 8.3";
    $post->content = "PHP 8.3 is the greatest because...";
    $post->save();

### Update

    $post = $posts->findOne(3847);
    $post->title = "PHP 8.3 Update";
    $post->save();

Delete
------

### Single Entry

    $post = $posts->reset()->findOne(3847);
    $post->delete();

### Multiple Entries

    $posts->where("title", "PHP 8.3")->delete();

Count
-----

Count all the entries based on `where()` filter:

    $allPosts = $posts->count();
     
    $count = $posts->where($x, $y)->count();

Use count for a specific column name:

    $count = $posts->where($x, $y)->count('columnName');

Max
---

Max based on `where()` filter:

    $max = $posts->where($x, $y)->max('columnName');

Min
---

Min based on where() filter:

    $min = $posts->where($x, $y)->min('columnName');

Sum
---

Sum based on `where()` filter:

    $sum = $posts->where($x, $y)->sum('columnName');

Avg
---

Avg based on `where()` filter:

    $avg = $posts->where($x, $y)->avg('columnName');

Aggregate
---------

    $agg = $posts->where($x, $y)->aggregate('GROUP_CONCAT columnName');

Querying
--------

The fluent query feature of the ORM query builder allows you to write simple queries without having to write SQL.

### FindOne

Returns a single record is found otherwise it will return false.

    $post = $posts->where(condition: 'postID', parameters: 364)
        ->findOne();

You can achieve the same above by using only the primary key and dropping the where filter.

    $post = $posts->findOne(364);

Retrieving the entry:

    if ($post) {
        echo " $post->title";
    
        // On a retrieved entry you can perform update and delete
        $post->last_viewed = $posts->now();
        $post->save();
    }

### Find

Find returns and ArrayIterator of rows found, otherwise it will return false.

    $allPosts = $posts->where(condition: 'title', parameters: 'PHP 8.3')
        ->find();
    
    foreach ($allPosts as $post) {
        echo "{$post->content}";
    
        // On a retrieved entry you can perform update and delete
        $post->last_viewed = $posts->now();
        $post->save();
    }

Find also accepts a closure ( find(Closure $callback) ) to perform data manipulation.

    $posts->where(condition: 'title', parameters: 'PHP 8.3');
    
    $results = $posts->find(function ($data) {
        $newResults = array();
    
        foreach ($data as $d) {
            $d["new_title"] = "{$data["title"]}";
            $newResults[] = $d;
        }
    
        return $newResults;
    });

Fluent Query Builder
--------------------

### Select All

    $posts->select()

### Select Columns

    $posts->select(columns: "title, content")
        ->select(columns: "last_viewed");

Where
-----

Where can be used to setup the where clauses and they work with `find()`, `findOne()`, `update()`, and `delete()`. 
This is the same for the where aliases as well. Repetitive call to where and it’s aliases will append to each other 
using the AND operator. Use `or__()` to mimic the OR operator.

### Examples:

    $posts->where(condition: "title", parameters: "PHP 8.3");
    
    $posts->where(condition: "authorID > ?", parameters: 25);
    
    $posts->where(condition: "name in (?, ?, ?)", parameters: "PHP 8.3", "HTML 5", "ROR");
    
    $posts->where(condition: "(field1, field2)", parameters: [[1, 2], [3, 4]]);

### Primary Key:

    $posts->wherePK(456);

### Not Equal To:

    $posts->whereNot('postID', 24);

### Like:

    $posts->whereLike('title', 'PH%');

### Not Like:

    $posts->whereNotLike('title', 'PH%');

### Greater Than:

    $posts->whereGt('timestamp', 2014-09-14);

### Greater Than Equal To:

    $posts->whereGte('timestamp', 2014-09-14);

### Less Than:

    $posts->whereLt('timestamp', 2014-09-14);

### Less Than Equal To:

    $posts->whereLte('timestamp', 2014-09-14);

### Where In:

    $posts->whereIn('authorID', ['2', '24']);

### Where Not In:

    $posts->whereNotIn('authorID', ['2', '24']);

### Where Null:

    $posts->whereNull('content');

### Where Not Null:

    $posts->whereNotNull('timestamp');

Where with OR and AND
---------------------

Use `and__()` / `or__()` chained to any where clauses:

    $posts->where(condition: "authorID", parameters: 24)
        ->and__()->whereGte(columnName: "timestamp", value: '2014-09-14');
    
    $posts->where(condition: "authorID", parameters: 24)
        ->or__()->whereGte(columnName: "authorID", value: 24)
        ->or__()->where(condition: "category", parameters: "Programming");

Order, Group, Limit, Offset
---------------------------

    $posts->orderBy(columnName: 'postID', ordering: 'DESC');
    
    $posts->groupBy(columnName: 'category');
    
    $posts->limit(limit: 10);
    
    $posts->offset(offset: 10);

Joins
-----

    /**
     * Defaults to LEFT JOIN, for others, use INNER, RIGHT, etc. as the
     * $joinOperator
     *
     * join( $tablename, $constraint, $table_alias , $joinOperator )
     */
    
    $posts->join(tableName: 'category', constraint: 'c.catID = posts.catID', tableAlias: 'c');