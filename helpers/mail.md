Description
-----------

An alternative to using PHP's native mail function with other options for SMTP (default), Qmail, and Sendmail.

Usage
-----

    <?php

    use function Codefy\Framework\Helpers\mail;
    
    mail(string|array $to, string $subject, string $message, array $headers = [], array $attachments = []): bool;

Parameters
----------

**$to** (string|array) (required) Email recipient(s).

**$subject** (string) (required) Subject of the email.

**$message** (string) (required) The email body.

**$headers** (array) (optional) An array of headers to include.

**$attachments** (array) (optional) Attachments to include.

Return Value
------------

(bool) Returns false on error or true if no error occurred.

Example
-------

    <?php

    use function Codefy\Framework\Helpers\mail;
    use function Codefy\Framework\Helpers\storage_path;

    $to = ['test@example.com' => 'Recipient Name'];
    $subject = 'Email Message';
    $message = 'This is a <strong>simple</strong> email message.';
    $headers = [
        'cc' => [
            'recipientone@example.com' => 'Recipient One',
            'recipienttwo@example.com' => 'Recipient Two'
        ],
        'bcc' => ['another@example.com' => 'Another Recipient'],
    ];
    $attachments = [storage_path('file.pdf')];

    mail(to: $to, subject: $subject, message: $message, headers: $headers, attachments: $attachments);