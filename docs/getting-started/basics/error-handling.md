---
title: Error Handling
sidebar_title: Error Handling
weight: 10
---

## Installation

```shell
composer require qubus/error
```

The `debug` option in your `./config/app.php` configuration file determines how much information is shown based on 
the set environment. This option is based on the `APP_DEBUG` setting in your environment file.

During testing, you can set `APP_DEBUG` to `true`, `APP_ENV` to `development` and also uncomment the `error.handler` 
middleware ([Whoops](https://github.com/filp/whoops)) alias in`./config/app.php` under `base_middlewares`.

Before going to production, make sure to comment out or remove `error.handler`, set `APP_DEBUG` to false, 
and set `APP_ENV` to `production`.

## PSR-3 Logging

Codefy uses a PSR-3 implementation of logging that sends your logs to files and inboxes. Check out the 
[Logging](logging.md) section for logging levels and SMTP logging for mission critical applications.

