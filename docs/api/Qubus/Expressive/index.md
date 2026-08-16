# Documentation

This is an automatically generated documentation for **Documentation**.

## Namespaces

### \Qubus\Expressive

#### Classes

| Class                                                                          | Description |
|--------------------------------------------------------------------------------|-------------|
| [`DbalException`](DbalException.md)                 |             |
| [`DsnGenerator`](DsnGenerator.md)                   |             |
| [`Expression`](Expression.md)                       |             |
| [`Identifier`](Identifier.md)                       |             |
| [`ParsePdoDsn`](ParsePdoDsn.md)                     |             |
| [`QueryBuilder`](QueryBuilder.md)                   |             |
| [`QueryBuilderException`](QueryBuilderException.md) |             |
| [`ResultSet`](ResultSet.md)                         |             |
| [`Schema`](Schema.md)                               |             |
| [`Structure`](Structure.md)                         |             |

#### Interfaces

| Interface                                                | Description |
|----------------------------------------------------------|-------------|
| [`Aggregate`](Aggregate.md)   |             |
| [`Connection`](Connection.md) |             |
| [`Database`](Database.md)     |             |
| [`Delete`](Delete.md)         |             |
| [`Insert`](Insert.md)         |             |
| [`Join`](Join.md)             |             |
| [`Select`](Select.md)         |             |
| [`Set`](Set.md)               |             |
| [`Singleton`](Singleton.md)   |             |
| [`Table`](Table.md)           |             |
| [`Update`](Update.md)         |             |
| [`Where`](Where.md)           |             |

### \Qubus\Expressive\ActiveRecord

#### Classes

| Class                                                         | Description |
|---------------------------------------------------------------|-------------|
| [`Model`](ActiveRecord/Model.md)   |             |
| [`Result`](ActiveRecord/Result.md) |             |
| [`Row`](ActiveRecord/Row.md)       |             |

### \Qubus\Expressive\ActiveRecord\Exception

#### Classes

| Class                                                                                         | Description |
|-----------------------------------------------------------------------------------------------|-------------|
| [`ReadOnlyException`](ActiveRecord/Exception/ReadOnlyException.md) |             |

### \Qubus\Expressive\ActiveRecord\Relations

#### Classes

| Class                                                                                 | Description |
|---------------------------------------------------------------------------------------|-------------|
| [`BelongsTo`](ActiveRecord/Relations/BelongsTo.md)         |             |
| [`BelongsToMany`](ActiveRecord/Relations/BelongsToMany.md) |             |
| [`HasMany`](ActiveRecord/Relations/HasMany.md)             |             |
| [`HasOne`](ActiveRecord/Relations/HasOne.md)               |             |
| [`Relation`](ActiveRecord/Relations/Relation.md)           |             |

### \Qubus\Expressive\Connection

#### Classes

| Class                                                                           | Description |
|---------------------------------------------------------------------------------|-------------|
| [`DriverConnection`](Connection/DriverConnection.md) |             |
| [`PdoConnection`](Connection/PdoConnection.md)       |             |

### \Qubus\Expressive\Connection\Pdo

#### Classes

| Class                                                           | Description |
|-----------------------------------------------------------------|-------------|
| [`Mysql`](Connection/Pdo/Mysql.md)   |             |
| [`Oci`](Connection/Pdo/Oci.md)       |             |
| [`Pgsql`](Connection/Pdo/Pgsql.md)   |             |
| [`Sqlite`](Connection/Pdo/Sqlite.md) |             |
| [`Sqlsrv`](Connection/Pdo/Sqlsrv.md) |             |

### \Qubus\Expressive\DataMapper

#### Classes

| Class                                                                                 | Description |
|---------------------------------------------------------------------------------------|-------------|
| [`DataMapperException`](DataMapper/DataMapperException.md) |             |
| [`Entity`](DataMapper/Entity.md)                           |             |
| [`PdoDataMapper`](DataMapper/PdoDataMapper.md)             |             |
| [`Property`](DataMapper/Property.md)                       |             |
| [`SerializableEntity`](DataMapper/SerializableEntity.md)   |             |

#### Interfaces

| Interface                                                           | Description |
|---------------------------------------------------------------------|-------------|
| [`DataMapper`](DataMapper/DataMapper.md) |             |

### \Qubus\Expressive\Migration

#### Classes

| Class                                                            | Description |
|------------------------------------------------------------------|-------------|
| [`Migration`](Migration/Migration.md) |             |
| [`Migrator`](Migration/Migrator.md)   |             |

### \Qubus\Expressive\Migration\Adapter

#### Classes

| Class                                                                                          | Description |
|------------------------------------------------------------------------------------------------|-------------|
| [`DbalMigrationAdapter`](Migration/Adapter/DbalMigrationAdapter.md) |             |
| [`FileMigrationAdapter`](Migration/Adapter/FileMigrationAdapter.md) |             |

#### Interfaces

| Interface                                                                                                            | Description |
|----------------------------------------------------------------------------------------------------------------------|-------------|
| [`ConnectionAwareMigrationAdapter`](Migration/Adapter/ConnectionAwareMigrationAdapter.md) |             |
| [`MigrationAdapter`](Migration/Adapter/MigrationAdapter.md)                               |             |

### \Qubus\Expressive\Migration\Seeder

#### Classes

| Class                                                                                   | Description |
|-----------------------------------------------------------------------------------------|-------------|
| [`BaseSeeder`](Migration/Seeder/BaseSeeder.md)               |             |
| [`SeederContext`](Migration/Seeder/SeederContext.md)         |             |
| [`SeederTransaction`](Migration/Seeder/SeederTransaction.md) |             |

#### Interfaces

| Interface                                                         | Description |
|-------------------------------------------------------------------|-------------|
| [`Seeder`](Migration/Seeder/Seeder.md) |             |

### \Qubus\Expressive\Migration\Seeder\Attribute

#### Classes

| Class                                                                             | Description |
|-----------------------------------------------------------------------------------|-------------|
| [`DependsOn`](Migration/Seeder/Attribute/DependsOn.md) |             |

### \Qubus\Expressive\Schema

#### Classes

| Class                                                               | Description |
|---------------------------------------------------------------------|-------------|
| [`AlterColumn`](Schema/AlterColumn.md)   |             |
| [`AlterTable`](Schema/AlterTable.md)     |             |
| [`BaseColumn`](Schema/BaseColumn.md)     |             |
| [`Compiler`](Schema/Compiler.md)         |             |
| [`CreateColumn`](Schema/CreateColumn.md) |             |
| [`CreateTable`](Schema/CreateTable.md)   |             |
| [`ForeignKey`](Schema/ForeignKey.md)     |             |

### \Qubus\Expressive\Schema\Compiler

#### Classes

| Class                                                                    | Description |
|--------------------------------------------------------------------------|-------------|
| [`MySQL`](Schema/Compiler/MySQL.md)           |             |
| [`Oracle`](Schema/Compiler/Oracle.md)         |             |
| [`PostgreSQL`](Schema/Compiler/PostgreSQL.md) |             |
| [`SQLite`](Schema/Compiler/SQLite.md)         |             |
| [`SQLServer`](Schema/Compiler/SQLServer.md)   |             |

### \Qubus\Expressive\Traits

#### Traits

| Trait                                                                     | Description |
|---------------------------------------------------------------------------|-------------|
| [`IdentifierAware`](Traits/IdentifierAware.md) |             |
