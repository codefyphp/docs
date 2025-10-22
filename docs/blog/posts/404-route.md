---
title: How to Create a Catchall 404 Not Found Route
date:
  created: 2025-10-22 13:45:00
links:
  - getting-started/basics/routing.md
  - getting-started/basics/scaffold-templates.md
authors: [nomadicjosh]
description: Learn how to create a 404 not found route as a fallback for routes that do not exist.
---

# How to Create a Catchall 404 Not Found Route

Currently, if a route does not exist, CodefyPHP will return a 404 JSON response. But this can be overridden with a 
custom 404 page. In this article, I will show you have to create a catch-all route that will return a 404 page when a 
user visits a page that doesn't exist or when an internal link is broken.

<!-- more -->

## Catchall Route

First, we need to create a catch-all route that will be loaded when no route match is found. Please note, that this 
route must be the last route loaded in your route's listing.

```php title="file: ./routes/web/web.php"
<?php

declare(strict_types=1);

use Qubus\Http\Factories\HtmlResponseFactory;
use Qubus\Routing\Route\RouteGroup;
use Qubus\View\Renderer;

return function (\Qubus\Routing\Psr7Router $router) {
    // other routes/route groups
    
    $router->any('{any}', fn(Renderer $view) => HtmlResponseFactory::create($view->render('framework::error/404')));
};
```

In the example above, we are using an anonymous function as the callback instead of a controller. We are passing in 
`Renderer` as the parameter, and the function will return an HTML response with our 404 page.

## 404 View Template

Next, we need to add the needed assets. For this simple example, we need a CSS file and a template:

```css title="file: ./public/assets/css/error.css"
@import url(https://fonts.googleapis.com/css?family=Open+Sans);
html{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 98vh;
    background-color: #FAFAFA;
}
body{
    font-family: Open Sans, Arial, serif;
    font-size:.9rem;
    margin:2em auto;
    max-width:800px;
    padding:1em;
    line-height:1.4;
    color: #454545;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
}

.error-middle{
    display: block;
    vertical-align: middle;
}
```

```php title="file: ./resources/views/error/404.phtml"
<?php

use Codefy\Framework\Proxy\Codefy;

use function Codefy\Framework\Helpers\site_url;

?>
<!DOCTYPE html>
<html lang="<?=Codefy::$PHP->language;?>">
<head>
    <base href="<?=site_url()?>">
    <link rel="stylesheet" type="text/css" href="assets/css/error.css"/>
    <title>Error 404</title>
</head>
<body>
<div class="error-middle">
    <h1>Error 404 - Not Found</h1>
</div>
</body>
</html>
```

## Result

With our route, stylesheet and template now in place, if you were to visit a non-existent route, you should see the 
following result:

<h3 align="center">
    <img src="/docs/blog/images/404-not-found.png" width="660" alt="404 Not Found Page">
</h3>

