CodefyPHP includes the [qubus/log](https://github.com/QubusPHP/log) component that is [PSR-3](https://www.php-fig.org/psr/psr-3/) 
compliant. If you are using the starter app or not, you can type-hint `Psr\Log\LoggerInterface`. But if you are using 
the starter app, you can conveniently use the factories instead: `Codefy\Framework\Factory\FileLoggerFactory` or 
`Codefy\Framework\Factory\FileLoggerSmtpFactory`.

The factories can be used to log various types of information, such as errors, warnings, and debugging messages to 
assist in identifying and resolving issues with the application. When using the `FileLoggerFactory`, all messages 
will be generated under `storage/logs`.

## Usage

    <?php
    
    use Codefy\Framework\Factory\FileLoggerFactory;
    
    FileLoggerFactory::getLogger()->error('An error has occurred.');

## Using Levels

The Logger component supports the standard POSIX set of logging levels. Each level represents an increasing level of 
severity.

- `FileLoggerFactory::getLogger()->debug('log your message');` - Detailed debug information.
- `FileLoggerFactory::getLogger()->info('log your message');` - Interesting events. Examples: User logs in, SQL logs.
- `FileLoggerFactory::getLogger()->notice('log your message');` - Normal but significant events.
- `FileLoggerFactory::getLogger()->warning('log your message');` - Exceptional occurrences that are not errors. Examples: Use of deprecated APIs, poor use of an API, undesirable things that are not necessarily wrong.
- `FileLoggerFactory::getLogger()->error('log your message');` - Runtime errors that do not require immediate action but should typically be logged and monitored.
- `FileLoggerFactory::getLogger()->critical('log your message');` - Critical conditions. Example: Application component unavailable, unexpected exception.
- `FileLoggerFactory::getLogger()->alert('log your message');` - Action must be taken immediately. Example: Entire website down, database unavailable, etc. This should trigger the SMS alerts and wake you up.
- `FileLoggerFactory::getLogger()->emergency('log your message');` - Emergency: system is unusable.

### Context

You can add extra information to logging by passing an array context:

    <?php
    
    FileLoggerFactory::getLogger()->info('Adding a new user.', ['username' => 'codefyadmin']);

## SMTP Logging

When your application is mission-critical or a component of your application is mission-critical, it is wise to use 
the `FileLoggerSmtpFactory`. When using this logger, you can receive emails when you need to be alerted right away 
of an issue. Email settings are configured at `config/mailer.php`. Sensitive info such as passwords, should be placed in 
your `.env` file.

    <?php
    
    FileLoggerSmtpFactory::getLogger()->critical ('The database is not responding.');