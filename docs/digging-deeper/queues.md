---
title: Queues
sidebar_title: Queues
summary: Run background work in CodefyPHP by creating queueable jobs, publishing them to a queue, and consuming queued tasks with Codex commands.
keywords: php-job-queues,background-jobs,codex-cli
order: 40
---

During the building stage of your application, you may come against some processes that take longer than a typical 
web request. This is where queues come into play.

CodefyPHP uses it own native noSQL database for queues, so no database or service configuration is required.

## Creating a Job

You may place your class anywhere within your application that makes the most sense. For this example, the namespace 
`Application\Service` will be used.

```php
<?php

declare(strict_types=1);

namespace Application\Service;

use Codefy\Framework\Factory\FileLoggerFactory;
use Codefy\Framework\Proxy\Codefy;
use Codefy\Framework\Queue\SimpleQueue;
use PHPMailer\PHPMailer\Exception;
use Qubus\Http\ServerRequest;

use function Codefy\Framework\Helpers\resource_path;

class NewEmailSignup extends SimpleQueue
{
    public string $name = 'New User Email';

    public string $schedule = '* * * * *';

    public function __construct(protected ServerRequest $request)
    {
    }

    /**
     * @inheritDoc
     */
    public function handle(): bool
    {
        $mailer = Codefy::$PHP->mailer;
        $body = $this->request->getParsedBody();

        try {
            $mailer
                ->withSmtp()
                ->withFrom(address: 'myapp@gmail.com')
                ->withTo(address: $body['email'])
                ->withSubject(subject: 'Signup Confirmation')
                ->withBody(
                    data: ['MESSAGE' => 'Hello {name}. Your signup was successful...'],
                    options: ['template_name' => resource_path(path: 'email.html')]
                )
                ->withHtml(isHtml: true)
                ->send();
                
                return true;
        } catch (Exception $e) {
            FileLoggerFactory::getLogger()->error($e->getMessage());
        }
        
        return false;
    }
}
```

To handle the job, we always extend the `SimpleQueue` class and use the `handle()` method. This method is called when 
our job is executed. Also, note the two properties added to our job:

* `$name` - The name property sets the name of our job.
* `$schedule` - The schedule property sets a cron expression for our job. This is used to determine if/and when the job should run.

!!! note
    Please note that the properties defined in the job class, must have a `public` visibility.

## Sending Job to Queue

Depending on the type of job you need will depend on where you need to queue it. For our example, we will use a 
controller. Sending a task to the queue is very simple and comes down to one command:

```php
<?php

declare(strict_types=1);

namespace Application\Http\Controllers;

use Application\Service\NewEmailSignup;
use Codefy\Framework\Codefy;
use Codefy\Framework\Http\BaseController;
//

use function Codefy\Framework\Helpers\command;
use function Codefy\Framework\Helpers\site_url;
use function Codefy\Framework\Helpers\queue;
//

final class HomeController extends BaseController
{
    public function create(ServerRequest $request): ResponseInterface
    {
        $command = new CreateUserCommand(data: [
            //
            'email' => new EmailAddress(value: $request->get('email')),
            //
        ]);

        try {
            command(command: $command);

            queue(queue: new NewEmailSignup(request: $request))->createItem();

            return $this->redirect(url: site_url(path: $this->router->url(name: 'home')));
        } catch (\Exception $e) {
            // Handle exception
        }
    }
}
```

## Consuming the Queue

Since we sent our sample job to the queue, we need to add it to the schedule in `./src/Application/Console/Kernel.php`:

```php
<?php

protected function schedule(Schedule $schedule): void
{
    $schedule->php(script: 'codex queue:run')->everyMinute();
}
```

We set the schedule to run every minute, so that when the cron expression on our job is due, it will run at the exact 
moment it should.

## Breakdown

So let's break down what's happening in the background. When you use the [`queue`](helpers/queue.md) helper: 
`queue(queue: new NewEmailSignup(request: $request))->createItem()`, the job is added to the queue.

Then, when the schedule runs, the cron expression will be checked to see if the job is due. If the job is due, it will 
pop off from the queue, and the `handle()` method on the class `NewEmailSignup` will be triggered.

If the job was processed successfully, the job will be deleted from the queue. If the job did not process successfully, 
it will be `released`, and the queue will try to process it again based on the cron schedule.

The queue will try to process the job `3` times before it is considered for `garbage collection`. If you would like to 
increase that number, add a public `executions` property to your job class with a higher number:

```php
<?php

declare(strict_types=1);

namespace Application\Service;

use Codefy\Framework\Factory\FileLoggerFactory;
use Codefy\Framework\Proxy\Codefy;
use Codefy\Framework\Queue\SimpleQueue;
use PHPMailer\PHPMailer\Exception;
use Qubus\Http\ServerRequest;

use function Codefy\Framework\Helpers\resource_path;

class NewEmailSignup extends SimpleQueue
{
    public int $executions = 6;
    
    //

    public function __construct(protected ServerRequest $request)
    {
    }

    /**
     * @inheritDoc
     */
    public function handle(): bool
    {
        //
    }
}
```


