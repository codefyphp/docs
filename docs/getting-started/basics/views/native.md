---
title: Native
sidebar_title: Native
summary: Render native PHP templates with Qubus View using namespaced loaders, layouts, blocks, globals, registered functions, pipelines, and output escaping.
keywords: native-php-templates,qubus-view,template-layouts
weight: 1
---

Scaffold Native renders ordinary PHP files without compiling them. It adds namespaced template lookup, layouts,
blocks, partials, components, slots, named content stacks, shared globals, registered functions, contextual escaping,
and Alpine.js builders while leaving PHP itself as the template language.

Choose Native when your team wants normal PHP syntax, IDE support inside templates, and no compiled-template cache.
Choose the [Compiler engine](compiler.md) when you want a restricted, purpose-built template language with automatic
HTML escaping.

## Quick start

Create a template directory:

```text
templates/
├── layouts/
│   └── main.phtml
└── pages/
    └── home.phtml
```

Create the engine and render a namespaced template:

```php
<?php

declare(strict_types=1);

use Qubus\View\Native\NativeLoader;

require __DIR__ . '/vendor/autoload.php';

$view = new NativeLoader([
    'app' => __DIR__ . '/templates',
]);

echo $view->render('app::pages/home', [
    'title' => 'Dashboard',
    'user' => $currentUser,
]);
```

Template names follow `namespace::path` and omit the extension. With the default `phtml` extension,
`app::pages/home` resolves to `templates/pages/home.phtml`.

```php
<!-- templates/pages/home.phtml -->
<?php $this->parent('app::layouts/main'); ?>

<?php $this->block('content', function (array $params): void { ?>
    <h1><?=$this->esc($params['title'])?></h1>
    <p>Welcome, <?=$this->esc($params['user']->name)?>.</p>
<?php }); ?>
```

```php
<!-- templates/layouts/main.phtml -->
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title><?=$this->esc($title)?></title>
</head>
<body>
    <?php $this->block('content'); ?>
</body>
</html>
```

## Creating and configuring the engine

The constructor accepts four arguments:

```php
$view = new NativeLoader(
    namespaces: [
        'app' => __DIR__ . '/templates',
        'admin' => __DIR__ . '/templates/admin',
    ],
    functions: [
        'money' => static fn (float $amount): string => '$' . number_format($amount, 2),
    ],
    extension: 'phtml',
    globals: [
        'siteName' => 'Acme',
        'locale' => 'en_US',
    ],
);
```

| Argument | Default | Description |
| --- | --- | --- |
| `namespaces` | `[]` | Map of template namespace to an existing root directory. |
| `functions` | `[]` | Map of function name to callable. Application functions replace built-ins with the same name. |
| `extension` | `'phtml'` | Template extension, with or without a leading dot. It must be an extension, not a path. |
| `globals` | `[]` | Values available to every top-level render. Render data takes precedence. |

Configuration can also be extended after construction:

```php
$view
    ->addNamespace('mail', __DIR__ . '/templates/mail')
    ->addFunction('initials', static function (string $name): string {
        return implode('', array_map(
            static fn (string $part): string => strtoupper($part[0]),
            preg_split('/\s+/', trim($name)),
        ));
    })
    ->addGlobal('currency', 'USD');
```

`addNamespace()` and `addGlobal()` return the loader, so they can be chained. `addFunction()` does too.
Use a valid PHP method identifier for any function that templates will call through `$this`; other non-empty names can
still be invoked through `callFunction()`.

### Namespace and extension rules

- Namespace names may contain ASCII letters, numbers, underscores, dots, and hyphens.
- Namespace directories must exist when registered. They are stored as canonical paths.
- Template names must contain a non-empty namespace and path separated by `::`.
- Forward and backward slashes in the template portion are normalized for the host operating system.
- Leading and trailing slashes around the template portion are ignored.
- The configured extension cannot be empty or contain `/`, `\`, or a null byte.
- The resolved file must remain inside the registered namespace, even when `..` segments or symbolic links are used.

Invalid names and escaped paths are rejected before the PHP file is included.

## Rendering and locating templates

### Returning rendered HTML

Both `render()` and `fetch()` return a string:

```php
$html = $view->render('app::pages/home', [
    'title' => 'Dashboard',
]);

$emailHtml = $view->fetch('mail::welcome', [
    'recipient' => $recipient,
]);
```

`fetch()` is an alias of `render()` at the loader level. Neither method automatically sends output to the response;
echo or return the resulting string yourself.

### Data and globals

Render data is merged over globals:

```php
$view = new NativeLoader(
    namespaces: ['app' => __DIR__ . '/templates'],
    globals: ['title' => 'Default title', 'siteName' => 'Acme'],
);

echo $view->render('app::page', ['title' => 'Page title']);
```

Inside a template, valid string keys become local PHP variables:

```php
<title><?=$this->esc($title)?> · <?=$this->esc($siteName)?></title>
```

Only names matching a PHP variable identifier are imported. The engine also protects `$this`, `$GLOBALS`, and its
internal include variables from replacement. Invalid keys remain in the context parameter array but do not become
local variables.

### Existence checks and resolved paths

```php
if ($view->exists('app::optional/banner')) {
    echo $view->render('app::optional/banner');
}

$absolutePath = $view->getTemplatePath('app::pages/home');
```

`exists()` returns `false` for malformed names, unknown namespaces, missing files, and paths that escape a namespace.
`getTemplatePath()` returns the canonical file path or throws an exception.

## Template context

Every native template runs with `$this` bound to `Qubus\View\Native\TemplateContext`. Its public methods provide the
features described below. Registered functions that do not match a concrete context method are dispatched through
`__call()`.

## Registered functions and pipelines

Registered functions are called as methods in templates:

```php
<span><?=$this->money($order->total)?></span>
<abbr title="<?=$this->esc($customer->name)?>">
    <?=$this->initials($customer->name)?>
</abbr>
```

They can also be invoked from application code:

```php
$formatted = $view->callFunction('money', [19.95]);
```

Calling an unknown function throws `FunctionDoesNotExistException`.

### Built-in registered functions

| Function | Purpose |
| --- | --- |
| `strip(string, removeBreaks = false, tags = '', invert = false)` | Removes HTML tags and their contents; script and style contents are removed by default. |
| `trim(array\|string)` | Removes all whitespace characters, not only leading and trailing whitespace. |
| `now(timezone = null)` | Returns a Carbon instance for the current time. |
| `upper`, `lower` | Call PHP's `strtoupper()` and `strtolower()`. |
| `ucfirst`, `lcfirst`, `ucwords` | Apply the corresponding PHP string function. |
| `sprintf` | Formats a string with PHP `sprintf()`. |
| `wordwrap` | Wraps text with PHP `wordwrap()`. |
| `alpine`, `alpineData`, `alpineComponent` | Build safe Alpine directive attributes. |
| `alpineStore`, `alpineScript`, `alpineCloakStyle` | Build Alpine initialization tags and CSP-aware assets. |

Constructor functions replace these defaults when keys collide:

```php
$view = new NativeLoader(
    namespaces: ['app' => __DIR__ . '/templates'],
    functions: [
        'upper' => static fn (string $value): string => mb_strtoupper($value),
    ],
);
```

### Function pipelines

`batch()` passes a value through a pipe-separated list of registered functions:

```php
$heading = $view->batch('hello world', 'ucwords|upper');
```

Empty pipeline segments and surrounding whitespace are ignored. An unknown pipeline function throws `LogicException`.

The same pipeline is available through `esc()`:

```php
<h1><?=$this->esc($title, 'ucwords|upper')?></h1>
```

The functions run first; the final result is then converted to a string and HTML-escaped.

## Layouts and blocks

A child template chooses one parent with `parent()` and defines named blocks with `block()`.

```php
<!-- templates/pages/article.phtml -->
<?php $this->parent('app::layouts/main', [
    'pageClass' => 'article',
]); ?>

<?php $this->block('content', function (array $params): void { ?>
    <article>
        <h1><?=$this->esc($params['title'])?></h1>
        <p><?=$this->esc($params['summary'])?></p>
    </article>
<?php }); ?>
```

The layout renders the captured block:

```php
<!-- templates/layouts/main.phtml -->
<!doctype html>
<html>
<body class="<?=$this->esc($pageClass)?>">
    <?php $this->block('content'); ?>
</body>
</html>
```

Important block behavior:

- A block callback is captured immediately and receives the complete template parameter array as its first argument.
- A later callback definition replaces an earlier block of the same name after its callback has been captured.
- Output in a child template outside captured blocks is discarded when a parent is selected.
- `parent()` parameters are merged into the parent's context and replace matching string keys.
- A template can select only one parent. A second `parent()` call throws `ViewException`.
- Circular parent, partial, or component chains are rejected.

The replacement timing lets an intermediate layout decorate a child block. While the new callback is being captured,
`block()` can still render the previously captured value:

```php
<?php $this->parent('app::layouts/main'); ?>

<?php $this->block('content', function (): void { ?>
    <section class="content-shell">
        <?php $this->block('content'); ?>
    </section>
<?php }); ?>
```

The final layout should normally render the block without supplying another callback. Use the `default` argument for
fallback layout content.

### Optional blocks and defaults

```php
<?php if ($this->hasBlock('sidebar')): ?>
    <aside><?php $this->block('sidebar'); ?></aside>
<?php endif; ?>

<?php $this->block('subtitle', default: 'No subtitle'); ?>
```

Rendering a block that has not been defined and has no default throws `ViewException`.

## Partials and nested rendering

`insert()` renders another namespaced template directly:

```php
<?php $this->insert('app::partials/user-card', [
    'user' => $author,
    'compact' => true,
]); ?>
```

Nested templates inherit the current parameters. Explicit parameters replace matching values for that nested render.

Use the context-level `fetch()` to capture the nested result:

```php
<?php $card = $this->fetch('app::partials/user-card', ['user' => $author]); ?>
<section class="result"><?=$card?></section>
```

The returned string is rendered template markup. Escape values inside the partial; do not escape the complete partial
unless you intend to show its HTML literally. Blocks and stacks created by a nested render propagate back to the
calling context.

## Components and slots

`component()` is a partial helper with an optional captured slot:

```php
<?php $this->component(
    'app::components/alert',
    ['type' => 'warning'],
    function (): void { ?>
        Your session will expire soon.
    <?php },
); ?>
```

The component receives the slot as `$slot`:

```php
<!-- templates/components/alert.phtml -->
<div class="alert alert-<?=$this->esc($type)?>">
    <?=$slot?>
</div>
```

The slot callback is output-captured and is called without arguments. Its completed markup is not escaped by the
engine. Escape or purify untrusted values while creating the slot.

## Named content stacks

Stacks collect content in children, partials, and components for later output in a layout. Typical uses include page
scripts, styles, metadata, and preload tags.

```php
<?php $this->push('scripts', function (): void { ?>
    <script src="/assets/profile.js" defer></script>
<?php }); ?>

<?php $this->prepend('scripts', '<script src="/assets/runtime.js" defer></script>'); ?>
```

Render a stack in the layout:

```php
<?php if ($this->hasStack('scripts')): ?>
    <?php $this->stack('scripts'); ?>
<?php else: ?>
    <?php $this->stack('scripts', '<!-- no page scripts -->'); ?>
<?php endif; ?>
```

- `push()` appends a string or captured callable.
- `prepend()` inserts a string or captured callable at the beginning.
- `stack()` echoes the collected string or its default.
- `hasStack()` reports whether the stack has been created.

Stack content is trusted rendered markup and is not escaped automatically.

## Escaping and output safety

Native PHP output is not automatically escaped. Use the helper appropriate to the output context.

```php
<!-- HTML text and quoted ordinary attributes -->
<h1><?=$this->esc($title)?></h1>
<input value="<?=$this->esc($value)?>">

<!-- URL attributes -->
<a href="<?=$this->escUrl($url, ['https'])?>">Profile</a>

<!-- Inline JavaScript attribute content -->
<button onclick="<?=$this->escJs($handler)?>">Run</button>

<!-- User-supplied rich HTML -->
<article><?=$this->purify($userSuppliedHtml)?></article>
```

### Context helpers

| Method | Use |
| --- | --- |
| `esc(string, ?pipeline)` | Escape HTML text or an ordinary quoted HTML attribute, optionally after a registered-function pipeline. |
| `escUrl(string, schemes = [], encode = false)` | Validate and escape a URL for a quoted URL attribute. The scheme list is application-controlled. |
| `escJs(string)` | Escape inline JavaScript attribute content. Prefer external scripts where possible. |
| `purify(string\|array\|null, isImage = false)` | Sanitize rich HTML using the security package's purifier. |
| `raw(mixed)` | Cast to string without escaping or sanitizing. |

`raw()` does not make data safe:

```php
<?=$this->raw($trustedHtml)?>
```

Only use it with application-generated markup or content already passed through an appropriate sanitizer. Escaping is
context-specific: HTML escaping is not a substitute for URL validation, JavaScript encoding, CSS validation, or safe
DOM APIs.

### Output capture safety

Blocks, slots, stack callbacks, and nested templates use exception-safe output buffers. If a callback throws, buffers
opened by the engine are cleaned before the exception is rethrown.

## Display helpers

Native context methods also include:

```php
<?=$this->truncate($description, 120, '…')?>
<?=$this->truncate($trustedHtml, 120, '…', isHtml: true)?>
<?=$this->concat('Joshua', 'Parker', ' ', 'Jr.')?>
```

`truncate()` delegates to `truncate_string()`. Set `isHtml: true` only when truncating markup. `concat()` joins the first
two strings and any additional strings using the supplied separator.

## Alpine.js integration

The Native engine registers safe server-side builders for Alpine directives and state. Scaffold does not install,
bundle, or start Alpine; your application controls the Alpine version and delivery method.

### Inline component state and directives

```php
<div
    <?=$this->alpineData([
        'open' => false,
        'label' => $menuLabel,
    ])?>
    <?=$this->alpine([
        'on:click.outside' => 'open = false',
        'show' => 'open',
        'transition.opacity' => null,
        'cloak' => null,
    ])?>
>
    <button <?=$this->alpine(['on:click' => 'open = ! open'])?>>
        <?=$this->esc($menuLabel)?>
    </button>
</div>
```

`alpineData()` JSON-encodes arrays and objects with script-safe flags, then escapes the value for an HTML attribute.
An empty state produces `x-data="{}"`.

`alpine()` accepts:

- aliases such as `data`, `init`, `show`, `text`, `html`, `model`, `modelable`, `for`, `transition`, `effect`, `ignore`,
  `ref`, `cloak`, `teleport`, `if`, and `id`;
- `on:event` and `bind:attribute`, normalized to `x-on:event` and `x-bind:attribute`;
- full `x-*`, `@event`, and `:attribute` forms, including modifiers;
- `null` or a numeric list entry for a valueless directive such as `x-cloak`;
- scalar expressions, booleans, arrays, objects, and `JsonSerializable` values.

Directive names are validated and attribute values are escaped. Alpine expressions are still executable JavaScript:
never accept an expression directly from an untrusted user.

### Registered Alpine.data components

```php
<section <?=$this->alpineComponent('dropdown', [true, $menuLabel])?>>
    ...
</section>
```

This renders an `x-data="dropdown(true, ...)"` attribute. List arguments become positional JavaScript arguments. An
associative PHP array is encoded as one object argument:

```php
<?=$this->alpineComponent('profileCard', [
    'userId' => $user->id,
    'compact' => true,
])?>
```

Component names must be valid JavaScript identifiers, optionally separated by dots.
With no arguments, `alpineComponent('dropdown')` renders `x-data="dropdown"`; supply an argument list when the
provider must be invoked as a function.

### Hydrated stores, script loading, and x-cloak

```php
<?=$this->alpineStore('session', [
    'user' => ['id' => $user->id, 'name' => $user->name],
], $cspNonce)?>

<?=$this->alpineScript('/assets/alpine.js', $cspNonce, [
    'integrity' => $integrity,
    'crossorigin' => 'anonymous',
])?>

<?=$this->alpineCloakStyle($cspNonce)?>
```

- `alpineStore()` emits an `alpine:init` listener that registers `Alpine.store(name, state)`.
- `alpineScript()` accepts relative, HTTP, or HTTPS URLs and adds `defer` by default.
- Supported script attributes are `async`, `crossorigin`, `defer`, `integrity`, `referrerpolicy`, and `type`.
- Pass `['defer' => false]` to remove the default `defer` attribute.
- `alpineCloakStyle()` emits `[x-cloak]{display:none!important}`.
- Store and style builders accept an optional CSP nonce. The script tag builder applies it to the external script too.

For a strict Content Security Policy, use Alpine's CSP-compatible build and provide the per-request nonce to inline
builders.

### Calling the builders outside templates

All builders are available directly through `Qubus\View\Alpine`:

```php
use Qubus\View\Alpine;

$attributes = Alpine::attributes(['show' => 'open']);
$state = Alpine::data(['open' => false]);
```

They return `Qubus\View\HtmlString`, a stringable marker for HTML already constructed and escaped by the library.

## Advanced result access

`makeContext()` returns an invokable `TemplateContext`. Invoking it returns a `TemplateResult` containing the rendered
HTML and the final block and stack state:

```php
$context = $view->makeContext('app::pages/article', [
    'title' => 'Native Templates',
]);

$result = $context();

echo $result->getContent();
$blocks = $result->getBlocks();
$stacks = $result->getStacks();

echo (string) $result;
```

`makeContext()` also accepts an initial block map as its third argument. Most applications should use `render()` or
`fetch()`; use the context/result API when an integration needs block or stack metadata.

## Exceptions and error handling

| Exception | Cause |
| --- | --- |
| `InvalidTemplateNameException` | Invalid `namespace::template` syntax, namespace name, null byte, or path outside a namespace. |
| `TemplateNotFoundException` | Missing namespace directory, unknown namespace, or missing template file. |
| `FunctionDoesNotExistException` | A template or application calls an unknown registered function. |
| `ViewException` | Invalid rendering state, including duplicate parents, missing blocks, or circular template references. |
| `InvalidArgumentException` | Invalid extension, function name, global name, or Alpine builder argument. |
| `LogicException` | `batch()` references an unknown pipeline function. |

PHP errors and other `Throwable` instances raised inside a native template or callback are cleaned up and propagated.

```php
use Qubus\View\Native\Exception\FunctionDoesNotExistException;
use Qubus\View\Native\Exception\InvalidTemplateNameException;
use Qubus\View\Native\Exception\TemplateNotFoundException;
use Qubus\View\Native\Exception\ViewException;

try {
    $html = $view->render('app::pages/article', ['title' => 'Example']);
} catch (
    FunctionDoesNotExistException
    | InvalidTemplateNameException
    | TemplateNotFoundException
    | ViewException $exception
) {
    $logger->error($exception->getMessage(), ['exception' => $exception]);
    $html = $view->render('app::errors/500');
}
```

Catch exceptions at the HTTP or console boundary, log the original exception, and return an application-specific error
response. Do not expose filesystem paths or raw exception details to end users.

## Public API summary

### `NativeLoader`

```php
new NativeLoader(array $namespaces = [], array $functions = [], string $extension = 'phtml', array $globals = [])

$view->addNamespace(string $namespace, string $path): NativeLoader
$view->addFunction(string $name, callable $callback): NativeLoader
$view->addGlobal(string $name, mixed $value): NativeLoader
$view->render(string $template, array $data = []): string
$view->fetch(string $template, array $data = []): string
$view->exists(string $name): bool
$view->getTemplatePath(string $name): string
$view->callFunction(string $name, array $arguments = []): mixed
$view->batch(mixed $value, string $functions): mixed
$view->makeContext(string $template, array $data = [], array $blocks = []): TemplateContext
```

### `TemplateContext` methods available as `$this`

```php
$this->parent(string $template, array $params = []): void
$this->insert(string $template, array $params = []): void
$this->fetch(string $template, array $params = []): string
$this->block(string $name, ?callable $callback = null, ?string $default = null): void
$this->hasBlock(string $name): bool
$this->push(string $name, callable|string $content): void
$this->prepend(string $name, callable|string $content): void
$this->hasStack(string $name): bool
$this->stack(string $name, string $default = ''): void
$this->component(string $template, array $params = [], ?callable $slot = null): void
$this->esc(string $string, ?string $functions = null): string
$this->raw(mixed $value): string
$this->escJs(string $string): string
$this->escUrl(string $url, array $scheme = [], bool $encode = false): string
$this->purify(array|string|null $string, bool $isImage = false): string
$this->truncate(string $string, int $limit, string $continuation = '...', bool $isHtml = false): string
$this->concat(string $string1, string $string2, string $separator = ',', string ...$strings): string
```

Any other method name is resolved against the registered-function map.

## Recommended project structure

```text
templates/
├── components/
│   ├── alert.phtml
│   └── user-card.phtml
├── errors/
│   └── 500.phtml
├── layouts/
│   └── main.phtml
├── pages/
│   ├── home.phtml
│   └── profile.phtml
└── partials/
    ├── footer.phtml
    └── navigation.phtml
```

Keep escaping close to output, keep layouts responsible for document structure and stacks, and use components or
partials for reusable fragments.
