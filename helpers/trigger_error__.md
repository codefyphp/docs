Description
-----------

Wrapper function for the core PHP function: `trigger_error`.

This function makes the error a little more understandable for the end user to track down the issue.

Usage
-----

    <?php

    use function Qubus\Support\Helpers\trigger_error__;
    
    trigger_error__(string $message, int $level = E_USER_NOTICE): void;

Parameters
----------

**$message** (string) (required) Custom message to print.

**$level** (int) (optional) Predefined PHP error constant.

Return Value
------------

(void)