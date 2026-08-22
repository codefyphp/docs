---
title: Codex Commands
sidebar_title: Codex Commands
summary: Use the CodefyPHP Codex CLI to generate domains and application classes, register console commands, read input, confirm actions, and print output.
keywords: codex-cli,codefyphp-commands,php-code-generation
weight: 6
---

Codex is the command line interface for CodefyPHP. It provides a few native commands to get you started building your 
first project. Codex depends on the [symfony/console](https://github.com/symfony/console) library.

## Domain Setup

If you are using the skeleton template, and you are keeping the same architecture, then you need to create your domain 
structure before generating classes. For example, if you are working with a `Post` domain, you will need to first run the 
following command:

    ❯ php codex ddd:make:domain Post

The command will create the following file and folder structure:

    src/Domain/Post
    ├── Command
    ├── Dto
    ├── Enum
    ├── Event
    ├── Exception
    ├── Query
    ├── Repository
    ├── Service
    ├── Post.php
    ├── Validator
    └── ValueObject

Once the `domain` has been created, you can use the following commands to generate your different classes:

    ❯ php codex ddd:make

The `ddd:make` is the command you will use when you want to generate a controller, service provider, validator, middleware, 
aggregate, and so on. When you run the command, the following options will appear. For our example, we will choose 
option 8 for `Input Validator` under the `Post` domain:

    Select the type of class to generate:
    [0 ] Aggregate
    [1 ] Domain Event
    [2 ] Command + Handler
    [3 ] Query + Handler
    [4 ] Controller
    [5 ] Middleware
    [6 ] Service Provider
    [7 ] Console Command
    [8 ] Input Validator
    [9 ] Form Request
    [10] Aggregate Repository
    >

When we chose option 8, the following prompt appears, and then we should choose option 1:

    Select the namespace to generate the class in:
    [0] Application\
    [1] Domain\
    [2] Database\Seeders\
    [3] Infrastructure\
    >

We are at our next prompt, and we should choose option 8:

    Select subdirectory inside Domain\:
    [0 ] [root directory]
    [1 ] Post
    [2 ] Post/Command
    [3 ] Post/Event
    [4 ] Post/Exception
    [5 ] Post/Query
    [6 ] Post/Repository
    [7 ] Post/Service
    [8 ] Post/Validator
    [9 ] Post/ValueObject
    [10] User
    [11] User/Command
    [12] User/Dto
    [13] User/Enum
    [14] User/Event
    [15] User/Query
    [16] User/Repository
    [17] User/Service
    [18] User/Validator
    [19] User/ValueObject
    >

After choosing option 8, we will then be asked to name our Validator. For this example we will chose the name `StorePost`:

    Class name (no namespace): StorePost

After entering the name, click enter, and you should see a similar message:

    Created: /var/www/html/src/Domain/Post/Validator/StorePostValidator.php

Hash A Password
---------------

    ❯ php codex password:hash 'jsx82kjsks9273js'
    Your hashed password is: $2y$10$4A3iA5z.qyi6DZ5bibKXUujbqYdjH.QjpbO/lUDR9dalaN1IbEZtm 

Run the Scheduler
-----------------

The `schedule:run` command starts the scheduler and will execute any schedules/tasks that are due.

    ❯ php codex schedule:run

Scheduler List
--------------

The `schedule:list` command displays the list of registered jobs/tasks.

    ❯ php codex schedule:list

Run the Dev Server
------------------

`cd` into the root of your project and run the following command:

    ❯ php codex serve

Generate a Ulid string
----------------------

The `ddd:ulid` command is useful if you need to generate a Ulid string for testing or other purposes.

    ❯ php codex ddd:ulid

Generate a Uuid string
----------------------

The `ddd:uuid` command is useful if you need to generate a Uuid string for testing or other purposes.

    ❯ php codex ddd:uuid

### Registering Commands

CodefyPHP registers and loads commands automatically within the `src/Application/Console/Commands` directory. The best 
and recommended place to register your custom console commands is by populating the `commands` property in 
`Application\Console\Kernel`:

```php
<?php

declare(strict_types=1);

namespace Application\Console;

use Codefy\Framework\Console\ConsoleKernel;
use Codefy\Framework\Scheduler\Schedule;
use Symfony\Component\Console\Command\SignalableCommandInterface;

class Kernel extends ConsoleKernel
{
    /**
     * Add your custom console commands here.
     *
     * @var array<class-string<SignalableCommandInterface>|callable>
     */
    protected array $commands = [
        Application\Console\Commands\DummyCommand::class,
    ];

    //
}
```

### Command Structure

After generating your new command, you need to define the name and description properties:

```php
<?php

declare(strict_types=1);

namespace Application\Console\Commands;

use Codefy\Framework\Console\ConsoleCommand;

class CacheFileDeleteCommand extends ConsoleCommand
{
    protected string $name = 'cache:file:delete';

    protected string $description = 'Deletes cache files older than 30 days.';

    /**
     * @throws EnvironmentIsBrokenException
     */
    public function handle(): int
    {
        // logic for delete
        return ConsoleCommand::SUCCESS;
    }
}
```

### Exit Codes

The handle method should return an exit code which is an integer. Here are a list of the exit codes you can use:

* `Codefy\Framework\Console\ConsoleCommand::SUCCESS` or (recommended) `self::SUCCESS`
* `Codefy\Framework\Console\ConsoleCommand::FAILURE` or (recommended) `self::FAILURE`
* `Codefy\Framework\Console\ConsoleCommand::INVALID` or (recommended) `self::INVALID`

### Inputs

If you command accepts arguments or options, you can use the `configure()` method:

```php
<?php

declare(strict_types=1);

namespace Application\Console\Commands;

use Codefy\Framework\Console\ConsoleCommand;
use Symfony\Component\Console\Input\InputArgument;
use Symfony\Component\Console\Input\InputOption;

class CacheFileDeleteCommand extends ConsoleCommand
{
    protected string $name = 'cache:file:delete';

    protected string $description = 'Deletes cache files older than 30 days.';

    protected function configure(): void
    {
        parent::configure();

        $this
            ->addArgument(
                name: 'argument',
                mode: InputArgument::REQUIRED,
                description: 'This argument is required.'
            )
            ->addOption(
                name: 'force',
                shortcut: '-f',
                mode: InputOption::VALUE_NONE,
                description: 'Do not prompt for confirmation'
            )
            ->setHelp(
                help: <<<EOT
            The <info>cache:file:delete</info> command description...
            <info>php codex cache:file:delete argument</info>
            EOT
        );
    }

    /**
     * @throws EnvironmentIsBrokenException
     */
    public function handle(): int
    {
        // logic for delete
        return ConsoleCommand::SUCCESS;
    }
}
```

### User Confirmation

If you need to confirm an action before actually executing it, you can use the `confirm()` method:

```php
<?php

declare(strict_types=1);

namespace Application\Console\Commands;

use Codefy\Framework\Console\ConsoleCommand;
use Symfony\Component\Console\Input\InputArgument;
use Symfony\Component\Console\Input\InputOption;

class CacheFileDeleteCommand extends ConsoleCommand
{
    protected string $name = 'cache:file:delete';

    protected string $description = 'Deletes cache files older than 30 days.';

    //

    /**
     * @throws EnvironmentIsBrokenException
     */
    public function handle(): int
    {
        if (! $this->confirm(question: 'Do you want to continue?')) {
            return ConsoleCommand::SUCCESS;
        }
    }
}
```

!!! note
    In this case, the user will be asked "Do you want to continue?". If the user answers with `y` 
    (or any word, expression starting with `y` due to default answer regex, e.g `yeti`) it returns `true` or `false` 
    otherwise, e.g. `n`. The second argument is the default value to return if the user doesn't enter any valid input. 
    If the second argument is not provided, `false` is assumed.

### Prompt for Input

You can also ask beyond a simple yes/no question.

```php
<?php

declare(strict_types=1);

namespace Application\Console\Commands;

use Codefy\Framework\Console\ConsoleCommand;
use Symfony\Component\Console\Input\InputArgument;
use Symfony\Component\Console\Input\InputOption;

class CummyCommand extends ConsoleCommand
{
    //

    /**
     * @throws EnvironmentIsBrokenException
     */
    public function handle(): int
    {
        if (! $this->ask(question: 'Please enter your first name.', 'Bobby')) {
            return ConsoleCommand::SUCCESS;
        }
    }
}
```

#### Single Choice

If you have a predefined list of answers, you can use the `choice()` method:

```php
<?php

declare(strict_types=1);

namespace Application\Console\Commands;

use Codefy\Framework\Console\ConsoleCommand;
use Symfony\Component\Console\Input\InputArgument;
use Symfony\Component\Console\Input\InputOption;

class DummyCommand extends ConsoleCommand
{
    //

    /**
     * @throws EnvironmentIsBrokenException
     */
    public function handle(): int
    {
        $color = $this->choice(
            question: 'Please select your favorite color (defaults to red)',
            choices: ['red', 'blue', 'yellow'],
            default: 0,
            message: 'Color %s is invalid.'
        );
        
        $this->terminalComment(string: 'You have just selected: '.$color);
    }
}
```

!!! note
    To use custom indices, pass an array with custom numeric keys as the choice values:
    ```php
        $this->choice(
            question: 'Please select your favorite color',
            choices: [100 => 'red', 101 => 'blue', 102 => 'yellow']
        )
    ```

#### Multiple Choice

Sometimes, multiple answers can be given. The `multiChoice()` method provides this feature using comma separated values.

```php
<?php

declare(strict_types=1);

namespace Application\Console\Commands;

use Codefy\Framework\Console\ConsoleCommand;
use Symfony\Component\Console\Input\InputArgument;
use Symfony\Component\Console\Input\InputOption;

class DummyCommand extends ConsoleCommand
{
    //

    /**
     * @throws EnvironmentIsBrokenException
     */
    public function handle(): int
    {
        $color = $this->multiChoice(
            question: 'Please select your favorite color (defaults to red and blue)',
            choices: ['red', 'blue', 'yellow'],
            default: '0, 1',
        );
        
        $this->terminalComment(string: 'You have just selected: '.$color);
    }
}
```

### Printing Output

To send output to the console, you may use the following methods:

* `terminalRaw` - Display plain, uncolored text.
* `terminalInfo` - Display green colored text.
* `terminalComment` - Display yellow colored text.
* `terminalQuestion` - Display black text with blue colored background.
* `terminalError` - Display grey text with red colored background.
* `terminalNewLine` - Display a blank line.


