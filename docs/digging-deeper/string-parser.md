---
title: String Parser
sidebar_title: String Parser
summary: Parse query-style strings into structured PHP data with defaults, optional placeholders, array keys, strict validation, and URL-decoded input.
keywords: php-string-parser,query-string,argument-parsing
order: 33
---

The `Codefy\Framework\Support\StringParser` class turns query strings like `foo=bar&baz=1` into arrays. 
The `StringParser` can handle both normal keys and array style keys `tags[]=php&tags[]=code`.

## Examples

### Simple Parse

    <?php
    
    $query = "foo=bar&baz=123";
    
    $result = StringParser::parse($query);
    
    // Result:
    [
        'foo' => 'bar',
        'baz' => '123',
    ]

### With Defaults

    <?php
    
    $query = "foo=bar";
    
    $defaults = [
        'foo' => 'default',
        'baz' => 'not-set',
    ];
    
    $result = StringParser::parse($query, $defaults);
    
    // Result:
    [
        'foo' => 'bar',      // overridden
        'baz' => 'not-set',  // from defaults
    ]

### Handling `?`

    <?php
    
    $query = "?foo=bar&baz=1";
    
    $result = StringParser::parse($query);
    
    // Result:
    [
        'foo' => 'bar',
        'baz' => '1',
    ]

### Array Style Keys

    <?php
    
    $query = "tags[]=php&tags[]=code&tags[]=framework";
    
    $result = StringParser::parse($query);
    
    // Result:
    [
        'tags' => ['php', 'code', 'framework']
    ]

### Strict Mode

    <?php
    
    $query = "=missingkey&foo=bar";
    
    $result = StringParser::parse($query, strict: true);
    
    // Result:
    [
        'foo' => 'bar'
    ]
    // the malformed `=missingkey` is skipped

### URL Encoded Input

    <?php
    
    $query = "city=New%20York&lang=en";
    
    $result = StringParser::parse($query);
    
    // Result:
    [
        'city' => 'New York',
        'lang' => 'en',
    ]

