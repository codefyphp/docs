In the skeleton starter app, a config file for database migrations can be found at `bootstrap/phpmig.php`. Codefy 
Migrations is a fork of [phpmig](https://github.com/davedevelopment/phpmig).

Getting Started
---------------

You can generate migrations by using the `migrate:generate` command. Migration files follow this naming convention: 
`versionnumber_name.php`, where version number is made of 0-9 and name is CamelCase or snake_case. Each migration file 
should contain a class with the same name as the file in CamelCase.

    ❯ php codex migrate:generate CreateTemplateTable
    +f ./database/migrations/20230908035134_CreateTemplateTable.php
    
    ❯ php codex migrate:status
    +--------+------------------+-----------------------+                                                                                                                 
    | Status | Migration ID     | Migration Name        |
    +--------+------------------+-----------------------+
    | down   |  20230908035134  | CreateTemplateTable   |
    +--------+------------------+-----------------------+
    
    ❯ php codex migrate
     == 20230908035134 CreateTemplateTable migrating
     == 20230908035134 CreateTemplateTable migrated 0.0090s
    
    ❯ php codex migrate:status
    +--------+------------------+-----------------------+                                                                                                                  
    | Status | Migration ID     | Migration Name        |
    +--------+------------------+-----------------------+
    | up     |  20230908035134  | CreateTemplateTable   |
    +--------+------------------+-----------------------+

Rollback
--------

Rollback the last run migration:

    ❯ php codex migrate:rollback 

To rollback all migrations up to a specific migration you can specify the rollback target:

    ❯ php codex migrate:rollback -t 20220925064056
    // or
    ❯ php codex migrate:rollback --target 20220925064056

Revert all migrations by specifying `0`:

    ❯ php codex migrate:rollback -t 0

You can also rollback a specific migration using the down command:

    ❯ php codex migrate:down 20220925064056