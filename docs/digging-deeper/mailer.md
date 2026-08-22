---
title: Mail
sidebar_title: Mail
summary: Send plain-text and HTML email from CodefyPHP with SMTP, templates, attachments, recipient options, and a concise mailer API.
keywords: php-mailer,smtp-email,email-templates
order: 26
---

## Installation

```shell
composer require qubus/mail
```

## Introduction

With `Mailer`, you can send emails from anywhere in your application. The configuration for `Mailer` can be found in 
`.env` and `config/mailer.php`.

You will first need to load then instantiate the mailer class:

    <?php
    
    use Codefy\Framework\Support\CodefyMailer;
    use Qubus\Config\Collection;
    use Qubus\Exception\Exception;
    
    use function Codefy\Framework\Helpers\config_path;
    
    $config = Collection::factory([
        'path' => config_path()
    ]);
    
    $mailer = new CodefyMailer($config);

Starting with CodefyPHP version 2.0.0, you can use the mailer global property:

    <?php
    
    use Codefy\Framework\Codefy;
    
    $mailer = Codefy::$PHP->mailer

## Sending An Email

    <?php
    
    try {
        $mailer
            ->withSmtp()
            ->withFrom(address: 'framework@example.com')
            ->withTo(address: 'test@example.com')
            ->withSubject(subject: 'Email Message')
            ->withBody(data: 'This is a simple email message.')
            ->send();
    } catch (\PHPMailer\PHPMailer\Exception | Exception $e) {
        return $e->getMessage();
    }

## Sending An HTML Email

    <?php
    
    try {
        $mailer
            ->withSmtp()
            ->withFrom(address: 'framework@example.com')
            ->withTo(address: 'test@example.com')
            ->withSubject(subject: 'Email Message')
            ->withBody(data: 'This is a <strong>simple</strong> email message.')
            ->withHtml(isHtml: true)
            ->send();
    } catch (\PHPMailer\PHPMailer\Exception | Exception $e) {
        return $e->getMessage();
    }

## Using Email Templates

You can send an email using an email template and pass in variables that can be replaced.

    <?php

    use function Codefy\Framework\Helpers\resource_path;
    
    try {
        $mailer
            ->withSmtp()
            ->withFrom(address: 'framework@example.com')
            ->withTo(address: 'test@example.com')
            ->withSubject(subject: 'Email Message')
            ->withBody(
                data: ['MESSAGE' => 'This is a <strong>simple</strong> email message.'],
                options: ['template_name' => resource_path('email.html')]
            )
            ->withHtml(isHtml: true)
            ->send();
    } catch (\PHPMailer\PHPMailer\Exception | Exception $e) {
        return $e->getMessage();
    }

## Sending Attachment

    <?php

    use function Codefy\Framework\Helpers\storage_path;

    try {
        $mailer
            ->withSmtp()
            ->withFrom(address: 'framework@example.com')
            ->withTo(address: 'test@example.com')
            ->withSubject(subject: 'Email Message')
            ->withBody(
                data: ['MESSAGE' => 'This is a <strong>simple</strong> email message.'],
                options: ['template_name' => resource_path('email.html')]
            )
            ->withAttachment(storage_path('file.pdf'))
            ->withHtml(isHtml: true)
            ->send();
    } catch (\PHPMailer\PHPMailer\Exception | Exception $e) {
        return $e->getMessage();
    }

## Simple Email

If you want to send a simple or quick email, you can utilize the [`mail`](helpers/mail.md) helper.
