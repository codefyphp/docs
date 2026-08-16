---
title: Database
sidebar_title: Database
weight: 0
---

## Installation

```shell
composer require qubus/expressive
```

Expressive is a PDO-based database toolkit for PHP 8.4 and later. It provides connection helpers, a fluent query
builder, schema and migration support, Active Record, and DataMapper.

Start with the component that matches the application boundary:

- [Connections](connections.md) explains supported drivers, DSNs, parameter binding, transactions, and connection
  isolation.
- [QueryBuilder](query-builder.md) documents fluent selects, writes, filters, aggregates, joins, and direct SQL.
- [DataMapper](data-mapper.md) maps typed persistence-independent entities.
- [Active Record](active-record.md) combines row data and persistence behavior in models.
- [Migrations](migrations.md) generate and run database schema migrations.

Query values should always be passed as bound parameters. SQL identifiers and expressions must come from trusted
application code or an explicit allowlist.

## Configuration

The database configuration for Codefy is located at `./config/database.php`.

### SQLite

Sqlite is the default database configured for Codefy. The sample environment file is already set up to use SQLite. But 
first, make sure that you've gone through the initial [configuration](../getting-started/configuration.md) of your app, 
so that Codefy is aware of your `base path`. When you run the migration command `php codex migrate`, the database will 
get created and then the migrations will run.
