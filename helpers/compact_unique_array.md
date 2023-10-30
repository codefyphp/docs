Description
-----------

Strips out all duplicate values and compact the array.

Usage
-----

    <?php

    use function Qubus\Support\Helpers\compact_unique_array;
    
    compact_unique_array(array $a): array;

Parameters
----------

**$a** (array) (required) An array to be compacted.

Return Value
------------

(bool) The unique array after its been compacted.