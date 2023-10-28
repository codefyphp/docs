Description
-----------

Properly strip all HTML tags including script and style (default).

This differs from PHP’s native `strip_tags()` function because this function removes the contents of the tags. E.g. 
`strip_tags__( '<script>something</script>' )` will return `''`.

Usage
-----

    <?php

    use function Qubus\Security\Helpers\strip_tags__;

    strip_tags__(
        string $string,
        bool $removeBreaks = false,
        string $tags = '',
        bool $invert = false
    ): string;

Parameters
----------

**$string** (string) (required) String containing HTML tags.

**$removeBreaks** (bool) (optional) Whether to remove left over line breaks and white space chars.

**$tags** (string) (optional) Tags that should be removed.

**$invert** (bool) (optional) Instead of removing tags, this option checks for which tags to not remove.

Return Value
------------

(string) The processed string after the `strip_tags` filter has been applied.

Example
-------

    <?php

    $string = '<b>sample</b> text with <div>tags</div>';
    
    strip_tags__($string); //returns 'text with'

    strip_tags__($string, false, '<b>'); //returns '<b>sample</b> text with'

    strip_tags__($string, false, '<b>', true); //returns 'text with <div>tags</div>'