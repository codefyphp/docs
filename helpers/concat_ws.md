Description
-----------

Concatenation with separator.

Usage
-----

    use function Qubus\Support\Helpers\concat_ws;
    
    concat_ws(string $string1, string $string2, string $separator = ',', ...$strings): string;

Parameters
----------

**$string1** (string) (required) Left string.

**$string2** (string (required) Right string.

**$separator** (string) (optional) Delimiter to use between strings. Default: comma.

**$…strings** (optional) List of strings.

Return Value
------------

(string) Concatenated string.