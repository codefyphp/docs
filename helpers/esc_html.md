Description
-----------

Escapes html.

Usage
-----

    <?php

    use function Qubus\Security\Helpers\esc_html;
    
    esc_html(string $string): string;

Parameters
----------

**$string** (string) (required) Html element to escape.

Return Value
------------

(string) Escaped HTML output.