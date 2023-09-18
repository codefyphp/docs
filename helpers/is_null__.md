Description
-----------

Checks if a variable is null.

Works the same as PHP’s native `is_null()` function. If `$var` is not set, an `Undefined variable` notice will be thrown.

Usage
-----

    use function Qubus\Support\Helpers\is_null__;
    
    is_null__(mixed $var): bool;

Parameters
----------

**$var** (mixed) (required) Variable to check.

Return Value
------------

(bool) Returns `true` if null, `false` otherwise.