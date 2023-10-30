All configuration files for the CodefyPHP Framework are stored in the `config` directory. These config files allow you 
to configure security, your database, caching, cookies, and various other aspects of your application.

## Environment Variables

You can configure sensitive information through environment variables. As you can see in your `config/app.php`, the 
env() function is used to read configuration from the environment.

When you install the starter app, you will see a `config/.env.example` file. You will want to make a copy, rename it 
to `.env` and customize the values. Make sure to not commit your .env file to source control or you end up sharing 
sensitive information you don't want others to see.

Once your values are set, you can use the `env()` function to read from the environment.

    $appName = env(key: 'APP_NAME', default: 'CodefyPHP Framework');

The second value is a default value. This value will be used if the environment value is not set or is null.

## General Configuration

Below are the different environment variables that can be set along with their description.

### Application Variables.

- `APP_NAME` - The name of your application.
- `APP_ENV` - The current application environment: development or production.
- `APP_KEY` - You can set this as your api key to use in your application.
- `APP_SALT` - A long private string used for hashing or encryption.
- `APP_DEBUG` - If set to false, error and warnings will print. If set to true, they will not print to screen.
- `APP_BASE_PATH` - Set the base path of your application.
- `APP_BASE_URL` - Set the base url of your application.

### Mailer Configuration

- `MAILER_HOST` - Outgoing mail server name.
- `MAILER_PORT` - Outgoing mail server port.
- `MAILER_USERNAME` - SMTP username.
- `MAILER_PASSWORD` - SMTP password.
- `MAILER_AUTHMODE` - Authentication mechanism.
- `MAILER_ENCRYPTION` - SSL, TLS, or STARTTLS.
- `MAILER_FROM_EMAIL` - Sender email address. Maybe the same as `MAILER_USERNAME`.
- `MAILER_FROM_NAME` - Application name.
- `MAILER_SENDMAIL_PATH` - Set the path of sendmail if not using SMTP.

### Database Setup

- `DB_CONNECTION` - The default database connection.
- `DB_DRIVER` - Database driver being used (mysql, postgres, sqlite, sqlserver).
- `DB_HOST` - Database hostname.
- `DB_NAME` - Database name.
- `DB_CHARSET` - The character set to use when sending SQL statements to the server.
- `DB_COLLATION` - Sorting rule.
- `DB_TABLE_PREFIX` - Database table prefix.
- `DB_PORT` - Database port.
- `DB_USER` - Database username.
- `DB_PASSWORD` - Database password.

### Amazon S3

- `AWS_ACCESS_KEY_ID` - S3 access key.
- `AWS_SECRET_ACCESS_KEY` - S3 secret access key.
- `AWS_DEFAULT_REGION` - S3 region (us-east-2, us-west-1).
- `AWS_BUCKET` - S3 bucket.
- `AWS_URL` - S3 url.
- `AWS_ENDPOINT` - S3 endpoint (s3.us-east-2.amazonaws.com, s3.us-west-1.amazonaws.com).

### Logger Email Setup.

- `LOGGER_EMAIL_SUBJECT` - Email subject for log messages.
- `LOGGER_FROM_EMAIL` - Sender email address. Maybe the same as `MAILER_USERNAME`.
- `LOGGER_TO_EMAIL` - Recipient email address.

