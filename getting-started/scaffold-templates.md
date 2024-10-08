Scaffold contains two templating engines to make it easier to use what you need for any project. One is 
Scaffold:Native while the other is Scaffold:Compiler. Scaffold:Compiler is a fork of Flow from which Twig was born.

## Scaffold:Native Engine

Scaffold:Native is not a compiler template engine. It uses native PHP syntax similar to Plates and FoilPHP. Like majority
of template engines, Scaffold:Native supports inheritance through blocks. Furthermore, child templates declare blocks
that can be overridden, extended and displayed by parent templates.

All Scaffold:Native templates must follow the `namepace::/path/to/template` format.


    <?php

    $this->parent('main::layout');
    $this->block('content', function ($params) {

    ?>
    <article>
        <header>
            <h1><?=$this->esc($this->ucfirst($params['title']));?></h1>
        </header>
        <main>
            <?php foreach($params['paragraphs'] as $paragraph): ?>
                <p>
                    <?=$this->esc($paragraph);?>
                </p>
            <?php endforeach; ?>
        </main>
    </article>
    <?php }); ?>



    <html>
        <head>
            <title><?=$this->esc($title);?></title>
        </head>
        <body>
            <?=$this->block('content');?>
        </body>
    </html>

Namespace and function callbacks are registered with the templating engine when it is constructed. Function callbacks
area available as methods within the template context and must be `callable`.

The default template extension is `phtml`, and all template files live in the `resources/views` folder.

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Http\Controllers;
    
    use Codefy\Framework\Http\BaseController;
    use Qubus\View\Native\Exception\InvalidTemplateNameException;
    use Qubus\View\Native\Exception\ViewException;

    use function Qubus\Security\Helpers\die__;
    
    final class HomeController extends BaseController
    {
        /**
         * @throws ViewException
         * @throws InvalidTemplateNameException
         */
        public function index(): ?string
        {
            $params = [
                'title' => 'CodefyPHP Framework',
                'paragraphs' => [
                    'My first paragraph.',
                    'My second paragraph.',
                ],
            ];
            
            try {
                return $this->view->render('framework::home', $params);
            } catch (InvalidTemplateNameException | ViewException $e) {
                die__($e->getMessage());
            }
        }
    }

### Registered Function Callbacks
- `strip` - Properly strip all HTML tags including script and style (default). This differs from PHP's native strip_tags()
  function because this function removes the contents of the tags.
    - Parameters
        - `string $string` - String containing HTML tags
        - `bool $removeBreaks` - Optional. Whether to remove left over line breaks and white space characters.
        - `string $tags` - Tags that should be removed.
        - `bool $invert` - Instead of removing tags, this option checks for which tags to not remove. Default: false.
- `trim` - Removes all whitespace.
- `upper` - Make a string uppercase (similar to `ucwords`).
- `lower` - Make a string lowercase.
- `ucfirst` - Uppercase the first character in a string.
- `lcfirst` - Lowercase the first character in a string.
- `ucwords` - Uppercase the first character of each word in a string.
- `esc` - Escaping for HTML output.
- `escJs` - Escaping for inline javascript.
- `escUrl` - Escaping for url.
- `purify` - Makes content safe to print on screen. To be used instead of `esc` for escaping rich text.
- `truncate` - Truncates a string to the given length. It will optionally preserve HTML tags if `$isHtml` is set to true.
    - Parameters
        - `string $string` The string to truncate.
        - `int $limit` The number of characters to truncate.
        - `string $continuation` The string to use to denote it was truncated. Default ...
        - `bool $isHtml` Whether the string has HTML.
- `concat` - Concatenation with separator (strings only).
    - Parameters
        - `string $string1`    Left string.
        - `string $string2 `   Right string.
        - `string $separator`  Delimiter to use between strings. Default: comma.
        - `string ...$strings` List of strings.

## Scaffold:Compiler Engine

### Usage

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Http\Controllers;
    
    use Codefy\Framework\Http\BaseController;
    use Qubus\View\Loader;
    use Qubus\View\Native\Exception\InvalidTemplateNameException;
    use Qubus\View\Native\Exception\ViewException;

    use function Codefy\Framework\Helpers\resource_path;
    use function Qubus\Security\Helpers\die__;
    
    final class HomeController extends BaseController
    {

        public function __construct(
            SessionService $sessionService,
            Router $router,
            ?Renderer $view = null
        ) {
            $this->view = new Loader([
                'source' => [resource_path('views')],
                'target' => resource_path('views/cache'),
                'extension' => '.phtml',
            ]);

            parent::__construct($sessionService, $router, $this->view);
        }
        /**
         * @throws ViewException
         * @throws InvalidTemplateNameException
         */
        public function index(): ?string
        {
            $params = [
                'user' => [
                    'data_1' => '<p>This is a paragraph that will probably be escaped if I don\'t intervene.</p>',
                    'data_2' => 'My second data',
                    'first_name' => 'Joshua',
                    'last_name' => 'Parker',
                    'fullname' => fn ($self) => $self['first_name'] . ' ' . $self['last_name']
                ],
            ];
            
            try {
                return $this->view->render('home', compact($params);
            } catch (InvalidTemplateNameException | ViewException $e) {
                die__($e->getMessage());
            }
        }
    }

The `Loader` class takes an array of parameters:

- `source` - Path to your templates (can be a string, an array, or callable).
- `target` - Path to the where templates are compiled.
- `helpers` - An array of custom helper functions to register (i.e. `['caps' => 'strtoupper']`).
- `extention` - Extension used for your templates (recommended: '.html', '.phtml', '.php'). The default is `.html'.
- `mode` - Compiler mode.
    - ```Loader::RECOMPILE_NEVER``` - Never recompile an already compiled template.
    - ```Loader::RECOMPILE_NORMAL``` - Only recompile if the compiled template is older
      than the source file due to modifications.
    - ```Loader::RECOMPILE_ALWAYS``` - Always recompile whenever possible.

### Basis Concepts

Scaffold uses `{%` and `%}` to delimit block tags. Block tags are used mainly for
block declarations in template inheritance and control structures. Examples of
block tags are `block`, `for`, and `if`. Some block tags may have a body
segment. They're usually enclosed by a corresponding `end<tag>` tag. Scaffold uses
`{{` and `}}` to delimit output tags, `{!` and `!}` to delimit raw output tags,
and `{#` and `#}` to delimit comments. Keywords and identifiers are
*case-sensitive*.

### Comments

Use `{#` and `#}` to delimit comments:

    {# This is a comment. It will be ignored. #}

Comments may span multiple lines but cannot be nested; they will be completely
removed from the resulting output.

### Expression Output

To output a literal, variable, or any kind of expression, use the opening `{{`
and the closing `}}` tags:

    Hello, {{ username }}

    {{ "Welcome back, " ~ username }}

    {{ "Two plus two equals " ~ 2 + 2 }}

### Raw Expression Output

To output a raw expression without doing any output escaping, use the opening
`{!` and the closing `!}` tags:

    The following will be HTML bold: {! "<b>bold text</b>" !}

### Literals

There are several types of literals: numbers, strings, booleans, arrays, and
`null`.

#### Numbers

Numbers can be integers or floats:

    {{ 42 }} and {{ 3.14 }}

Large numbers can be separated by underscores to make it more readable:

    Price: {{ 12_000 | numberFormat }} USD

The exact placing of _ is insignificant, although the first character must be a
digit; any _ character inside numbers will be removed. Numbers are translated
into PHP numbers and thus are limited by how PHP handles numbers with regards to
upper/lower limits and precision. Complex numeric and monetary operations should
be done in PHP using the GMP extension or the bcmath extension instead.

#### Strings

Strings can either be double-quoted or single quoted; both recognize escape
sequence characters. There are no support for variable extrapolation. Use string
concatenation instead:

    {{ "This is a string " ~ 'This is also a string' }}

You can also join two or more strings or scalars using the join operator:

    {{ "Welcome," .. user.name }}

The join operator uses a single space character to join strings together.

#### Booleans

    {{ true }} or {{ false }}

When printed or concatenated, `true` will be converted to `1` while `false` will
be converted to an empty string.

#### Arrays

    {{ ["this", "is", "an", "array"][0] }}

Arrays are also hash tables just like in PHP:

    {{ ["foo" => "bar", 'oof' => 'rab']['foo'] }}

Printing arrays will cause a PHP notice to be thrown; use the `join` helper:

    {{ [1,2,3] | join(', ') }}

#### Nulls

    {{ null }}

When printed or concatenated, `null` will be converted to an empty string. This
behavior is consistent with the way PHP treats nulls in a string context.

### Operators

In addition to short-circuiting, boolean operators `or` and `and` returns one
of their operands. This means you can, for example, do the following:

    Status: {{ user.status or "default value" }}

Note that the strings `'0'` and `''` are considered to be false. See the section
on branching for more information.

Comparison operators can take multiple operands:

    {% if 1 <= x <= 10 %}
    <p>x is between 1 and 10 inclusive.</p>
    {% endif %}

Which is equivalent to:

    {% if 1 <= x and x <= 10 %}
    <p>x is between 1 and 10 inclusive.</p>
    {% endif %}

The `in` operator works with arrays, iterators and plain objects:

    {% if 1 in [1,2,3] %}
    1 is definitely in 1,2,3
    {% endif %}

    {% if 1 not in [4,5,6] %}
    1 is definitely not in 4,5,6
    {% endif %}

For iterators and plain objects, the `in` operator first converts them using a
simple `(array)` type conversion.

Use `~` (tilde) to concatenate between two or more scalars as strings:

    {{ "Hello," ~ " World!" }}

String concatenation has a lower precedence than arithmetic operators:

    {{ "1 + 1 = " ~ 1 + 1 ~ " and everything is OK again!" }}

Will yield

    1 + 1 = 2 and everything is OK again!

Use `..` (a double dot) to join two or more scalars as string using a single
space character:

    {{ "Welcome," .. user.name }}

String output, concatenations and joins coerce scalar values into strings.

#### Operator Precedence

Below is a list of all operators in Scaffold sorted and listed according to their
precedence in descending order:

- Attribute access: `.` and `[]` for objects and arrays
- Filter chaining: `|`
- Arithmetic: unary `-` and `+`, `%`, `/`, `*`, `-`, `+`
- Concatenation: `..`, `~`
- Comparison: `!==`, `===`, `==`, `!=`, `<>`, `<`, `>`, `>=`, `<=`
- Conditional: `in`, `not`, `and`, `or`, `xor`
- Ternary: `? :`

You can group subexpressions in parentheses to override the precedence rule.

### Attribute Access

#### Objects

You can access an object's member variables or methods using the `.` operator:

    {{ user.name }}

    {{ user.get_full_name() }}

When calling an object's method, the parentheses are optional when there are no
arguments passed. The full semantics of object attribute access are as follows:

For attribute access *without* parentheses, in order of priority:

1. If the attribute is an accessible member variable, return its value.
2. If the object implements `__get`, invoke and return its value.
3. If the attribute is a callable method, call and return its value.
4. If the object implements `__call`, invoke and return its value.
5. Return null.

For attribute access with parentheses, in order of priority:

1. If the attribute is a callable method, call and return its value.
2. If the object implements `__call`, invoke and return its value.
3. Return null.

You can always force a method call by using parentheses.

#### Arrays

You can return an element of an array using either the `.` operator or the `[`
and `]` operator:

    {{ user.name }} is the same as {{ user['name'] }}

    {{ users[0] }}

The `.` operator is more restrictive: only tokens of name type can be used as
the attribute. Tokens of name type begins with an alphabet or an underscore and
can only contain alphanumeric and underscore characters, just like PHP variables
and function names.

One special attribute access rule for arrays is the ability to invoke closure
functions stored in arrays:

    <?php
    $this->view->render('home', [
        'user' => [
            'firstname' => 'Rasmus',
            'lastname'  => 'Lerdorf',
            'fullname'  => function($self) {
                return $self['firstname'] . ' ' .  $self['lastname'];
            },
        ],
    ]);

And call the `fullname` "method" in the template as follows:

    {{ user.fullname }}

When invoked this way, the closure function will implicitly be passed the array
it's in as the first argument. Extra arguments will be passed on to the closure
function as the second and consecutive arguments. This rule lets you have arrays
that behave not unlike objects: they can access other member values or functions
in the array.

#### Dynamic Attribute Access

It's possible to dynamically access an object or array attributes:

    {% assign attr = 'name' %}

    Your name: {{ user[attr] }}

### Helpers

Helpers are simple functions you can use to test or modify values prior to use.
There are two ways you can use them:

- Using helpers as functions
- Using helpers as filters

Except for a few exceptions, they are exchangeable.

#### Using helpers as functions

    {{ upper(title) }}

You can chain helpers just like you can chain function calls in PHP:

    {{ nl2br(capitalize(trim(my_data))) }}

#### Using helpers as filters

Use the `|` character to separate the data with the filter:

    {{ title | capitalize }}

You can use multiple filters by chaining them with the `|` character. Using them
this way is not unlike using pipes in Unix: the output of the previous filter is
the input of the next one. For example, to trim, upper case and convert newlines
to `<br>` tags (in that order), simply write:

    {{ my_data | trim | capitalize | nl2br }}

Some built-in helpers accept additional parameters, delimited by parentheses and
separated by commas, like so:

    {{ "foo " | repeat(3) }}

Which is equivalent to the following:

    {{ repeat("foo ", 3) }}

When using helpers as filters, be careful when mixing operators:

    {{ 12_000 + 5_000 | numberFormat }}

Due to operator precedence, the above example is semantically equivalent to:

    {{ 12_000 + (5_000 | numberFormat) }}

Which, when compiled to PHP, will output 12005 which is probably not what you'd
expect. Either put the addition inside parentheses like so:

    {{ (12_000 + 5_000) | numberFormat }}

Or use the helper as a function:

    {{ numberFormat(12_000 + 5_000) }}

#### Built-in helpers

- `abs` - Absolute value of a number.
- `bytes` - Convert to KB, MB or GB.
- `capitalize` - Uppercase a strings first character.
- `cycle` -
- `date` - Works similar to PHP's date function.
- `dump` - Wrapper for Symfony's dump and die function dd().
- `esc` - Short form of the escape() helper.
    - Parameters
        - `string $obj` - The string to be escaped.
        - `bool $force` - Whether to double encode. Default: false
- `escape` - Escaping for HTML output.
- `first` - Returns the first letter of a string.
- `format` - Return a formatted string. Similar to PHP's sprintf() function.
- `isIterable` - Returns true if iterable, false otherwise.
- `isDivisibleBy` - Checks if object is divisible by a particular number.
- `isEmpty` - Checks if object is empty.
- `isEven` - Checks if scalar is an even number.
- `isOdd` - Checks if scalar is an odd number.
- `join` - Join array elements with a string.
- `jsonEncode` - Returns the JSON representation of a value.
- `keys` - Return all the keys or a subset of the keys of an array.
- `last` - Returns the last letter of a string.
- `length` - Returns the length of a string or count the elements in an iterator.
- `lower` - Converts a string to lower case.
- `nl2br` - Inserts HTML line breaks before all newlines in a string.
- `numberFormat` - Format a number with grouped thousands.
- `repeat` - Repeat a string.
- `replace` - Replace all occurrences of the search string with another string or perform a regular expression search and replace.
- `stripTags` - Strip HTML and PHP tags from a string. Wrapper for PHP's native strip_tags() function.
- `title` - Uppercase the first character of each word in a string.
- `trim` - Strip whitespace (or other characters) from the beginning and end of a string.
- `truncate` - Truncates a string to the given length. It will optionally preserve HTML tags if `$isHtml` is set to true.
- `unescape` - Convert special HTML entities back to characters
- `upper` - Uppercase a string.
- `urlEncode` - URL-encodes string.
- `wordWrap` - Wraps a string to a given number of characters.

#### Registering custom helpers

Registering custom helpers is straightforward:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Infrastructure\Http\Controllers;
    
    use Codefy\Framework\Http\BaseController;
    use Qubus\View\Loader;
    use Qubus\View\Native\Exception\InvalidTemplateNameException;
    use Qubus\View\Native\Exception\ViewException;

    use function Codefy\Framework\Helpers\resource_path;
    use function Qubus\Security\Helpers\die__;
    
    final class HomeController extends BaseController
    {

        public function __construct()
        {
            $helpers = [
                'random' => fn() => 4,
                'exclamation' => fn($s = null) => $s . '!',
            ];

            $this->view = new Loader([
                'source' => [resource_path('views')],
                'target' => resource_path('views/cache'),
                'extension' => '.frm',
                'helpers' => $helpers,
            ]);
        }
        /**
         * @throws ViewException
         * @throws InvalidTemplateNameException
         */
        public function index(): ?string
        {
            $params = [
                'user' => [
                    'data_1' => '<p>This is a paragraph that will probably be escaped if I don\'t intervene.</p>',
                    'data_2' => 'My second data',
                    'first_name' => 'Joshua',
                    'last_name' => 'Parker',
                    'fullname' => fn ($self) => $self['first_name'] . ' ' . $self['last_name']
                ],
            ];
            
            try {
                return $this->view->render('home', compact($params);
            } catch (InvalidTemplateNameException | ViewException $e) {
                die__($e->getMessage());
            }
        }
    }

You can use your custom helpers just like any other built-in helpers:

    A random number: {{ random() }} is truly {{ "bizarre" | exclamation }}

When used as functions, the parentheses are necessary even if your helpers do
not take any parameters. As a rule, when used as a filter, the input is passed
on as the first argument to the helper. It's advisable to have a default value
for every parameter in your custom helper.

Since built-in helpers and custom helpers share the same namespace, you can
override built-in helpers with your own version although it's generally not
recommended.

### Branching

Use the `if` tag to branch. Use the optional `elseif` and `else` tags to have
multiple branches:

    {% if expression_1 %}
        expression 1 is true!
    {% elseif expression_2 %}
        expression 2 is true!
    {% elseif expression_3 %}
        expression 3 is true!
    {% else %}
        nothing matches!
    {% endif %}

Values considered to be false are `false`, `null`, `0`, `'0'`, `''`, and `[]`
(empty array). This behavior is consistent with the way PHP treats data types in
a boolean context. From experience, it's generally useful to have the string
`'0'` be considered a false value: usually the data comes from a relational
database which, in most drivers in PHP, integers in returned tuples are
converted to strings. You can always use the strict `===` and `!==` comparison
operators.

#### Inline `if` and `unless`

Apart from the standalone block tag version, the `if` tag is also available as
a statement modifier. If you know Ruby or Perl, you might find this familiar:

    {{ "this will be printed" if this_evaluates_to_true }}

The above is semantically equivalent to:

    {%- if this_evaluates_to_true -%}
    {{ "this will be printed" }}
    {%- endif -%}

You can use any kind of boolean logic just as in the standard block tag
version:

    {{ "this will be printed" if not this_evaluates_to_false }}

Using the `unless` construct might be more natural for some cases.
The following is equivalent to the above:

    {{ "this will be printed" unless this_evaluates_to_false }}

Inline `if` and `unless` modifiers are available for output tags, break and continue
tags, extends tags, parent tags, set tags, and include tags.

#### Ternary Operator `?:`

You can use the ternary operator if you need branching inside an expression:

    {{ error ? '<p>' ~ error ~ '</p>' :  '<p>success!</p>' }}

The ternary operator has the lowest precedence in an expression.

### Iteration

Use the `for` tag to iterate through each element of an array or iterator. Use
the optional `else` clause to implicitly branch if no iteration occurs:

    {% for link in links %}
        <a href="{{ link.url }}">{{ link.title }}</a> {% else %}
    {% else %}
        There are no links available.
    {% endfor %}

Empty arrays or iterators, and values other than arrays or iterators will branch
to the `else` clause.

You can also iterate as key and value pairs by using a comma:

    {% for key, value in associative_array %}
        <p>{{ key }} = {{ value }}</p>
    {% endfor %}

Both `key` and `value` in the example above are local to the iteration. They
will retain their previous values, if any, once the iteration stops.

The special variable `loop` contains several useful attributes and is available
for use inside the `for` block:

    {% for user in users %}
        {{ user }}{{ ", " unless loop.last }}
    {% endfor %}

If you have an ordinary `loop` variable, its value will temporarily be out of
scope inside the `for` block.

The special `loop` variable has a few attributes:

- `loop.index`: The zero-based index.
- `loop.count`: The one-based index.
- `loop.first`: Evaluates to `true` if the current iteration is the first.
- `loop.last`: Evaluates to `true` if the current iteration is the last.
- `loop.parent`: The parent iteration `loop` object if applicable.

#### Break and Continue

You can use `break` and `continue` to break out of a loop and to skip to the
next iteration, respectively. The following will print "1 2 3":

    {% for i in [0,1,2,3,4,5] %}
        {% continue if i < 1 %}
        {{ i }}
        {% break if i > 2 %}
    {% endfor %}

### Assign

It is sometimes unavoidable to set values to variables and object or array
attributes; use the `assign` construct:

    {% assign fullname = user.firstname .. user.lastname %}

    {% assign user.fullname = fullname %}

You can also use `assign` as a way to buffer output and store the result in a
variable:

    {% assign slogan %}
    <p>This changes everything!</p>
    {% endassign %}
    ...
    {{ slogan }}
    ...

The scope of variables introduced by the `assign` construct is always local to
its surrounding context.

### Blocks

Blocks are at the core of template inheritance:

    {# this is in "parent_template.html" #}
    <p>Hello</p>
    {% block content %}
    <p>Original content</p>
    {% endblock %}
    <p>Goodbye</p>

    {# this is in "child_template.html" #}
    {% extends "parent_template.html" %}
    This will never be displayed!
    {% block content %}
    <p>This will be substituted to the parent template's "content" block</p>
    {% endblock %}
    This will never be displayed!

When `child_template.html` is loaded, it will yield:

    <p>Hello</p>

    <p>This will be substituted to the parent template</p>

    <p>Goodbye</p>

Block inheritance works by replacing all blocks in the parent, or extended
template, with the same blocks found in the child, or extending template, and
using the parent template as the layout template; the child template layout is
discarded. This works recursively upwards until there are no more templates to
be extended. Two blocks in a template cannot have the same name. You can define
blocks within another block, but not within macros.

### Extends

The `extends` construct signals Scaffold:Compiler to load and extend a template. Blocks
defined in the current template will override blocks defined in extended
templates:

    {% extends "path/to/layout.html" %}

The template extension mechanism is fully dynamic with some caveats. You can use
context variables or wrap it in conditionals just like any other statement:

    {% extends layout if some_condition %}

You can also use the ternary operator:

    {% extends some_condition ? custom_layout : "default_layout.html" %}

You cannot however use expressions and variables that are calculated inside the
template before the `extends` tag. This is because the extends tag is the first
thing a template will evaluate regardless of where its position is in the
template. This is also why it's best to put your `extends` tags somewhere at the
top of your templates. For example, the following will not work:

    {% assign extend_template = true %}
    {% extends "parent.html" if extend_template %}

The following will also not work because `tpl` is a value calculated inside the
template before the `extends` tag:

    {% assign tpl = "parent.html" %}
    {% extends tpl %}

If however the `extend_template` or the `tpl` variables are context variables
that already exist before the template loads, then the two examples above will
work as expected.

It is a syntax error to declare more than one `extends` tag per template or to
declare an `extends` tag anywhere but at the top level scope.

#### Parameterized Template Extension

Using the `assign` tag to override a context variable before extending a parent
template will not work. This is because an `extends` tag is the first thing a
template will evaluate regardless of where its position is in the template and
extending a template will discard the current extending template's layout
(i.e., everything outside `block` tags) in favor of the extended template's
layout.

You can however pass an array to override a parent template's context when
extending it. With a parent template:

    {# this is in parent.html #}
    {% if show %}
    TADA!
    {% endif %}

And a child template:

    {# this is in child.html #}
    {% extends "parent.html" with ['show' => true] %}

Rendering the child template will produce:

    TADA!

Likewise, you can't use variables created using the `assign` tag inside the
array parameter used with the `extends` tag. For example, the following will
not work:

    {% assign foo = "BAR" %}
    {% extends "parent.html" with [some_string => foo] %}

### Parent

By using the `parent` tag, you can include the parent block's contents inside
the child block:

    {% block child %}
        {% parent %}
    {% endblock %}

Using the `parent` tag anywhere outside a block or inside a macro is a syntax
error.

### Macros

Macros are a great way to make flexible and reusable partial templates:

    {% macro bolder(text) %}
    <b>{{ text }}</b>
    {% endmacro %}

To call them:

    {% call bolder("this is great!") %}

All parameters are optional; they default to `null` while extra positional
arguments passed are ignored. Scaffold:Compiler lets you define a custom default value for
each parameter:

    {% macro bolder(text="this is a bold text!") %}
    <b>{{ text }}</b>
    {% endmacro %}

You can also use named arguments:

    {% call bolder(text="this is a text") %}

Extra named arguments overwrite positional arguments with the same name and
previous named arguments with the same name. The parentheses are optional only
if there are no arguments passed. Parameters and variables declared inside
macros with the `assign` construct are local to the macro and will cease to
exist once the macro returns.

Macros are dynamically scoped. They inherit the calling context:

    {% macro greet %}
    <p>{{ "Hello," .. name }}</p>
    {% endmacro %}

    {% assign name = "Joe" %}

    {% call greet %}

The above will print:

    <p>Hello Joe</p>

The calling context is masked by the arguments and the default parameter values.

Macros are inherited by extending templates and at the same time overrides other
macros with the same name in parent templates.

Defining macros inside blocks or other macros is a syntax error. Redefining
macros in a template is also a syntax error.

#### Macro Block and Yield

You can call a macro `with` a block and `yield` inside the macro definition:

    {% macro header %}
    <header>{% yield %}</header>
    {% endmacro %}

    {% assign title = "Scaffold:Compiler macro blocks is cool" %}

    {% call header with %}<h1>{{ title or "This is the title" }}</h1>{% endcall %}

The above will result in:

    <header><h1>Scaffold:Compiler macro blocks is cool</h1></header>

It is possible to `yield` multiple times and to also provide context overrides:

    {% macro header %}
    <header>{% yield(title="Scaffold:Compiler") %}</header>
    {% endmacro %}

    {% call header with %}<h1>{{ title }}</h1>{% endcall %}

Which will result in:

    <header><h1>Scaffold:Compiler</h1></header>

#### Importing Macros

It's best to group macros in templates like you would functions in modules or
classes. To use macros defined in another template, simply import them:

    {% import "path/to/form_macros.html" as form %}

All imported macros must be aliased using the `as` keyword. To call an imported
macro, simply prepend the macro name with the alias followed by a dot:

    {% call form.text_input %}

Imported macros are inherited by extending templates and at the same time
overrides other imported macros with the same alias and name pair in parent
templates.

#### Decorating Macros

You can decorate macros by importing them first:

    {# this is in "macro_A.html" #}
    {% macro emphasize(text) %}<b>{{ text }}</b>{% endmacro %}

    {# this is in "macro_B.html" #}
    {% import "macro_A.html" as A %}
    {% macro emphasize(text) %}<i>{% call A.emphasize(text) %}</i>{% endmacro %}

    {# this is in "template_C.html" #}
    {% import "macro_B.html" as B %}
    Emphasized text: {% call B.emphasize("this is pretty cool!") %}

The above when rendered will yield:

    Emphasized text: <i><b>this is pretty cool!</b></i>

### Include

Use the `include` tag to include bits and pieces of templates in your template:

    {% include "path/to/sidebar.html" if page.sidebar %}

This is useful for things like headers, sidebars and footers. Including
non-existing or non-readable templates is a runtime error. Note that there are
no mechanisms to prevent circular inclusion of templates, although there is a
PHP runtime limit on recursion: either the allowed memory allocation size is
reached, thereby producing a fatal runtime error, or the number of maximum
nesting level is reached, if you're using xdebug.

#### Parameterized Template Inclusion

As with template extension, you can pass an array as the overriding context for
the included template:

    {% include "footer.html" with ['year' => current_year] %}

The array parameter will override any variables in the current context but only
for the duration of the include.

### Path Resolution

Paths referenced in `extends`, `include`, and `import` tags can either be
absolute from the specified `source` option when instantiating the loader
object, or relative to the current template's directory.

#### Absolute Paths

Absolute paths must begin with a `/` character like so:

    {% include "/foo/bar.html" %}

In the example above, if the `source` directory is `/var/www/resources/views`, then
the tag will try to include the template `/var/www/resources/views/foo/bar.html`
regardless of what the current template's directory is.

#### Relative Paths

Relative paths must **not** begin with a `/` character:

    {% include "far.html" %}

In this example, if the `source` directory is `/var/www/resources/views`, and the
current template's directory is `boo`, relative to the `source`, then the tag
will try to include the template `/var/www/resources/views/boo/far.html`.

#### Path Injection Prevention

Scaffold:Compiler throws a `RuntimeException` if you try to load any file that is outside the
`source` directory.

### Loading Templates From Other Sources

Sometimes you need to load templates from a database or even string arrays. This
is possible in Scaffold:Compiler by simply passing an object of a class that implements the
`Qubus\View\Adapter\Adapter` interface to the `adapter` option of the `Loader` constructor.

The `Qubus\View\Adapter\Adapter` interface declares five methods:

- `isReadable`: Determines whether the path is readable or not.
- `lastModified`: Returns the last modified time of the path.
- `getContents`: Returns the contents of the given path.
- `putContents`: Puts content in path and returns bytes written.
- `getStreamUrl`: Returns the stream URL.

The `source` option given in the `Loader` constructor still determines if a
template is valid; i.e., whether the template can logically be found in the
source directory.

Below is an example of implementing a Scaffold:Compiler adapter to string arrays:

    <?php
    use Qubus\View\Loader;
    use Qubus\View\Adapter\Adapter;
    
    final class ArrayAdapter implements Adapter
    {
        protected static $templates = [
            'first.html' => 'First! {% include "second.html" %}',
            'second.html' => 'Second!',
        ];
    
        public function isReadable(string $path) : bool
        {
            return isset(self::$templates[$path]);
        }
    
        public function lastModified(string $path) : int
        {
            return filemtime(__FILE__);
        }
    
        public function getContents(string $path) : string
        {
            return self::$templates[$path];
        }
    
        public function putContents(string $path, string $contents) : int
        {
            self::$templates[$path] = $contents;
            return strlen($contents);
        }
    
        public function getStreamUrl(string $path) : string
        {
            /* registering array stream wrapper storage is left as an exercise */
            return 'array://' . $path;
        }
    }
    
    $loader = new Loader([
        'source' => [__DIR__ . '/templates'],
        'target' => __DIR__ . '/cache',
        'mode' => Loader::RECOMPILE_ALWAYS,
        'adapter' => new ArrayAdapter(),
    ]);
    
    try {
        $loader->render('home');
    } catch (Exception $e) {
        // something went wrong!
        die__($e->getMessage());
    }

The above will compile the templates and render the following:

```
First! Second!
```

### Controlling whitespace

When you're writing a template for a certain file format that is sensitive
to whitespace, you can use `{%-` and `-%}` in place of the normal opening and
closing block tags to suppress whitespaces before and after the block tags,
respectively. You can use either one or both at the same time depending on
your needs. The `{{-` and `-}}` delimiters  are also available for expression
output tags, while the `{#-` and `-#}` delimiters are available for comment
tags.

The following is a demonstration of whitespace control:

    <ul>
        {%- for user in ["Alice", "Bob", "Charlie"] -%}
        <li>{{ user }}</li>
        {%- endfor -%}
    </ul>

Which will yield a compact

    <ul>
        <li>Alice</li>
        <li>Bob</li>
        <li>Charlie</li>
    </ul>

While the same example, this time without any white-space control:

    <ul>
        {% for user in ["Alice", "Bob", "Charlie"] %}
        <li>{{ user }}</li>
        {% endfor %}
    </ul>

Will yield the rather sparse

    <ul>
        
        <li>Alice</li>
        
        <li>Bob</li>
        
        <li>Charlie</li>
        
    </ul>

The semantics are as follows:

- `{%-`, `{{-`, and `{#-` delimiters will remove all whitespace to their left
  **up to but not including** the first newline it encounters.

- `-%}`, `-}}`, and `-#}` delimiters will remove all whitespace to their right
  **up to and including** the first newline it encounters.

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.