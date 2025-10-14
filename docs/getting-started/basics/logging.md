---
title: Logging
sidebar_title: Logging
weight: 11
---

## Installation

```shell
composer require qubus/log
```

## Introduction

CodefyPHP includes a [PSR-3](https://www.php-fig.org/psr/psr-3/) logger. You can also conveniently use one of two factories: 
`Codefy\Framework\Factory\FileLoggerFactory` or `Codefy\Framework\Factory\FileLoggerSmtpFactory`.

The factories can be used to log various types of information, such as errors, warnings, and debugging messages to
assist in identifying and resolving issues with the application. When using the `FileLoggerFactory`, all messages
will be generated under `File: ./storage/logs`.

## Usage

    <?php
    
    use Codefy\Framework\Codefy;

    $logger = Codefy::$PHP::getLogger();

    $logger->error('An error has occurred.');

## Using Levels

The Logger component supports the standard POSIX set of logging levels. Each level represents an increasing level of
severity.

| Method                             | Special arguments                                                                                                                                          | 
|------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------| 
| `->debug('log your message')`      | Detailed debug information.                                                                                                                                |
| `->info('log your message');`      | Interesting events. Examples: User logs in, SQL logs.                                                                                                      |
| `->notice('log your message');`    | Normal but significant events.                                                                                                                             |
| `->warning('log your message');`   | Exceptional occurrences that are not errors. Examples: Use of deprecated <br/>APIs, poor use of an API, undesirable things that are not necessarily wrong. |
| `->error('log your message');`     | Runtime errors that do not require immediate action but should typically <br/>be logged and monitored.                                                     |
| `->critical('log your message');`  | Critical conditions. Example: Application component unavailable, <br/>unexpected exception.                                                                |
| `->alert('log your message');`     | Action must be taken immediately. Example: Entire website down, <br/>database unavailable, etc. This should trigger the SMS alerts and wake you up.        |
| `->emergency('log your message');` | Emergency: system is unusable.                                                                                                                             |

### Context

You can add extra information to logging by passing an array context:

    <?php
    
    $logger->info('Adding a new user.', ['username' => 'codefyadmin']);

## SMTP Logging

When your application is mission-critical or a component of your application is mission-critical, it is wise to use
the `FileLoggerSmtpFactory`. When using this logger, you can receive emails when you need to be alerted right away
of an issue. Email settings are configured at `File: ./config/mailer.php`. Sensitive info such as passwords, should be placed in
your `.env` file.

    <?php

    use Codefy\Framework\Codefy;

    $logger = Codefy::$PHP::getSmtpLogger();
    
    $logger->critical('The database is not responding.');