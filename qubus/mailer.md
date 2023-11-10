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

Starting with CodefyPHP version 2.0.0, the above gets even easier:

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

If you want to send a simple or quick email, you can utilize the `mail` function.

    <?php

    use function Codefy\Framework\Helpers\mail;

    try {
        return mail(
            to: ['test@example.com' => 'Recipient Name'],
            subject: 'Email Message',
            message: 'This is a <strong>simple</strong> email message.',
            headers: [
                'cc' => [
                    'recipientone@example.com' => 'Recipient One',
                    'recipienttwo@example.com' => 'Recipient Two'
                ],
                'bcc' => ['another@example.com' => 'Another Recipient'],
            ],
            attachments: [storage_path('file.pdf')]
        );
    } catch (\PHPMailer\PHPMailer\Exception | Exception $e) {
    return $e->getMessage();
    }

The sender name and email is read from the environment (`.env`) file. You can override it by adding filters:

    <?php
    
    use Qubus\EventDispatcher\ActionFilter\Observer;
    
    //override sender name
    (new Observer())->filter->addFilter('mail.from.name', fn() => 'My Business Name');
    
    //override sender email
    (new Observer())->filter->applyFilter('mail.from.email', fn() => 'business@businessname.com');