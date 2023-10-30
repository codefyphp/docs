With `Mailer`, you can send emails from anywhere in your application. The configuration for `Mailer` can be found in 
`.env` and `config/mailer.php`.

You will first need to load then instantiate the mailer class:

    <?php
    
    use Qubus\Config\Collection;
    use Qubus\Mail\Mailer;
    
    use function Codefy\Framework\Helpers\config_path;
    
    $config = Collection::factory([
    'path' => config_path()
    ]);
    
    $mail = (new Mailer())->factory('smtp', $config);

Starting with CodefyPHP version 1.0.6, the above gets even easier:

    <?php
    
    use Codefy\Framework\Codefy;
    
    $mail = Codefy::$PHP->mailer

## Sending An Email

    <?php
    
    $mail->send(function ($message) {
        $message->to('phpframe@gmail.com');
        $message->from('test@gmail.com', 'CodefyPHP');
        $message->subject('Test Message');
        $message->body('This is a regular plain text message.');
        $message->charset('utf-8');
        $message->html(false);
    });

## Sending An HTML Email

    <?php
    
    $mail->send(function ($message) {
        $message->to('phpframe@gmail.com');
        $message->from('test@gmail.com', 'CodefyPHP');
        $message->subject('Test Message');
        $message->body('This is an <strong>html</strong> message.');
        $message->charset('utf-8');
        $message->html(true);
    });

## Using Email Templates

You can send an email using an email template and pass in variables that can be replaced.

    <?php

    use function Codefy\Framework\Helpers\resource_path;
    
    $mail->send(function ($message) {
        $message->to('phpframe@gmail.com');
        $message->from('test@gmail.com', 'CodefyPHP');
        $message->subject('Test Message');
        $message->body(['MESSAGE' => 'This is an <strong>html</strong> message.'], [
            'template_name' => resource_path('email.html'),
        ]);
        $message->charset('utf-8');
        $message->html(true);
    });

## Sending Attachment

    <?php

    use function Codefy\Framework\Helpers\storage_path;
    
    $mail->send(function ($message) {
        $message->to('phpframe@gmail.com');
        $message->from('test@gmail.com', 'CodefyPHP');
        $message->subject('Test Message');
        $message->body('This is an <strong>html</strong> message.');
        $message->charset('utf-8');
        $message->html(true);
        $message->attach(storage_path('file.pdf'));
    });