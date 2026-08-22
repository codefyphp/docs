---
title: Compiler
sidebar_title: Compiler
summary: Build secure CodefyPHP templates with the Qubus compiler engine, automatic HTML escaping, layouts, directives, expressions, functions, and caching.
keywords: php-template-engine,template-compiler,html-escaping
weight: 2
---

Scaffold Compiler turns a purpose-built template language into cached PHP classes. It provides automatic HTML
escaping, expressions, helpers and filters, branching, iteration, assignments, inheritance, blocks, includes, macros,
imports, callable blocks, path containment, source adapters, and Alpine.js builders.

Choose Compiler when template authors should use a constrained presentation language instead of PHP. Choose the
[Native engine](native.md) when templates should be ordinary PHP files and do not need compilation.

## Quick start

Create source and cache directories:

```text
resources/views/
└── home.html
storage/views/
```

Configure a loader and return rendered output:

```php
<?php

declare(strict_types=1);

use Qubus\View\Loader;

require __DIR__ . '/vendor/autoload.php';

$view = new Loader([
    'source' => __DIR__ . '/resources/views',
    'target' => __DIR__ . '/storage/views',
    'mode' => Loader::RECOMPILE_NORMAL,
    'exception_handler' => false,
]);

$html = $view->fetch('home', [
    'title' => 'Dashboard',
    'user' => $currentUser,
]);

echo $html;
```

```html
{# resources/views/home.html #}
<!doctype html>
<html lang="en">
<head>
    <title>{{ title }}</title>
</head>
<body>
    <h1>{{ "Welcome," .. user.name }}</h1>
</body>
</html>
```

`{{ ... }}` escapes its result for HTML. The names `home` and `home.html` both resolve with the configured extension.
Nested templates can be addressed as `pages/home` or `pages.home`.

## Loader configuration

`Qubus\View\Loader` takes an options array. `source` and `target` are required.

```php
$view = new Loader([
    'source' => [
        __DIR__ . '/resources/views',
        __DIR__ . '/packages/blog/views',
    ],
    'target' => __DIR__ . '/storage/compiled-views',
    'extension' => 'html',
    'mode' => Loader::RECOMPILE_NORMAL,
    'mkdir' => 0775,
    'helpers' => [
        'money' => static fn (float $amount): string => '$' . number_format($amount, 2),
    ],
    'exception_handler' => false,
]);
```

| Option | Default | Description |
| --- | --- | --- |
| `source` | required | Source directory, non-empty array of source directories, or a `Closure` returning either form. |
| `target` | required | Directory for generated PHP classes. |
| `extension` | `'.html'` | Template extension, with or without a leading dot. It must not contain path separators. |
| `mode` | `RECOMPILE_NORMAL` | Controls when source is recompiled. |
| `mkdir` | `0777` | Recursive mode used to create a missing target directory; use `false` to prohibit creation. |
| `helpers` | `[]` | Map of helper name to callable. Custom helpers replace built-ins with the same name. |
| `adapter` | `FileAdapter` | Object implementing `Qubus\View\Adapter\Adapter` for non-filesystem sources. |
| `exception_handler` | `true` | When true, syntax errors render Scaffold's debug page and terminate; when false, they are thrown. |

For reusable libraries, workers, APIs, tests, and production exception middleware, set `exception_handler` to `false`
and handle `SyntaxErrorException` at the application boundary. The default `true` behavior exists for the legacy
browser debug page and calls `die()` after rendering it.

### Recompilation modes

| Constant | Behavior |
| --- | --- |
| `Loader::RECOMPILE_NEVER` | Compile only when the generated class file does not exist. |
| `Loader::RECOMPILE_NORMAL` | Compile when missing or older than the source. Recommended for most deployments. |
| `Loader::RECOMPILE_ALWAYS` | Compile whenever an uncached template is loaded or `compile()` is explicitly called. Useful in development. |

Loaded template objects are cached inside each `Loader` instance. Re-rendering the same template through the same
loader uses that instance. Because a generated PHP class cannot be redeclared in the same process, recompiling an
already loaded template takes effect in a new PHP process; use a fresh process when testing recompilation behavior.

### Source order and target permissions

With multiple filesystem sources, the first readable matching template wins. Source directories must exist when the
default `FileAdapter` is created. The target must be writable by the PHP process. Generated files are written through a
temporary file and atomically renamed into place to prevent readers from observing partially generated PHP.

## Rendering API

The loader offers output-oriented legacy methods and string-returning methods.

### Return a string

```php
$html = $view->fetch('pages.profile', ['user' => $user]);

$fragment = $view->fetchString(
    '<strong>{{ label }}</strong>',
    ['label' => 'Saved'],
);
```

- `fetch(template, data)` loads the template, captures its output, and returns a string.
- `fetchString(source, data)` compiles a source string, captures it, and returns a string.
- Output buffers opened by `fetch()` are cleaned if rendering throws.

### Send output directly

```php
$view->render('pages.profile', ['user' => $user]);
$view->renderString('<p>{{ message }}</p>', ['message' => 'Hello']);
```

- `render()` returns `void` and writes template output directly.
- `renderString()` also renders directly; use `fetchString()` when a returned string is required.

### Load or compile explicitly

```php
$template = $view->load('pages.profile');
$html = $template->render(['user' => $user]);

$view->compile('pages.profile');
$view->compile('pages.profile', Loader::RECOMPILE_ALWAYS);

$inlineTemplate = $view->loadFromString('<p>{{ message }}</p>');
```

`load()` accepts a template name or an existing `Qubus\View\Template`. `compile()` returns the loader for chaining.

### Utility methods

```php
if ($view->exists('optional.banner')) {
    echo $view->fetch('optional.banner');
}

$logicalPath = $view->resolvePath('pages.profile');
$parts = $view->normalizePath('pages/../shared/card');
$version = $view->getVersion();

$view->setExceptionHandler(false);
```

`exists()` converts path-related `RuntimeException` failures to `false`. `resolvePath()` returns the normalized logical
path used by the adapter, not necessarily an absolute filesystem path.

## Language overview

Compiler templates use four delimiter families. Identifiers and keywords are case-sensitive.

| Syntax | Purpose |
| --- | --- |
| `{{ expression }}` | Evaluate, HTML-escape, and output an expression. |
| `{! expression !}` | Evaluate and output without escaping. |
| `{% statement %}` | Control flow, assignment, inheritance, includes, blocks, or macros. |
| `{# comment #}` | Remove a comment from output. |

```html
{# A comment #}
{% if user %}
    <p>{{ user.name }}</p>
{% endif %}
```

Comments can span lines, cannot nest, and must be closed.

## Output and escaping

### Escaped output

```html
<h1>{{ title }}</h1>
<input value="{{ value }}">
```

Normal output calls the built-in `escape` helper. It uses UTF-8 `htmlspecialchars()` with quote escaping and does not
double-encode existing entities by default.

Automatic HTML escaping only addresses HTML text and ordinary quoted attributes. Validate URL schemes in application
code, do not place untrusted values in CSS or JavaScript contexts, and prefer safe DOM APIs for client-side behavior.

### Raw output

```html
{! trustedHtml !}
```

Raw output performs no escaping or sanitization. Use it only with application-generated markup or appropriately
sanitized rich text. A normal helper that returns a string is still escaped by `{{ ... }}`.

`Qubus\View\HtmlString` marks HTML already safely constructed. Scaffold's Alpine helpers return `HtmlString`, so these
can use normal output without becoming escaped text:

```html
<div {{ alpineData(["open" => false]) }}></div>
```

Custom helpers should return `HtmlString` only when they fully validate and escape every value used to construct HTML.

## Literals

### Numbers

```html
{{ 42 }}
{{ 3.14 }}
{{ -10 }}
{{ 12_000 + 5_000 }}
```

Underscores inside numbers are removed. Values compile to PHP integers or floats and therefore use PHP's range and
precision rules.

### Strings

Single- and double-quoted strings support backslash escape sequences. They do not interpolate variables.

```html
{{ "Hello, " ~ user.name }}
{{ 'It\'s ready' }}
```

### Booleans and null

```html
{{ true }}
{{ false }}
{{ null }}
```

In output, `true` becomes `1`; `false` and `null` become an empty string, following PHP string conversion.

### Arrays and maps

```html
{{ ["red", "green", "blue"][0] }}
{{ ["role" => "admin", "active" => true]["role"] }}
{{ [1, 2, 3,] | join(", ") }}
```

String, number, and bare-name entries can be keys. A trailing comma is allowed. Printing an array directly is not
meaningful; use `join`, access an element, or encode it. In array literals, a bare name without `=>` is treated as a
string literal. Parenthesize a variable expression when it must be evaluated as an unkeyed array value.

```html
{{ [(user), (account)] | length }}
```

## Variables and attribute access

Missing variables evaluate to `null`.

### Arrays

```html
{{ user.name }}
{{ user["name"] }}
{{ users[0].email }}
```

For arrays, dot and bracket lookup return the value when the key is set, otherwise `null`. Dot attributes must be valid
template names; bracket expressions can be dynamic.

Array entries containing closures behave like methods:

```php
$data = [
    'user' => [
        'firstName' => 'Ada',
        'lastName' => 'Lovelace',
        'fullName' => static function (array $self, string $separator = ' '): string {
            return $self['firstName'] . $separator . $self['lastName'];
        },
    ],
];
```

```html
{{ user.fullName }}
{{ user.fullName(" / ") }}
```

The containing array is supplied as the closure's first argument. Explicit arguments follow it.

### Objects

```html
{{ user.name }}
{{ user.displayName() }}
{{ user.formatName("last-first") }}
```

Without parentheses, resolution checks an accessible public property, then `__get`, then a callable method (including
`__call`). A no-argument method may therefore omit parentheses. With parentheses, Scaffold attempts a callable method
with the supplied arguments. Missing attributes evaluate to `null`.

Only expose view-safe objects to templates. Template attribute access can invoke public methods; do not pass powerful
service objects, database connections, or mutable infrastructure into an untrusted template.

### Dynamic access

```html
{% assign field = "displayName" %}
{{ user[field] }}
```

## Expressions and operators

```html
{{ price * quantity }}
{{ total >= 100 ? "free shipping" : "standard shipping" }}
{{ status or "unknown" }}
```

### Arithmetic

Supported arithmetic operators are unary `+` and `-`, multiplication `*`, division `/`, modulo `%`, addition `+`, and
subtraction `-`. Multiplicative and additive operators are left-associative. `%` compiles through PHP `fmod()`.

### Strings

- `~` concatenates values without adding a separator.
- `..` joins values with one literal space between them.

```html
{{ firstName ~ lastName }}
{{ "Welcome," .. user.name }}
```

### Comparisons and membership

Supported comparisons are `!==`, `===`, `==`, `!=`, `<>`, `<`, `>`, `>=`, and `<=`.

```html
{% if 1 <= page <= pageCount %}
    Current page is in range.
{% endif %}
```

Chained comparisons evaluate each adjacent pair. Membership casts the right operand to an array and uses PHP
`in_array()`:

```html
{% if role in ["admin", "editor"] %}...{% endif %}
{% if status not in ["disabled", "deleted"] %}...{% endif %}
```

Membership is non-strict because the generated `in_array()` call does not enable strict comparison.

### Boolean operators

`not`, `and`, `or`, and `xor` are supported. `and` and `or` short-circuit and return an operand, enabling defaults:

```html
{{ user.nickname or user.name or "Anonymous" }}
```

PHP-false values include `false`, `null`, `0`, `"0"`, `""`, and an empty array.

### Ternary expressions

```html
{{ error ? "Error: " ~ error : "Ready" }}
```

The ternary operator requires all three expressions: `condition ? whenTrue : whenFalse`.

### Precedence

From highest to lowest:

1. Parentheses, literals, variables, function calls, attribute access, and filter chaining.
2. Unary `+` and `-`.
3. `*`, `/`, `%`.
4. `+`, `-`.
5. Space join `..`.
6. Concatenation `~`.
7. Comparisons.
8. Membership with `in` and `not in`.
9. Prefix `not`.
10. `and`.
11. `or`.
12. `xor`.
13. Ternary `? :`.

Use parentheses whenever mixed operators could be ambiguous.

## Helpers and filters

Helpers can be called as functions or applied as filters.

```html
{{ upper(title) }}
{{ title | upper }}
{{ description | trim | capitalize }}
{{ numberFormat(subtotal + tax, 2) }}
```

For a filter, the value on the left becomes the helper's first argument:

```html
{{ "ha" | repeat(3) }}
{# equivalent to repeat("ha", 3) #}
```

Filters bind tightly. Parenthesize a larger expression before filtering it:

```html
{{ (12_000 + 5_000) | numberFormat }}
```

### Registering custom helpers

```php
$view = new Loader([
    'source' => __DIR__ . '/resources/views',
    'target' => __DIR__ . '/storage/compiled-views',
    'helpers' => [
        'money' => static fn (float $value, string $currency = 'USD'): string => sprintf(
            '%s %.2f',
            $currency,
            $value,
        ),
        'exclaim' => static fn (mixed $value = null): string => (string) $value . '!',
    ],
]);
```

```html
{{ money(order.total, "EUR") }}
{{ "Saved" | exclaim }}
```

Function syntax always requires parentheses. Custom helpers take precedence over built-in helpers with the same name.
Exceptions and errors from helpers are wrapped in a `RuntimeException` with template and line context; the original is
available through `getPrevious()`.

### Built-in value helpers

| Helper | Description |
| --- | --- |
| `abs(value = null)` | Integer-casts and returns the absolute value. |
| `bytes(value = null, decimals = 1, decimalPoint = '.', thousandsSeparator = ',')` | Formats a non-negative byte count as bytes, KB, MB, or GB. |
| `capitalize(value)` | Uppercases the first character. |
| `date(timestamp = null, format = 'Y-m-d')` | Formats a timestamp; `null` means the current time and `0` means the Unix epoch. |
| `first(value = null, default = null)` | First character or first iterable/object value. |
| `format(format, value, ...)` | Calls `sprintf()` with all arguments. Supply at least one format argument value. |
| `isIterable(value = null)` | True for arrays and `Traversable` objects. |
| `isDivisibleBy(value = null, number = null)` | Numeric divisibility test; zero divisors return false. |
| `isEmpty(value = null)` | Tests null, strings, arrays, `Countable`, and `Traversable` values. A non-countable iterator is consumed. |
| `isEven(value = null)`, `isOdd(value = null)` | Tests numbers or the length/count of strings and collections. |
| `join(value = null, glue = '')` | Joins arrays or traversables. |
| `jsonEncode(value = null)` | Calls PHP `json_encode()`. Normal output HTML-escapes the returned JSON. |
| `keys(value = null)` | Returns array or traversable keys, otherwise null. |
| `last(value = null, default = null)` | Last character or last iterable/object value. |
| `length(value = null)` | String length, collection count, traversable count, or `1` for other values. |
| `lower(value = null)`, `upper(value = null)` | Lowercase or uppercase string conversion. |
| `numberFormat(value = null, decimals = 0, decimalPoint = '.', thousandsSeparator = ',')` | Calls `number_format()`. |
| `repeat(value, times = 2)` | Repeats a string. |
| `replace(value = null, search = '', replacement = '', regex = false)` | Literal replacement or `preg_replace()` when `regex` is true. |
| `stripTags(value = null, allowableTags = '')` | Calls PHP `strip_tags()`. |
| `title(value = null)` | Calls `ucwords()`. |
| `trim(value = null, charlist = PHP whitespace)` | Trims the beginning and end. |
| `truncate(value = null, limit = 255, continuation = '&hellip;', isHtml = false)` | Truncates text, optionally preserving HTML structure. |
| `urlEncode(value = null)` | Calls `urlencode()`. |
| `wordWrap(value = null, width = 75, break = "\n", cut = false)` | Calls `wordwrap()`. |

### Escaping and HTML-producing helpers

| Helper | Description |
| --- | --- |
| `esc(value = null, force = false)`, `escape(...)` | HTML escape with quote escaping; `force` controls double encoding. |
| `unescape(value = null)` | Decode HTML entities. Do not use with untrusted content. |
| `nl2br(value = null, isXhtml = false)` | Inserts `<br>` markup; use raw output only when the input has already been escaped appropriately. |
| `imageTag(url, options = [])` | Builds an image tag; options: `id`, `class`, `title`, `style`, `alt`, `width`, `height`, `border`. |
| `cssTag(url, options = [])` | Builds a stylesheet tag; options also include `media`. |
| `scriptTag(url, options = [])` | Builds a script tag; supports `async`, `crossorigin`, `defer`, `integrity`, `nonce`, `referrerpolicy`, and `type`. |

The tag helpers return strings, not `HtmlString`, so intentionally render them with raw output:

```html
{! cssTag("/assets/app.css", ["media" => "screen"]) !}
{! scriptTag("/assets/app.js", ["defer" => true]) !}
```

Asset URLs reject executable schemes. Relative, HTTP, and HTTPS URLs are accepted; `imageTag` additionally permits
base64 AVIF, GIF, JPEG, PNG, and WebP data images. Option values are HTML-escaped.

`dump(value)` delegates to the environment's `dd()` helper and terminates execution. It is intended only for debugging.

### Collection helpers

`cycle(values)` returns a `Cycler`. The input must contain at least one value:

```html
{% assign rowClasses = cycle(["odd", "even"]) %}
{% for user in users %}
    <div class="{{ rowClasses.next }}">{{ user.name }}</div>
{% endfor %}
```

The cycler exposes `next`, `random(seed = null)`, `count`, and `cycle` through normal object method access.

`range(lower, upper, step = 1)` returns an inclusive ascending or descending iterator. Step cannot be zero:

```html
{% for page in range(1, pageCount) %}
    <a href="?page={{ page }}">{{ page }}</a>
{% endfor %}

{% for value in range(10, 2, 2) %}
    {{ value }}
{% endfor %}
```

The range object also exposes `length`, `count`, `includes(value)`, and `random(seed = null)`. `includes()` tests the
numeric bounds; it does not test whether a value falls exactly on a configured step.

## Branching

```html
{% if user.isAdmin %}
    <p>Administrator</p>
{% elseif user %}
    <p>Member</p>
{% else %}
    <p>Guest</p>
{% endif %}
```

### Inline `if` and `unless`

Output and selected statements support modifiers:

```html
{{ "Published" if post.published }}
{{ "Draft" unless post.published }}

{% include "partials/admin" if user.isAdmin %}
{% continue if item.hidden %}
{% break if loop.count >= limit %}
```

Modifiers are supported on escaped output, raw output, `break`, `continue`, `extends`, expression-form `assign`,
`parent`, and `include`.

## Iteration

```html
{% for user in users %}
    <p>{{ user.name }}</p>
{% else %}
    <p>No users found.</p>
{% endfor %}
```

Arrays and `Traversable` objects are supported. Non-iterable and empty values execute the optional `else` body.
Non-countable iterators and generators are buffered so loop length and `loop.last` remain available.

Key/value form:

```html
{% for id, user in usersById %}
    <p>{{ id }}: {{ user.name }}</p>
{% endfor %}
```

The loop variable and iteration variables temporarily shadow values of the same names and are restored afterward. If
they did not previously exist, they are removed from the context.

### Loop metadata

| Attribute | Meaning |
| --- | --- |
| `loop.index` | Zero-based index. |
| `loop.count` | One-based iteration count. |
| `loop.first` | True on the first item. |
| `loop.last` | True on the last item. |
| `loop.length` | Total item count. |
| `loop.parent` | Outer loop metadata, or the previous `loop` context value. |

```html
{% for category in categories %}
    {% for item in category.items %}
        {{ loop.parent.count }}.{{ loop.count }} {{ item.name }}
    {% endfor %}
{% endfor %}
```

### Break and continue

```html
{% for value in values %}
    {% continue if value.hidden %}
    {{ value.name }}
    {% break if loop.count >= 10 %}
{% endfor %}
```

Using either statement outside a `for` body is a syntax error.

## Assignment

Assign an expression to a context variable or nested array/object attribute:

```html
{% assign fullName = user.firstName .. user.lastName %}
{% assign user.displayName = fullName %}
{% assign settings[activeKey] = true %}
```

Capture rendered output:

```html
{% assign message %}
    <strong>{{ title }}</strong>
{% endassign %}

{! message !}
```

Captured content is a normal string. Use escaped output to display it literally or raw output only when all values used
to create it were safely escaped.

An expression assignment can use an inline modifier:

```html
{% assign badge = "new" if item.isNew %}
```

## Template inheritance and blocks

Parent layout:

```html
{# layouts/main.html #}
<!doctype html>
<html>
<head>
    <title>{% block title "Default title" %}</title>
</head>
<body>
    {% block content %}{% endblock %}
</body>
</html>
```

Child template:

```html
{% extends "/layouts/main" %}

{% block title %}{{ pageTitle }}{% endblock title %}

{% block content %}
    <h1>{{ pageTitle }}</h1>
{% endblock content %}
```

Block names are unique within a template. The optional name after `endblock` must match. A compact block can contain a
single escaped expression:

```html
{% block title pageTitle %}
```

Child blocks replace parent blocks. Blocks and macros from deeper children take precedence as the inheritance chain is
rendered. Content outside blocks in a child is discarded when its parent is displayed.

### Extends

These are separate alternatives; a template may contain only one of them:

```html
{% extends layout %}
{% extends "/layouts/admin" if user.isAdmin %}
{% extends compact ? "/layouts/compact" : "/layouts/main" %}
```

Only one `extends` declaration is allowed, and it must be at top-level rather than inside a block or macro. The compiler
evaluates it before the template body regardless of where it appears in the source, so it cannot depend on a variable
created earlier by `assign`. Pass such values in render data instead.

Parameterized inheritance gives values to the parent, with the supplied array taking precedence:

```html
{% extends "/layouts/main" with [
    "theme" => "dark",
    "showNavigation" => true,
] %}
```

### Parent block content

```html
{% block content %}
    {% parent %}
    <p>Child content after the parent block.</p>
{% endblock %}
```

`parent` is valid only inside a block and cannot be used inside a macro. It supports inline `if` and `unless`.

### Circular references

The runtime rejects circular include and inheritance chains with `RuntimeException`. The display guard is reset in a
`finally` block, so a failed render does not permanently poison the cached template object.

## Includes and path resolution

```html
{% include "partials/card" %}
{% include "partials/card" with ["item" => featuredItem, "compact" => true] %}
{% include "partials/sidebar" if page.showSidebar %}
```

Include parameters replace matching current-context values only for the included template.

### Relative and source-root paths

A reference without a leading slash is relative to the current template directory:

```html
{# pages/account.html -> pages/partials/menu.html #}
{% include "partials/menu" %}
```

A reference beginning with `/` is resolved from the configured source root:

```html
{% include "/shared/footer" %}
```

The same rules apply to `extends` and `import`.

Loader calls also accept slash paths or dot notation:

```php
$view->fetch('pages/account');
$view->fetch('pages.account');
```

Known template suffixes are removed before the configured extension is added. Dot notation converts dots in the
logical template name to directory separators, so use slash notation when a name could otherwise be ambiguous.

### Path security

Filesystem paths are normalized and null bytes are rejected. Attempts to traverse above a source root fail. With the
default `FileAdapter`, the canonical resolved file must stay under one of the configured source directories; symbolic
links cannot be used to escape it. Include, extend, and import failures are wrapped with the calling template and source
line.

## Macros

Macros are reusable template functions that render output.

```html
{% macro badge(text, kind="info") %}
    <span class="badge badge-{{ kind }}">{{ text }}</span>
{% endmacro badge %}

{% call badge("Saved", "success") %}
{% call badge(text="Draft", kind="warning") %}
```

Macro parameters are optional and default to `null` unless a literal default is declared. Defaults must be literal
values. Positional and named arguments are supported; named values take precedence. Macros inherit the calling context,
while parameters and assignments inside the macro remain local to that call.

Macros cannot be declared inside blocks or other macros, and a name cannot be declared twice in one template.

### Caller blocks and yield

```html
{% macro panel(title="Panel") %}
    <section class="panel">
        <h2>{{ title }}</h2>
        {% yield %}
    </section>
{% endmacro %}

{% call panel("Account") with %}
    <p>{{ user.name }}</p>
{% endcall %}
```

The caller block inherits its call-site context. `yield` can override values:

```html
{% macro repeatCard %}
    {% yield(position=1) %}
    {% yield(position=2) %}
{% endmacro %}
```

Only use `yield` in a macro that is invoked with a caller block; otherwise there is no callable block to execute.

### Importing macros

```html
{# macros/forms.html #}
{% macro input(name, value="") %}
    <input name="{{ name }}" value="{{ value }}">
{% endmacro %}
```

```html
{% import "/macros/forms" as forms %}
{% call forms.input("email", user.email) %}
```

Imports require an alias. Use a literal template path for predictable constructor-time loading. Imported macros are
available by `alias.macro`; child imports and macros take precedence through inheritance.

## Whitespace control

Add `-` to either side of any delimiter family:

```html
<ul>
    {%- for user in users -%}
    <li>{{- user.name -}}</li>
    {%- endfor -%}
</ul>
```

Supported trimmed forms are:

- `{%-` and `-%}` for statements;
- `{{-` and `-}}` for escaped output;
- `{!-` and `-!}` for raw output;
- `{#-` and `-#}` for comments.

An opening trim marker removes spaces and tabs immediately to its left, stopping before a newline. A closing trim
marker removes spaces and tabs to its right and may consume the immediately following newline.

## Alpine.js integration

Scaffold builds safe Alpine attributes and server-provided state without choosing an Alpine version, CDN, or bundling
strategy for your application.

### State and directives

```html
<div
    {{ alpineData([
        "open" => false,
        "label" => menuLabel,
    ]) }}
    {{ alpine([
        "on:click.outside" => "open = false",
        "show" => "open",
        "transition.opacity" => null,
        "cloak" => null,
    ]) }}
>
    <button {{ alpine(["on:click" => "open = ! open"]) }}>
        {{ menuLabel }}
    </button>
</div>
```

These helpers return `HtmlString`, so use ordinary `{{ ... }}` output. State is JSON-encoded with script-safe flags and
attribute-escaped. An empty state creates `x-data="{}"`.

`alpine()` supports shorthand aliases, `on:event`, `bind:attribute`, full `x-*`, `@event`, and `:attribute` names, and
Alpine modifiers. A `null` value creates a valueless directive. Arrays, objects, and `JsonSerializable` values become
JSON expressions. Directive names are validated, but expression strings are executable JavaScript and must not come
from untrusted users.

### Reusable Alpine.data components

```html
<section {{ alpineComponent("dropdown", [(true), (menuLabel)]) }}>
    ...
</section>
```

List arguments become positional arguments. The parentheses are needed because an unkeyed bare name in a compiler
array is a string literal. A keyed array becomes one object argument:

```html
{{ alpineComponent("profileCard", [
    "userId" => user.id,
    "compact" => true,
]) }}
```

With no arguments, `alpineComponent("dropdown")` renders `x-data="dropdown"`; supply an argument list when the
provider must be invoked as a function.

### Stores, script tags, and x-cloak

```html
{{ alpineStore("session", sessionState, cspNonce) }}
{{ alpineScript("/assets/alpine.js", cspNonce, [
    "integrity" => alpineIntegrity,
    "crossorigin" => "anonymous",
]) }}
{{ alpineCloakStyle(cspNonce) }}
```

- `alpineStore` registers JSON state during `alpine:init`.
- `alpineScript` accepts relative, HTTP, or HTTPS URLs and adds `defer` by default.
- Script options are `async`, `crossorigin`, `defer`, `integrity`, `referrerpolicy`, and `type`.
- Set `"defer" => false` to remove the default.
- `alpineCloakStyle` emits the standard hide rule.
- Store and style output accept optional CSP nonces.

Use Alpine's CSP-compatible build when your policy forbids dynamic function evaluation. Scaffold only constructs HTML;
your frontend must load Alpine and any plugins.

The same builders can be called in PHP through `Qubus\View\Alpine`:

```php
use Qubus\View\Alpine;

$directives = Alpine::attributes(['show' => 'open']);
$state = Alpine::data(['open' => false]);
$component = Alpine::component('dropdown', [true]);
$store = Alpine::store('session', ['userId' => 42], $cspNonce);
$script = Alpine::script('/assets/alpine.js', $cspNonce);
$cloak = Alpine::cloakStyle($cspNonce);
```

Every builder returns `Qubus\View\HtmlString`, a stringable marker for HTML already constructed and escaped by the
library.

## Custom source adapters

Implement `Qubus\View\Adapter\Adapter` to load logical templates from a database, object storage, an in-memory map, or
another source:

```php
<?php

declare(strict_types=1);

use Qubus\View\Adapter\Adapter;
use Qubus\View\Loader;

final class ArrayAdapter implements Adapter
{
    public function __construct(private array $templates)
    {
    }

    public function isReadable(string $path): bool
    {
        return array_key_exists($path, $this->templates);
    }

    public function lastModified(string $path): int
    {
        return 1;
    }

    public function getContents(string $path): string
    {
        return $this->templates[$path];
    }

    public function putContents(string $path, string $contents): int|bool
    {
        $this->templates[$path] = $contents;
        return strlen($contents);
    }

    public function getStreamUrl(string $path): string
    {
        return 'array://' . $path;
    }
}

$view = new Loader([
    'source' => ['virtual'],
    'target' => __DIR__ . '/storage/compiled-views',
    'adapter' => new ArrayAdapter([
        'home.html' => 'Home {% include "partials/message" %}',
        'partials/message.html' => '{{ message }}',
    ]),
    'mode' => Loader::RECOMPILE_ALWAYS,
    'exception_handler' => false,
]);

echo $view->fetch('home', ['message' => 'Hello']);
```

The five interface methods are:

| Method | Contract |
| --- | --- |
| `isReadable(path): bool` | Report whether a normalized logical template can be loaded. |
| `lastModified(path): int` | Return a comparable modification timestamp for normal recompilation mode. |
| `getContents(path): string` | Return template source. |
| `putContents(path, contents): int\|bool` | Store content and return bytes written or false. Required by the interface. |
| `getStreamUrl(path): string` | Return a backing stream URL or diagnostic representation. |

Compiled PHP is always written to `target` through `FileAdapter`; the source adapter is not used as the compiled cache.
For non-filesystem adapters, `isReadable()` defines logical path availability. The adapter is responsible for its own
authorization, tenant isolation, and key containment.

## Errors and security

### Syntax errors

With `exception_handler => false`, malformed templates throw `Qubus\View\SyntaxErrorException`. The exception includes
the token, line, character, and template file when available.

```php
use Qubus\View\SyntaxErrorException;

try {
    $html = $view->fetch('pages/home', $data);
} catch (SyntaxErrorException $exception) {
    $logger->error($exception->getMessage(), ['exception' => $exception]);
    throw $exception;
}
```

With the default handler enabled, the engine renders a source-code debug page and terminates. Do not expose that debug
page in production.

### Runtime errors

`RuntimeException` covers missing templates, unreadable files, path escapes, compiled-file write failures, recursive
references, inaccessible assignments, undefined helpers, and contextual include/extend/import failures.
`InvalidArgumentException` covers invalid loader configuration, zero range steps, empty cyclers, unsafe asset URLs, and
invalid Alpine arguments. `Qubus\Exception\Data\TypeException` is used by legacy mixed-typed loading methods when a
string was expected.

### Template trust model

- Normal output is HTML-escaped; raw output is an explicit trust boundary.
- Template files themselves are trusted application code because they can invoke registered helpers and public methods
  on objects supplied in the context.
- Pass view models or simple data structures rather than infrastructure services.
- Custom helpers and adapters are trusted extension points.
- Filesystem templates are canonicalized beneath configured source roots, including symbolic-link checks.
- Generated PHP should be stored outside the public web root and not served as source.
- Do not let users control template names, Alpine expressions, helper registration, source roots, or the compile target
  without an application-level allowlist.

## Public API summary

```php
new Loader(array $options)

$view->compile(string $template, ?int $mode = null): Loader
$view->load(string|Template $template, string $from = ''): Template
$view->loadFromString(string $template): Template
$view->render(string|Template $template, array $data = []): void
$view->renderString(string $source, array $data = []): mixed
$view->fetch(string|Template $template, array $data = []): string
$view->fetchString(string $source, array $data = []): string
$view->exists(string $template, string $from = ''): bool
$view->resolvePath(string $template, string $from = ''): string
$view->normalizePath(string $path): array
$view->getVersion(): string
$view->setExceptionHandler(bool $enabled = true): Loader
```

## Recommended project structure

```text
resources/views/
├── components/
├── layouts/
│   └── main.html
├── macros/
│   └── forms.html
├── pages/
├── partials/
└── shared/
storage/compiled-views/
```

Keep `storage/compiled-views` writable but outside the public document root. Commit source templates, not generated PHP.
