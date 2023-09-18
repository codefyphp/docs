Description
-----------

SQL Where operator in PHP.

Usage
-----

    use function Qubus\Support\Helpers\php_where;
    
    php_where(string $key, string $operator, mixed $pattern): bool;

Parameters
----------

**$key** (string) (required) Term to search.

**$operator** (string) (required) The filter to perform.

**$pattern** (mixed) (required) Term to check against.

Return Value
------------

(bool) Will return `true` if condition matches, `false` otherwise.

Example
-------

    // Where dog is in ['cat', 'bear', 'chicken', 'dog']
    php_where('dog', 'in', ['cat', 'bear', 'chicken', 'dog']); // true