---
title: CodefyPHP 3 Is Here
date:
  created: 2023-10-15 08:00:00
authors: [nomadicjosh]
description: CodefyPHP 3 is the newest release of the PHP web framework for building complex applications.
---

# CodefyPHP 3 Is Here

CodefyPHP 3 is the newest release of the PHP web framework for building complex applications. This release includes a 
plethora of changes, updates, enhancements, and bug fixes. Due to config changes cross many file of the config files, 
it is recommended that you read thoroughly through the [documentation](https://codefyphp.com/docs/) and the 
[skeleton](https://github.com/codefyphp/skeleton) app to ascertain the best way to upgrade your existing applications.

<!-- more -->

From asset management to encrypting your environment data, CodefyPHP 3 makes it easier to create secure, robust applications 
that scale over time. Below are just a few of the changes you will find in version 3.

This new release brings lots of changes, updates, and bug fixes:

- fixed: marking service providers as registered.
- feature: console commands
    -  `vendor:publish`
    - [`asset:flush`](../../digging-deeper/assets.md#pipeline)
    - [`generate:key:file`](../../getting-started/configuration.md#encrypting-environment-data)
    - [`encrypt:env`](../../getting-started/configuration.md#encrypting-environment-data)
    - [`queue:*`](../../digging-deeper/queues.md)
- feature: helpers
    - [`command()`](../../digging-deeper/helpers/command.md)
    - [`ask()`](../../digging-deeper/helpers/ask.md)
    - [`trans()`](../../digging-deeper/localization.md#translation-helpers)
    - [`queue()`](../../digging-deeper/helpers/queue.md)
- feature: [job queues](../../digging-deeper/queues.md)
- feature: [schedule tasks](../../digging-deeper/scheduler.md#scheduling-tasks)
- feature: middlewares
    - Content cache
    - HTTP cache
    - Referer Spam
    - API
    - Rate Limiter
    - HTML, JS, and CSS minifier
- feature: [SEO helper](../../digging-deeper/seo.md) for better SEO
- enhancement: removed native providers and console commands from configs
- feature: automatic loading of native providers and console commands

And a host of other bug fixes, enhancements, and new features. Check out the new [documentation](https://codefyphp.com/docs/) for a full view of what v3.0.0 has to offer.