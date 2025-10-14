---
title: esc_textarea
sidebar_title: esc_textarea
---

Description
-----------

Escapes for textarea.

Usage
-----

    <?php

    use function Qubus\Security\Helpers\esc_textarea;
    
    esc_textarea(string $string): string;

Parameters
----------

**$string** (string) (required) String to escape.

Return Value
------------

(string) Escaped string.