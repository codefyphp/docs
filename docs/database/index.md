---
title: Database
sidebar_title: Database
weight: 0
---

## Installation

```shell
composer require qubus/expressive
```

## Introduction

CodefyPHP comes with a very simple database abstraction layer, a wrapper for `PDO` with a query builder.
Codefy's DBAL and Query Builder supports a variety databases using raw SQL. Currently, Codefy provides support for 
five databases:

* MariaDB 10+
* MySQL 5.7
* PostgreSQL
* SQLite 3.26.0+
* SQL Server

## Configuration

The database configuration for Codefy is located at `./config/database.php`.

### SQLite

Sqlite is the default database configured for Codefy. The sample environment file is already set up to use SQLite. But 
first, make sure that you've gone through the initial [configuration](../getting-started/configuration.md) of your app, 
so that Codefy is aware of your `base path`. When you run the migration command `php codex migrate`, the database will 
get created and then the migrations will run.

## Database Abstraction Layer

    <?php

    use Exception;
    use Codefy\Framework\Proxy\Codefy;
    
    try {
        $dbal = Codefy::$PHP->getDbConnection();
    } catch (Exception $e) {
        return $e->getMessage();
    }

### query()

The `query` method accepts a raw query along with optional parameters for binding.

    <?php
    
    $post = $dbal->query("SELECT * FROM posts");

### all()

The `all()` method fetch's all results.

    <?php
    
    $post = $dbal->query("SELECT * FROM posts")
        ->all();

### fetchAssoc()

The `fetchAssoc()` method fetch's each result as an associative array. It returns a `PDOStatement`. To get the array,
you must append with the `all()` method.

    <?php
    
    $post = $dbal->query("SELECT * FROM posts WHERE post_id = ?", [0 => '01K74SR0BRE4093D40SR087PPR'])
        ->fetchAssoc()
        ->all();

### first()

The `first()` method fetch's the first result.

    <?php
    
    $post = $dbal->query("SELECT * FROM posts")
        ->first();

### next()

The `next()` method fetch's the next result. If there is no next result, `false` will be returned.

    <?php
    
    $post = $dbal->query("SELECT * FROM posts WHERE post_id = ?", [0 => '01K74SR0BRE4093D40SR087PPR'])
        ->next();

### count()

The `count()` method counts affected rows.

    <?php
    
    $post = $dbal->query("SELECT * FROM posts")
        ->next();

### column()

The `column()` method returns a column.

    <?php
    
    $post = $dbal->query("SELECT * FROM posts")
        ->column(2);

