---
title: Data Mapper
sidebar_title: Data Mapper
keywords: orm,active-record,data-mapper
weight: 1
---

Expressive ORM also has a very simple Data Mapper along with the Active Record.

## Create Entity Class

    <?php
    
    use Qubus\Expressive\DataMapper\Entity;
    use Qubus\Expressive\DataMapper\Property;
    use Qubus\Expressive\DataMapper\SerializableEntity;
    
    #[Entity('post')]
    class Post extends SerializableEntity
    {
        #[Property('id')]
        public int|string $id;
    
        #[Property('author')]
        public int $author;
    
        #[Property('category')]
        public string $category;
    
        #[Property('title')]
        public string $title;
    
        #[Property('slug')]
        public string $slug;
    
        #[Property('content')]
        public string $content;
    
    }

## Call the Data Mapper

    <?php
    
    use Qubus\Expressive\DataMapper\PdoDataMapper;
    use Post;
    
    // Instantiate the data mapper by passing a PDO instance and the entity class name.
    $dm = new PdoDataMapper($pdo, Post::class);
    
    // Retrieve all posts
    $dm->findAll();
    
    // Retrieve all posts by category
    $dm->findAllBy('category', 'General');
    
    // Retrieve a single post with the id = 1
    $dm->findOne('01K7A51JXJEFBBT89K10CA13H1');
    
    // Save a post instance to the database
    $post = new Post();
    $post->category = 'Living';
    $post->title = 'How to Create A Lavish Lifestyle';
    $post->content = 'Living a lavish lifestyle is not ...';
    $post = $dm->create($post);
    
    // Update a post
    $post->category = 'Lifestyle';
    $post = $dm->update($post);
    
    // Delete a post with the id = 01K7A51JXJEFBBT89K10CA13H1
    $dm->delete('01K7A51JXJEFBBT89K10CA13H1');
