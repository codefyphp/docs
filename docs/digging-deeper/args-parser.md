---
title: Argument Parser
sidebar_title: Argument Parser
order: 34
---

The `Codefy\Framework\Support\ArgsParser` class takes arguments (arrays, objects, or strings), normalizes them into 
arrays, and merges them with defaults.

## Examples

### Simple Merge

    <?php
    
    $defaults = [
        'host' => 'localhost',
        'port' => 3306,
        'user' => 'root',
    ];
    
    $args = [
        'port' => 3307,
    ];
    
    $result = ArgsParser::parse($args, $defaults);

**Result:**

```text
[
    'host' => 'localhost',
    'port' => 3307,   // overridden
    'user' => 'root',
]
```

### Deep Merge

    <?php
    
    $defaults = [
        'db' => [
            'host' => 'localhost',
            'port' => 3306,
        ],
        'debug' => false,
    ];
    
    $args = [
        'db' => [
            'port' => 3307,
        ],
    ];
    
    $result = ArgsParser::parse($args, $defaults, deep: true);

**Result:**

```text
[
    'db' => [
        'host' => 'localhost',
        'port' => 3307,   // merged instead of replacing whole 'db'
    ],
    'debug' => false,
]
```

!!! note "Replacement"
    With a simple merge, the entire `db` array would have been replaced with `['port' => 3307]`.

### Object Input

    <?php
    
    class Config {
        public string $host = '127.0.0.1';
        public int $port = 8080;
    }
    
    $args = new Config();
    
    $defaults = [
        'host' => 'localhost',
        'port' => 80,
        'debug' => false,
    ];
    
    $result = ArgsParser::parse($args, $defaults);

**Result:**
```text
[
    'host' => '127.0.0.1',
    'port' => 8080,
    'debug' => false,
]
```



