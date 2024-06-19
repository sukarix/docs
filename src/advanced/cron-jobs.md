# CRON / Task Scheduling

<!-- toc -->

## TaskScheduler

`TaskScheduler` is an Action in Sukarix designed for task scheduling. The CLI toolbox installs it as a cron job by
default, utilizing the GO\Scheduler syntax.

## Default Configuration

The `route-cli.ini` file contains the default route for task scheduling:

```ini
[routes]
; route to the main task scheduler
GET @run_job : /cli/jobs/run [cli] = Actions\Jobs\TaskScheduler->execute
```

## Setting Up Cron

The default cron job should contain:

```sh
* * * * * /usr/bin/php /var/www/sukarix/public/index.php "/cli/jobs/run"
```

## Defining Jobs

Each job must be defined in `route-cli.ini`. For example, the default log cleaning job is implemented as:

```ini
GET @logs_clean : /cli/logs/clean [cli] = Sukarix\Actions\Logs\Clean->execute
```

## Implementing the Execute Function

The `execute` function should schedule tasks using the `scheduler`:

```php
public function execute() {
    // Clean old sessions every 8 hours at 10 minutes after the hour
    $this->scheduler->php($this->documentRoot, null, ['/cli/sessions/clean' => ''], 'sessions-clean')
                    ->onlyOne()
                    ->at('20 */8 * * *');
}
```

This example schedules a session cleaning task to run every 8 hours at 10 minutes past the hour, ensuring only one
instance runs at a time.