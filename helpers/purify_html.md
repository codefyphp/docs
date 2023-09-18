Description
-----------

Makes content safe to print on screen.

This function should only be used on output. Except uploading images, never use this function on input. 
All inputted data should be accepted and then purified on output for optimal results. For output of images, make sure 
to escape with `esc_url()`.

Usage
-----

    use function Qubus\Security\Helpers\purify_html;
    
    purify_html(string $string, bool $isImage = false): string;

Parameters
----------

**$string** (string) (required) Output to purify.

**$isImage** (bool) (optional) Whether the output is an image.

Return Value
------------

(string) The purified output.