---
title: Codex Commands
sidebar_title: Codex Commands
weight: 6
---

Codex is the command line interface for CodefyPHP. It provides a few native commands to get you started building your 
first project. Codex depends on the [symfony/console](https://github.com/symfony/console) library.

Controller
----------

This command will create a controller class (i.e. UsersController) in `App/Infrastructure/Http/Controllers`:

    ❯ php codex stub:make Users_controller

Repository
----------

This command will create a repository class (i.e UserViewRepository) in `App/Infrastructure/Persistence/Repository`:

    ❯ php codex stub:make UserView_repository

Service Provider
----------------

This command will create a service provider class (i.e. DbalServiceProvider) in `App/Infrastructure/Providers`:

    ❯ php codex stub:make DbalService_provider

Middleware
----------

This command will create a middleware class (i.e. CsrfMiddleware) in `App/Infrastructure/Http/Middleware`:

    ❯ php codex stub:make Csrf_middleware

Error
-----

This command will create an error class (i.e. UserIdNotFoundError) in `App/Infrastructure/Errors`:

    ❯ php codex stub:make UserIdNotFound_error

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

## Creating Codex Commands

In addition to the commands provided with `Codex`, you may build your own custom commands. Commands are stored in the
`App/Application/Console/Commands` directory.

### Generating Commands

To generate a new command, you can use the `stub:make` Codex command:

    ❯ php codex stub:make CacheFileDelete_command

### Registering Commands

CodefyPHP registers and loads commands automatically within the `App/Application/Console/Commands` directory. The best 
and recommended place to register your custom console commands is by populating the `commands` property in 
`App\Application\Console\Kernel`:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console;
    
    use Codefy\Framework\Console\ConsoleKernel;
    use Codefy\Framework\Scheduler\Schedule;
    
    class Kernel extends ConsoleKernel
    {
        /**
         * Add your custom console commands here.
         *
         * @var array
         */
        protected array $commands = [
            App\Application\Console\Commands\DummyCommand::class,
        ];
    
        //
    }

### Command Structure

After generating your new command, you need to define the name and description properties:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console\Commands;

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

### Exit Codes

The handle method should return an exit code which is an integer. Here are a list of the exit codes you can use:

* `Codefy\Framework\Console\ConsoleCommand::SUCCESS`
* `Codefy\Framework\Console\ConsoleCommand::FAILURE`
* `Codefy\Framework\Console\ConsoleCommand::INVALID`

### Inputs

If you command accepts arguments or options, you can use the `configure()` method:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console\Commands;

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

### User Confirmation

If you need to confirm an action before actually executing it, you can use the `confirm()` method:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console\Commands;

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

!!! note
    In this case, the user will be asked "Do you want to continue?". If the user answers with `y` 
    (or any word, expression starting with `y` due to default answer regex, e.g `yeti`) it returns `true` or `false` 
    otherwise, e.g. `n`. The second argument is the default value to return if the user doesn't enter any valid input. 
    If the second argument is not provided, `false` is assumed.

### Prompt for Input

You can also ask beyond a simple yes/no question.

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console\Commands;

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

#### Single Choice

If you have a predefined list of answers, you can use the `choice()` method:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console\Commands;

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

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console\Commands;

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

### Printing Output

To send output to the console, you may use the following methods:

* `terminalRaw` - Display plain, uncolored text.
* `terminalInfo` - Display green colored text.
* `terminalComment` - Display yellow colored text.
* `terminalQuestion` - Display black text with blue colored background.
* `terminalError` - Display grey text with red colored background.
* `terminalNewLine` - Display a blank line.



