---
title: CodefyPHP v2.0.0 Honoring Mathias Verraes
description: Explore CodefyPHP 2.0 features, its updated application API and starter project, and the DDD and CQRS ideas inspired by Mathias Verraes.
summary: Explore CodefyPHP 2.0 features, its updated application API and starter project, and the DDD and CQRS ideas inspired by Mathias Verraes.
keywords: codefyphp-2,domain-driven-design,release-notes
date:
  created: 2024-09-05 13:58:00
  updated: 2025-10-13
authors: [nomadicjosh]
---

# CodefyPHP v2.0.0 - Honoring Mathias Verraes

It took longer than expected, but CodefyPHP v2.0.0 is out with shiny new features. This release is dedicated to 
Mathias Verraes, whose code [buttercup.protects](https://github.com/buttercup-php/protects) helped me to get a better 
grasp of DDD, CQRS, and is the base/foundation of CodefyPHP.

<!-- more -->

In this release, a new class Codefy was added, which interacts with the Application class. It is recommended that 
you use the class Codefy instead of using the Application class directly. To instantiate the new class you type 
`Codefy::$PHP`. So, for example if you needed to set a flash message in your controller, 
you can use `Codefy::$PHP->flash->error('This was an error.');` instead of instantiating the Flash class. 
You also have access to the following as well:

* `Codefy::$PHP->request` = \Qubus\Http\ServerRequest
* `Codefy::$PHP->response` = \Qubus\Http\Response
* `Codefy::$PHP->assets` = \Qubus\Support\Assets
* `Codefy::$PHP->mailer` = \Qubus\Mail\Mailer
* `Codefy::$PHP->session` = \Qubus\Http\Session\NativeSession
* `Codefy::$PHP->event` = \Qubus\EventDispatcher\Dispatcher
* `Codefy::$PHP->httpCookie` = \Qubus\Http\Cookies\Factory\CookieFactory
* `Codefy::$PHP->localStorage` = \Codey\Framework\Support\LocalStorage
* `Codefy::$PHP->configContainer` = \Qubus\Config\Collection
* `Codefy::$PHP->getLogger()` = \Codefy\Framework\Factory\FileLoggerFactory
* `Codefy::$PHP->getSmtpLogger()` = \Codefy\Framework\Factory\FileLoggerSmtpFactory
* 
The [skeleton app](https://github.com/codefyphp/skeleton) has also been updated. A simple admin backend was added with examples of domain events, 
repositories, middlewares, commandbus, querybus, services, and more. Also, the 
[Installation](../../getting-started/installation.md) guide has been updated to reflect the new changes, and how 
to get your first application up and running.
