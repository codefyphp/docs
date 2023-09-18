The scheduler allows you to manage scheduled tasks on your server. You can define your schedule for each task that is 
triggered by a single cron job, which will be discussed later.

Define a Schedule
-----------------

In order to define a schedule, you will need to open `App/Application/Console/Kernel.php`. All of your scheduled tasks c
an be defined in the `schedule` method. The example below is an [event dispatcher](https://codefyphp.com/knowledgebase/event-dispatcher/) task that runs daily:

    <?php
    
    declare(strict_types=1);
    
    namespace App\Application\Console;
    
    use Codefy\Framework\Console\ConsoleKernel;
    use Codefy\Framework\Scheduler\Schedule;
    
    class Kernel extends ConsoleKernel
    {
        /**
         * Place all your scheduled tasks here.
         *
         * @param Schedule $schedule
         * @return void
         */
        protected function schedule(Schedule $schedule): void
        {
            $schedule->php(script: 'subscriber_event.php')->daily();
        }

In addition to using the scheduler to run PHP scripts, you can also schedule [Codex](https://codefyphp.com/knowledgebase/codex/) 
commands, system commands, custom registered commands, and shell commands.

Scheduler Frequency Options
---------------------------

In the above example, the frequency is set to daily, but there are many more fluent frequency options to choose from.

| **Method**                            | **Description**                                                                       |
|---------------------------------------|---------------------------------------------------------------------------------------|
| `->cron('* * * * *');`                | Task will run based on a custom cron schedule.                                        |
| `->everyMinute();`                    | Task will run every minute.                                                           |
| `->hourly();`                         | Task will run every hour.                                                             |
| `->hourly(15);`                       | Take will run hourly at 15 minutes past the hour.                                     |
| `->every('hour', 5);`                 | Task will run every hour at 5 minutes past the hour.                                  |
| `->everyHour(4, 15);`                 | Task will run every 4 hours and 15 minutes.                                           |
| `->daily();`                          | Task will run every day at midnight.                                                  |
| `->daily('21');`                      | Task will run every day at 9 p.m.                                                     |
| `->on('2023-04-25');`                 | Task will run on a specific date.                                                     |
| `->dailyAt('10:00');`                 | Task will run daily at 10 a.m.                                                        |
| `->twiceDaily(10, 15);`               | Task will run twice daily, first at 10 a.m. then at 3 p.m.                            |
| `->weekdays('2');`                    | Task will run only on the weekdays at 2 a.m.                                          |
| `->weekends('2');`                    | Task will run only on weekends at 2 a.m.                                              |
| `->mondays('2');`                     | Task will only run on Mondays at 2 a.m.                                               |
| `->tuesdays('2');`                    | Task will only run on Tuesdays at 2 a.m.                                              |
| `->wednesdays('2');`                  | Task will only run on Wednesdays at 2 a.m.                                            |
| `->thursdays('2');`                   | Task will only run on Thursdays at 2 a.m.                                             |
| `->fridays('2');`                     | Task will only run on Fridays at 2 a.m.                                               |
| `->saturdays('2');`                   | Task will only run on Saturdays at 2 a.m.                                             |
| `->sundays('2');`                     | Task will only run on Sundays at 2 a.m.                                               |
| `->weekly();`                         | Task will run every Sunday at midnight.                                               |
| `->weeklyOn('4', '02:15');`           | Task will run every week on Thursday at 2:15 a.m.                                     |
| `->monthly();`                        | Task will run every month on the first day of the month at midnight                   |
| `->monthlyOn('4', '02:15');`          | Take will run every month on the first Thursday of the <br/> month at 2:15 a.m.       |
| `->lastDayOfTheMonth('02:15');`       | Task will run on the last day of the month at 2:15 a.m.                               |
| `->quarterly();`                      | Task will run every quarter, first day of the month at midnight.                      |
| `->quarterly('3', '02:15');`          | Task will run every quarter, on 3rd day of the quarter at 2:15 a.m.                   |
| `->quarterly(['3','15'], '02:15');`   | Task will run every quarter, on the 3rd and 15th day of <br/>the quarter at 2:15 a.m. |
| `->yearly();`                         | Task will run the first month, first day of the year at midnight.                     |
| `->yearly(7, 15, '02:15');`           | Task will run the 7th month, 15th day of the month at 2:15 a.m.                       |
| `->days(['0', '3']);`                 | Task will run every Sunday and Wednesday at midnight.                                 |
| `->between('01:00', '03:00');`        | Task will run every day between 1 and 3 a.m.                                          |
| `->unlessBetween('01:00', '03:00'`);  | Task will not run between 1 and 3 a.m.                                                |

You can also chain methods to create a more finely tuned schedule. This example shows a task running every day on 
weekdays every 4 hours:

    $schedule->php(script: 'subscriber_event.php')
        ->weekdays()
        ->daily()
        ->everyHour(4);

Literal Options
---------------

You can also use literals when using the `alias` method:

    /**
     * Other literals to use.
     * 
     * @always - every minute
     * @weekdays
     * @weekends
     * @quarterly
     * @sunday
     * @monday
     * @tuesday
     * @wednesday
     * @thursday
     * @friday
     * @saturday
     * @january
     * @february
     * @march
     * @april
     * @may
     * @june
     * @july
     * @august
     * @september
     * @october
     * @november
     * @december
     */
    
    $schedule->php(script: 'subscriber_event.php')->alias('@always');