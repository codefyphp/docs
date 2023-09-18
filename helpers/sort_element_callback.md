Description
-----------

Sorts a structured array by `Name` property.

Usage
-----

    use function Qubus\Support\Helpers\sort_element_callback;
    
    sort_element_callback(array $a, array $b): int;

Parameters
----------

**$a** (array) (required) First item for comparison. The compared items should be associative arrays that optionally 
include a `Name` key.

**$b** (array) (required) Second item for comparison.

Return Value
------------

(bool) Return 0, -1, or 1 based on two string comparison.