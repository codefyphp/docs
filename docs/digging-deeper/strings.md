---
title: Strings
sidebar_title: Strings
order: 30
---

## Installation

```shell
composer require qubus/support
```

Codefy includes a set of string helpers that you can use throughout your application if you deem them helpful.

The class also contains multibyte agnostic versions of PHP's multibyte-aware functions in category 2, as defined on 
this page. They are drop-in replacements for both versions. For example, you can replace both `strlen()` and 
`mb_strlen()` with `Qubus\Support\StringHelper::strlen()`, which will return a multibyte aware result based on whether 
PHP's mbstring extension is loaded.

To instantiate the `StringHelper` class, you can use Codefy's global property:

    <?php
    
    $helper = Codefy\Framework\Codefy::$PHP->string;

## alternator()

The `alternator()` method returns a closure that will alternate the values you've passed to this method as arguments, 
unless you call the closure with `false` as argument - in which case it will just return the value without moving to 
the next and return the same value on the next call.

    <?php
    
    $alt = $helper->alternator('one', 'two', 'three', 'four');
    
    echo $alt(); // outputs 'one'
    echo $alt(); // outputs 'two'
    echo $alt(false); // outputs 'three', but doens't move to the next as you can see in the next call
    echo $alt(); // outputs 'three'
    echo $alt(); // outputs 'four'
    echo $alt(); // outputs 'one'
    // etc...

## endsWith()

The `endsWith()` method checks whether a string has a specific ending.

    <?php
    
    $string = "Lorem ipsum dolor sit amet";
    
    echo $helper->endsWith(str: $string, end: 'amet'); // returns true
    echo $helper->endsWith(str: $string, end: 'Amet'); // returns false
    echo $helper->endsWith(str: $string, end: 'Amet', ignoreCase: true); // returns true

## increment()

The `increment()` method allows you to append a number to the end of a string or increment that number if it already exists.

    <?php


    $string = "filename";
    echo $helper->increment(str: $string); // returns filename_1
    
    $string = "filename_1";
    echo $helper->increment(str: $string); // returns filename_2
    
    $string = "filename";
    echo $helper->increment(str: $string, first: 3); // returns filename_3

## isHtml()

The `isHtml()` method checks if a string is html.

    <?php
    
    $string = "Lorem <strong>ipsum dolor</strong> sit amet";
    
    echo $helper->isHtml(string: $string); // returns true

## isJson()

The `isJson()` method checks if a string is json encoded.

    <?php
    
    echo $helper->isJson(string: '{"0":"An","encoded":["string"]}'); // returns true

## isXml()

The `isXml()` method checks if a string is valid xml. Requires the [libxml](http://www.php.net/manual/en/ref.libxml.php) 
extension.

    <?php
    
    echo $helper->isXml(string: '<?xml version="1.0" encoding="utf-8"?><xml><foo>bar</foo></xml>');
    // returns true

## isSerialized()

The `isSerialized()` method checks if a string is serialized.

    <?php
    
    echo $helper->isSerialized(string: 'a:2:{i:0;s:2:"An";s:7:"encoded";a:1:{i:0;s:6:"string";}}');
    // returns true

## lcfirst()

The `lcfirst()` method confirts the first letter of a string to lowercase. Please note that `lcfirst` does not use 
[`strtoupper`](https://www.php.net/manual/en/function.strtoupper.php).

    <?php
    
    echo $helper->lcfirst(str: 'LOWER');
    // returns lOWER

## random()

The `random()` method generates a random string based on the type given.

    <?php
    
    // alnum (uppercase and lowercase letters mixed with numbers)
    echo $helper->random(type: 'alnum', length: 16);
    // Returns: SvZi9Dh3lq7zQYim
    
    // numeric (just numbers)
    echo $helper->random(type: 'numeric', length: 16);
    // Returns: 1045343964672481
    
    // nozero (just numbers excluding zero)
    echo $helper->random(type: 'nozero', length: 16);
    // Returns: 3244623373994515
    
    // alpha (just uppercase and lowercase letters)
    echo $helper->random(type: 'alpha', length: 16);
    // Returns: LuVAXbmxQbbWoYqz
    
    // distinct (uppercase letters and numbers that cannot be confused)
    echo $helper->random(type: 'distinct', length: 16);
    // Returns: R79MPKMH4KTRN35J
    
    // hexdec (hexadecimal characters a-f, 0-9)
    echo $helper->random(type: 'hexdec', length: 16);
    // Returns: 09c34e42f36547f8
    
    // unique (32 character string based on md5)
    echo $helper->random(type: 'unique');
    // Returns: ed4bb844a35b7a4edb7eed0d3795d328
    
    // sha1 (40 character string based on sha1)
    echo $helper->random(type: 'sha1');
    // Returns: af5c5a8cc3be9a3180205c1ed2975015cd6cf1e7
    
    // uuid (version 4 - random)
    echo $helper->random(type: 'uuid');
    // Returns: f47ac10b-58cc-4372-a567-0e02b2c3d479

## startsWith()

The `startsWith()` method checks whether a string has a precific beginning.

    <?php
    
    $string = "Lorem ipsum dolor sit amet";
    
    echo $helper->startsWith($string, 'Lorem'); // returns true
    echo $helper->startsWith($string, 'lorem'); // returns false
    echo $helper->startsWith($string, 'lorem', true); // returns true

## tr()

The `tr()` method parses the params from the given string using PHP's 
[`strtr()`](https://www.php.net/manual/en/function.strtr.php) function.

    <?php
    
    echo $helper->tr(string: 'Hello, :name', array: ['name' => 'Joshua']); // returns 'Hello, Joshua'

## truncate()

The `truncate()` method allows you to limit characters and provide a continuation string without breaking html.

    <?php
    
    $string = "Lorem ipsum dolor sit amet, consectetur adipiscing elit.";
    echo $helper->truncate(string: $string, limit: 15); // returns Lorem ipsum dol...
    
    $string = "Lorem ipsum dolor sit amet, consectetur adipiscing elit.";
    echo $helper->truncate(string: $string, limit: 15, continuation: '...Read More'); // returns Lorem ipsum dol...Read More







