***

# Assets





* Full name: `\Qubus\Support\Assets`



## Properties


### assetRegex

Regex to match against a filename/url to determine if it is an asset.

```php
protected string $assetRegex
```






***

### cssRegex

Regex to match against a filename/url to determine if it is a CSS asset.

```php
protected string $cssRegex
```






***

### jsRegex

Regex to match against a filename/url to determine if it is a JavaScript asset.

```php
protected string $jsRegex
```






***

### noMinificationRegex

Regex to match against a filename/url to determine if it should not be minified by pipeline.

```php
protected string $noMinificationRegex
```






***

### publicDir

Absolute path to the public directory of your App (WEBROOT).

```php
protected ?string $publicDir
```

Required if you enable the pipeline.
No trailing slash!.




***

### cssDir

Directory for local CSS assets.

```php
protected string $cssDir
```

Relative to your public directory ('public_dir').
No trailing slash!.




***

### jsDir

Directory for local JavaScript assets.

```php
protected string $jsDir
```

Relative to your public directory ('public_dir').
No trailing slash!.




***

### packagesDir

Directory for local package assets.

```php
protected string $packagesDir
```

Relative to your public directory ('public_dir').
No trailing slash!.




***

### pipeline

Enable assets pipeline (concatenation and minification).

```php
protected bool|string $pipeline
```

Use a string that evaluates to `true` to provide the salt of the pipeline hash.
Use 'auto' to automatically calculated the salt from your assets last modification time.




***

### pipelineDir

Directory for storing pipelined assets.

```php
protected string $pipelineDir
```

Relative to your assets directories ('css_dir' and 'js_dir').
No trailing slash!.




***

### pipelineGzip

Enable pipelined assets compression with Gzip. Do not enable unless you know what you are doing!.

```php
protected bool|int $pipelineGzip
```

Useful only if your webserver supports Gzip HTTP_ACCEPT_ENCODING.
Set to true to use the default compression level.
Set an integer between 0 (no compression) and 9 (maximum compression) to choose compression level.




***

### fetchCommand

Closure used by the pipeline to fetch assets.

```php
protected ?\Closure $fetchCommand
```

Useful when file_get_contents() function is not available in your PHP
installation or when you want to apply any kind of preprocessing to
your assets before they get pipelined.

The closure will receive as the only parameter a string with the path/URL of the asset, and
it should return the content of the asset file as a string.




***

### notifyCommand

Closure invoked by the pipeline whenever new assets are pipelined for the first time.

```php
protected ?\Closure $notifyCommand
```

Useful if you need to hook to the pipeline event for things such syncing your pipelined
assets with an external server or CDN.

The closure will receive five parameters:
- String containing the name of the file that has been created.
- String containing the relative URL of the file.
- String containing the absolute path (filesystem) of the file.
- Array containing the assets included in the file.
- Boolean indicating whether a gzipped version of the file was also created.




***

### cssMinifier

Closure used by the pipeline to minify CSS assets.

```php
protected ?\Closure $cssMinifier
```






***

### jsMinifier

Closure used by the pipeline to minify JavaScript assets.

```php
protected ?\Closure $jsMinifier
```






***

### collections

Available collections.

```php
protected array $collections
```

Each collection is an array of assets.
Collections may also contain other collections.




***

### css

CSS files already added.

```php
protected array $css
```

Not accepted as an option of config() method.




***

### js

JavaScript files already added.

```php
protected array $js
```

Not accepted as an option of config() method.




***

## Methods


### __construct



```php
public __construct(array $options = []): void
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$options` | **array** | See config() method for details. |





***

### config

Set up configuration options.

```php
public config(array $config): \Qubus\Support\Assets
```

All the class properties except 'js' and 'css' are accepted here.
Also, an extra option 'autoload' may be passed containing an array of
assets and/or collections that will be automatically added on startup.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$config` | **array** | Configurable options. |





***

### add

Add an asset or a collection of assets.

```php
public add(mixed $asset): \Qubus\Support\Assets
```

It automatically detects the asset type (JavaScript, CSS or collection).
You may add more than one asset passing an array as argument.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **mixed** |  |





***

### prepend

Add an asset or a collection of assets to the beginning of the queue.

```php
public prepend(mixed $asset): \Qubus\Support\Assets
```

It automatically detects the asset type (JavaScript, CSS or collection).
You may prepend more than one asset passing an array as argument.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **mixed** |  |





***

### addCss

Add a CSS asset.

```php
public addCss(mixed $asset): \Qubus\Support\Assets
```

It checks for duplicates.
You may add more than one asset passing an array as argument.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **mixed** |  |





***

### prependCss

Add a CSS asset to the beginning of the queue.

```php
public prependCss(mixed $asset): \Qubus\Support\Assets
```

It checks for duplicates.
You may prepend more than one asset passing an array as argument.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **mixed** |  |





***

### addJs

Add a JavaScript asset.

```php
public addJs(mixed $asset): \Qubus\Support\Assets
```

It checks for duplicates.
You may add more than one asset passing an array as argument.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **mixed** |  |





***

### prependJs

Add a JavaScript asset to the beginning of the queue.

```php
public prependJs(mixed $asset): \Qubus\Support\Assets
```

It checks for duplicates.
You may prepend more than one asset passing an array as argument.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **mixed** |  |





***

### css

Build the CSS `<link>` tags.

```php
public css(array|\Closure|null $attributes = null): string
```

Accepts an array of $attributes for the HTML tag.
You can take control of the tag rendering by
providing a closure that will receive an array of assets.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array&#124;\Closure&#124;null** |  |





***

### js

Build the JavaScript `<script>` tags.

```php
public js(array|\Closure|null $attributes = null): string
```

Accepts an array of $attributes for the HTML tag.
You can take control of the tag rendering by
providing a closure that will receive an array of assets.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array&#124;\Closure&#124;null** |  |





***

### registerCollection

Add/replace collection.

```php
public registerCollection(string $collectionName, array $assets): \Qubus\Support\Assets
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$collectionName` | **string** |  |
| `$assets` | **array** |  |





***

### reset

Reset all assets.

```php
public reset(): \Qubus\Support\Assets
```












***

### resetCss

Reset CSS assets.

```php
public resetCss(): \Qubus\Support\Assets
```












***

### resetJs

Reset JavaScript assets.

```php
public resetJs(): \Qubus\Support\Assets
```












***

### cssPipeline

Minify and concatenate CSS files.

```php
protected cssPipeline(): string
```












***

### jsPipeline

Minify and concatenate JavaScript files.

```php
protected jsPipeline(): string
```












***

### pipeline

Minify and concatenate files.

```php
protected pipeline(array $assets, string $extension, string $subdirectory, \Closure $minifier): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$assets` | **array** |  |
| `$extension` | **string** |  |
| `$subdirectory` | **string** |  |
| `$minifier` | **\Closure** |  |





***

### calculatePipelineHash

Calculate the pipeline hash.

```php
protected calculatePipelineHash(array $assets): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$assets` | **array** |  |





***

### packLinks

Download, concatenate and minify the content of several links.

```php
protected packLinks(array $links, \Closure $minifier): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$links` | **array** |  |
| `$minifier` | **\Closure** |  |





***

### buildLocalLink

Build link to local asset.

```php
protected buildLocalLink(string $asset, string $dir): string
```

Detect packages links.






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **string** |  |
| `$dir` | **string** |  |


**Return Value:**

the link




***

### buildTagAttributes

Build an HTML attribute string from an array.

```php
public buildTagAttributes(array $attributes): string
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$attributes` | **array** |  |





***

### assetIsFromPackage

Determine whether an asset is normal or from a package.

```php
protected assetIsFromPackage(string $asset): bool|array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$asset` | **string** |  |





***

### isRemoteLink

Determine whether a link is local or remote.

```php
protected isRemoteLink(string $link): bool
```

Understands both "http://" and "https://" as well as protocol agnostic links "//"






**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$link` | **string** |  |





***

### getCss

Get all CSS assets already added.

```php
public getCss(): array
```












***

### getJs

Get all JavaScript assets already added.

```php
public getJs(): array
```












***

### addDir

Add all assets matching $pattern within $directory.

```php
public addDir(string $directory, string|null $pattern = null): \Qubus\Support\Assets
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$directory` | **string** | Relative to $this-&gt;publicDir |
| `$pattern` | **string&#124;null** | (regex) |





***

### addDirCss

Add all CSS assets within $directory (relative to public dir).

```php
public addDirCss(string $directory): \Qubus\Support\Assets
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$directory` | **string** | Relative to $this-&gt;publicDir |





***

### addDirJs

Add all JavaScript assets within $directory (relative to public dir).

```php
public addDirJs(string $directory): \Qubus\Support\Assets
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$directory` | **string** | Relative to $this-&gt;publicDir |





***

### rglob

Recursively get files matching $pattern within $directory.

```php
protected rglob(string $directory, string $pattern, string|null $ltrim = null): array
```








**Parameters:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `$directory` | **string** |  |
| `$pattern` | **string** | (regex) |
| `$ltrim` | **string&#124;null** | Will be trimmed from the left of the file path |





***


***
> Automatically generated on 2025-10-13
