Description
-----------

Appends a trailing slash.

Will remove trailing forward and backslashes if it exists already before adding a trailing forward slash. This prevents 
double slashing a string or path.

Usage
-----

    <?php

    use function Qubus\Support\Helpers\add_trailing_slash;
    
    add_trailing_slash(string $string): string;

Parameters
----------

**$string** (string) (required) What to add the trailing slash to.

Return Value
------------

(string) String with trailing slash.