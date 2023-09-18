Description
-----------

Translates a string.

Usage
-----

    use function Qubus\Security\Helpers\t__;
    
    t__(string $msgid, string $domain = ''): string;

Parameters
----------

**$msgid** (string) (required) The string to be translated.

**$domain** (string) (optional) Domain lookup for translated text.

Return Value
------------

(string) Translated text according to current locale.