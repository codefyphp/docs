---
title: Active Record
sidebar_title: Active Record
keywords: orm,active-record,data-mapper
weight: 0
---

## Installation

```shell
composer require qubus/expressive
```

## Introduction

CodefyPHP is designed to provide a comprehensive set of tools for developing domain-driven applications without 
the use of an ORM. Nonetheless, the framework is flexible and can be utilized independently of 
Domain-Driven Design (DDD), Command Query Responsibility Segregation (CQRS), or Event Sourcing principles. 
While CodefyPHP does not use the ORM natively, documentation is provided for developers who wish to implement their 
own architectural patterns and persistence layers outside or in conjunction with DDD principles and CodefyPHP's 
philosophy.

## Defining Models

Models in Active Record represent a single table to work with. To define a model, you need to extend the Model class.

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';
    }

The `$tablName` property is used to tell which table the model will work with. There are also several other properties 
to customize the model configuration.

### Model Properties

* `$tableName`: to define the table name. This property is required.
* `$tablePrefix`: to define a prefix for table names. This property is optional.
* `$primaryKey`: to define the column name of the table's primary key. Default is `id`. If your PK has other name than `id` you should change this.
* `$incrementing`: to define whether your PK is auto-increment. Default value is true. If you'd like to generate your Primary Key value by custom function, set this to `false`.

## Querying

### Retrieve All Models

    <?php
    
    $posts = Post::all();
    foreach($posts as $post) {
        echo $post->title;
    }

### Find A Model By Primary Key

    <?php
    
    $post = Post::find('01K74SR0BRE4093D40SR087PPR');
    echo $post->title;

You can also pass multiple IDs or an array to get multiple records.

    <?php
    
    $posts = Post::find('01K74SR0BRE4093D40SR087PPR', '01K7A51H9EE1PSAQ3TW8897XTG', '01K7A51JXJEFBBT89K10CA13H1');
    // or
    $posts = Post::find( ['01K74SR0BRE4093D40SR087PPR', '01K7A51H9EE1PSAQ3TW8897XTG', '01K7A51JXJEFBBT89K10CA13H1'] );

### Custom Query

You can still use Active Record to generate a custom query.

    <?php
    
    $posts = Post::where('status', 'published')->get();
    foreach($posts as $post) {
        echo $post->title;
    }

Or if you only want to retrieve the first record, you can use `first()` method.

    <?php
    
    $post = post::where('status', 'published')->first();
    echo $post->title;

### 'Pluck'-ing

Plucking is the way to retrieve a single column value of the first record.

    <?php
    
    // Returns the `title` column of the first row
    echo 'Newest post is: ' . Post::orderBy('id', 'desc')->pluck('title');

### Selecting Specific Columns
By default, Active Record will generate a `SELECT *` query for all examples above. If you think this is a bad practice, 
you can select only specific columns you need in several ways:

    <?php
    
    Post::all( ['id', 'title'] );
    Post::where('status', 1)->get( ['id', 'title'] );
    Post::select( ['id', 'title'] )->get();
    Post::where('status', 1)->first( ['id', 'title'] );

!!! note
    For now, the `find()` method doesn't support selecting specific column.

## Aggregates Methods

Active Record also provides aggregates method, such as `max`, `min`, `avg`, `sum`, and `count`. You can call these 
methods right away or chain them.

    <?php
    
    $total = Product::count();
    
    $max = Product::max('price');
    
    // Example of chaining with where()
    $min = Product::where('category', '01K7ABSCGNE83V89CGKB4SPWXK')->min('price');
    
    $avg = Product::avg('price');
    
    // Another chaining example
    $sum = Order::where('status', 1)->sum('price');

## Create, Update & Delete

### Creating A New Model

    <?php
    
    $post =  new Post();
    
    $post->title = 'A New Title';
    $post->content = 'More content to come...';
    
    $post->save();

After saving the record, if your model uses an auto incrementing primary key, the generated insert id will be set to 
the object. So if you use example above, you can show the new post's ID.

    <?php
    
    echo "New Post ID: " . $post->id;

!!! note
    Note that the property name isn't always `id`. It depends on the `primaryKey` property you've set.

Alternatively, you can use `create()` method to create new models.

    <?php
    
    $post = Post::create( ['title' => 'A New Title', 'content' => 'More content to come...'] );
    
    // create() method will return a newly created model or false if inserting fails
    echo $post->id;

### Updating Models

#### Updating Retrieved Models

    <?php
    
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    
    $post-title = 'A Different Title';
    $post->save();

#### Mass Updating

    <?php
    
    Post::where('status', 'published')->update( ['title' => 'A Different Title'] );

Or alternatively you can call `update()` method right away.

    <?php
    
    Post::update( ['title' => 'A Different Title'], ['id' => '01K7A51JXJEFBBT89K10CA13H1'] );

### Deleting Models

There are several ways to delete a model:

    <?php
    
    // Delete retrieved model
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    $post->delete();
    
    // Delete a single model by its primary key
    Post::delete('01K7A51JXJEFBBT89K10CA13H1');
    
    // Delete multiple models by their primary keys
    Post::delete('01K74SR0BRE4093D40SR087PPR', '01K7A51H9EE1PSAQ3TW8897XTG', '01K7A51JXJEFBBT89K10CA13H1');
    //or
    Post::delete( ['01K74SR0BRE4093D40SR087PPR', '01K7A51H9EE1PSAQ3TW8897XTG', '01K7A51JXJEFBBT89K10CA13H1'] );
    
    // Use Active Record
    Post::where('status', 'published')->delete();

## Query Scopes

Scopes is a custom function you can create in your models to generate custom queries

### Defining A Scope

Some conventions:

* Scope method name must be in camel case.
* Scope method name must start with `scope`.
* At least one parameter is required. This first parameter is a `QueryBuilder` which you can use to call Active Record methods.

```php
<?php

use Qubus\Expressive\ActiveRecord\Model;

class Post extends Model
{
    protected string $primaryKey = 'id';

    protected ?string $tablePrefix = '';

    protected ?string $tableName = 'post';
    
    public function scopeActive($query)
    {
        return $query->where('status', 1)->orderBy('title');
    }
}
```

### Utilizing Scopes

Using example above:

    <?php
    
    $activePosts = Post::active()->get();

!!! note
    When using a scope, the method name isn't using the `scope` prefix.

### Dynamic Scopes

Scopes can also accept parameters to be used in generating queries.

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';
        
        // Search an active post by title
        public function scopeSearch($query, $keyword)
        {
            return $query->where('status', 1)->and()->whereLike('title', "%$keyword%");
        }
    }

    // Using the scope
    $searchResults = Post::search('Why Use CodefyPHP for Your Next Project')->get();

## Relationship

### One to One

#### Defining One to One Relationship

This example shows how to define a one-to-one relationship between a `Post` model with `Tag`. In this case, a `Post` might have one `Tag`.

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Tag;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';

        public function tag()
        {
            return $this->hasOne(Tag::class);
        }
    }

The parameter injected into the `hasOne()` method is the name of the related model. Once the relationship is set,
you can retrieve it:

    <?php
    
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    $tag = $post->tag;
    // You can work with $tag object like the usual way
    
    // Returns its property
    echo $tag->name;
    
    // Or updates it
    $tag->name = "coding";
    $tag->save();

!!! note
    The name of the method where you call `hasOne()` doesn't have to be the same name of the related model. You can name it 
    anything you want, just make sure it doesn't conflict with an existing table's field name.

In the example above, the foreign key in the tag table is assumed to be `post_id` 
(lowercased related model's name with `_id` suffix). You can define a custom key name as the second parameter if your 
foreign key doesn't match this naming convention.

    <?php
    
    $this->hasOne(Tag::class, 'custom_field_name');

#### Defining the Inverse Relationship

You can also define the inverse of the relationship. For our example, after you get a `Tag` object, you may want to 
know what Post it belongs to. In the `Tag` model you have to call the `belongsTo()` method.

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Post;
    
    class Tag extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'tag';

        public function postAggregate()
        {
            return $this->belongsTo(Post::class);
        }
    }

    // Using the relationship
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    
    echo $post->postAggregate->title;

You can also define a custom foreign key as second parameter to `belongsTo()` method.

### One to Many

#### Defining One to Many Relationship

An example of one-to-many relationship is a `Post` can have one or many comments. To define such relationship, 
you can do this:

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Comment;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';

        public function comments()
        {
            return $this->hasMany(Comment::class);
        }
    }

The difference between `hasOne()` and `hasMany()` is that `hasMany()` will return an array of matched models, 
while `hasOne()` will return only one model.

    <?php
    
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    
    foreach($post->comments() as $comment)
    {
      echo $comment->text;
    }

#### Defining the Inverse Relationship

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Post;
    
    class Comment extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'comment';

        public function post()
        {
            return $this->belongsTo(Post::class);
        }
    }

    // Using the relationship
    $comment = Comment::find('01K7A81ZRBEAV91ACBN8K0N4W0');
    
    return $comment->post->title;

Again, you can set a custom foreign key to `belongsTo()` method as stated in the One to One section.

### Many to Many

#### Defining Many to Many Relationship

Many to many relationships are the most complex relationship. It requires a pivot table to bridge the relation between 
two models.

An example of this relationship is between a `Post` model with a `Tag` model. A post might have one or more tags while 
a tag can also be in one on more Posts.

To define the relationship:

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Tag;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';

        public function tags()
        {
            return $this->belongsToMany(Tag::class);
        }
    }

To retrieve the tags:

    <?php
    
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    
    foreach($post->tags as $tag)
    {
      echo $tag->name;
    }

Or you can do vice-versa in `Tag` model:

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Post;
    
    class Tag extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'tag';

        public function posts()
        {
            return $this->belongsToMany(Post::class);
        }
    }

    // Using the relationship
    $tag = Tag::find('01K7A8KR2JE5HSWVC7SDCGBWH9');
    foreach($tag->posts as $post)
    {
        echo $post->title;
    }

#### Customizing Pivot Table

By default, Active Record will assume that the name of the pivot table is the concatenated name of two models using an 
underscore in alphabetical order. So if the models are Post and `Tag`, the default pivot table name is `post_tag`.

If you want to use another name for the pivot table, you can specify in second parameter of the `belongsToMany()` method.

    <?php
    
    // Use a custom pivot table name
    $this->belongsToMany(Tag::class, 'custom_pivot_name');

You can also customize the name of associated keys in the pivot. By default, it uses the same convention as in 
One to One or One to Many. So for the example, in `post_tag` table, the fields will be post_id and tag_id.

To customize the key name, you can pass a third and/or fourth parameter. The third parameter is the associated key of 
the current model, while the fourth is for the related model.

Basically, this is what `belongsToMany()` will look like:

    <?php
    
    $this->belongsToMany(Tag::class, 'post_tag', 'post_id', 'tag_id');

### Working With Related Model's Record

Let's say a `Post` model might have many `Comment`. But when you are querying a post, probably you want to show the 
approved comments only, which in this case you have `status` equals to 1.

You can do it in two ways. The first one is by chaining the relation object with where method (or any Active Record class).

    <?php
    
    // Using example above
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    
    $comments = $post->comments()->where('status', 1)->get();
    foreach($comments as $comment)
    {
      echo $comment->text;
    }

Note that you need to call the `comments` as a method (`$post->comments()` instead of `$post->comments`). And you will 
always need to call the `get()` method at the end to finally fetch the records you want.

The second way is by chaining the `hasMany()` or `belongsToMany()` method right after you define the relationship.

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Comment;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';

        public function approvedComments()
        {
            return $this->hasMany(Comment::class)->where('status', 1);
        }
    }

This way, you can have a cleaner syntax without the need to call the `get()` method:

    <?php
    
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    
    foreach($post->approvedComments as $comment)
    {
      echo $comment->text;
    }

You can call `approvedComments` as a property to do the loop like in the example above, or you call it as a method to 
chain it again with another Active Record method. Just don't forget to call `get()` at the end.

    <?php
    
    // Show only 5 first comments
    $comments = $post->approvedComments()->limit(5)->get();
    
    // Or sort the comments by date
    $comments = $post->approvedComments()->orderBy('date', 'desc')->get();

## Eager Loading

### Using Eager Load

Eager loading is a technique to reduce the number of queries needed to relate one model to another:

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    use Comment;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';

        public function comments()
        {
            return $this->hasMany(Comment::class);
        }
    }

Then, for this example, we want to show all posts along with their comments:

    <?php
    
    $posts = Post::all();
    
    foreach($posts as $post)
    {
      echo $post->title;
    
      foreach($post->comments() as $comment)
        echo $comment->text;
    }

There's nothing wrong with that code, except that each time you call the relationship method, 
(the `comments()` method) to retrieve the comments, a new query is built. So imagine if we have 50 posts to be shown, 
that means the loop will run 51 queries (the 1 is for fetching all posts):

```sql
SELECT * FROM post;

SELECT * FROM comment WHERE post_id = '01K74SR0BRE4093D40SR087PPR';
SELECT * FROM comment WHERE post_id = '01K7A51H9EE1PSAQ3TW8897XTG';
SELECT * FROM comment WHERE post_id = '01K7A51JXJEFBBT89K10CA13H1';
...
```

To solve that problem, Expressive Active Record provides the support for eager loading:

    <?php
    
    $posts =  Post::all();
    $posts->load('comments');
    
    foreach($posts as $post)
    {
      echo $post->title;
    
      foreach($posts->comments as $comment)
        echo $comment->text;
    }

It will produce the same output, but with a drastic decrease in the number of queries. Instead of running N + 1 queries 
like the previous example, it will run queries like this:

```sql
SELECT * FROM post;
SELECT * FROM comment WHERE post_id IN ('01K74SR0BRE4093D40SR087PPR', '01K7A51H9EE1PSAQ3TW8897XTG', '01K7A51JXJEFBBT89K10CA13H1', .....);
```

The secret sauce is the `load()` method. Pass the name of the relation method (`comments`), then it will smartly build 
the query using the `IN` keyword and match each comment to the right post. Note that when fetching the comments using 
eager load, you should always call it as a property instead of as a method as in the example above 
(`$posts->comments`, not `$posts->comments()`).

## Accessors and Mutators

Sometimes you will want to transform some of your model's values when setting or getting them. The accessors will 
transform your model's value before returning it to your application, so you don't have to do the transformation 
yourself each time you need that value. While the mutators will transform it before you save it to the database, 
it frees yourself from doing it every time.

### Accessors

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';

        public function getAttrTitle($value)
        {
            return strtoupper($value);
        }
    }

Every time you echo or use the `title` field from a `Post` model, it will always be in all capital letters despite the 
actual value saved.

    <?php
    
    $post = Post::find('01K7A51JXJEFBBT89K10CA13H1');
    echo $post->title; // will echo something like 'A DIFFERENT TITLE'

### Mutators

    <?php
    
    use Qubus\Expressive\ActiveRecord\Model;
    
    class Post extends Model
    {
        protected string $primaryKey = 'id';
    
        protected ?string $tablePrefix = '';
    
        protected ?string $tableName = 'post';

        public function setAttrTitle($value)
        {
            return strtolower($value);
        }
    }

So when you save a new `Post` or update an existing one, the value `title` will be transformed into lowercase.

    <?php
    
    $post = new Post;
    $post->title = 'a different title';
    $post->save();

In example above, the value will be lowercased upon saving, so in the database, the `title` value will be: `a different title`.

### Conventions

When you want to declare a mutator/accessor method, here are some rules you need to understand:

* Method names need to in camelCase
* Accessors should be prefixed with `getAttr` while mutators with `setAttr` like in the examples above.
* Accessors and mutators actually receive two parameters. The first is the value of the field you want to transform, and the second is the model object (optional) in case you want to look for some reference to a different field.

```php
<?php
    
use Qubus\Expressive\ActiveRecord\Model;

class User extends Model
{
    protected string $primaryKey = 'id';

    protected ?string $tablePrefix = '';

    protected ?string $tableName = 'user';

    public function getAttrLastName($value, $model)
    {
        // look up the "gender" field to define salutation to be attached
        $salutation = $model->gender === 'male' ? 'Mr.' : 'Mrs.';
        return $salutation . ' '  . ucwords($value);
    }
}
```

You may define an accessor for a field that actually doesn't exist in database. For example, in your table, you only 
have `first_name` and `last_name` fields. If you want to show a full name, instead of echoing the fields one by one you 
can do this:

    <?php
    
    public function getAttrFullName($value, $model)
    {
        // $value will be empty since the field doesn't exist.
        // use another field instead
        return $model->first_name .' '. $model->last_name;
    }

## Miscellaneous

### Converting Models to Array / JSON

The Expressive Active Record query result is always returned as a special `Qubus\Expressive\ActiveRecord\Result` 
object. If you wish to work with plain arrays instead, you may convert it using `toArray()` method.

    <?php
    
    $users = User::all();

    return $users->toArray();

If you want to include a related model, you can use the eager load method:

    <?php
    
    $posts = Post::all();
    $posts->load('comments');
    
    return $posts->toArray();

You can also convert models to a JSON object instead. Especially if you work with Javascript libraries like 
[Backbone.js](https://backbonejs.org/). To do so you can call the `json()` method:

    <?php
    
    $posts = Post::all();
    $posts->load('comments');
    
    echo $posts->toJson();















