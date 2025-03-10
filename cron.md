Cron is time based job scheduler in Unix like systems. Cron allows the user to schedule programs to run on intervals. Cron jobs are programmed by adding them to the [[#crontab]]. Errors in cron are logged via email with sendmail or by using the `-m` option to log it to a file.

# crontab

crontab is the job table for cron. It works by allowing you to edit, add and remove jobs from the table. Additionally, it checks syntax before adding jobs to the table. Files are usually located in `/var/spool/cron` but shouldn't be edited directly. A system wide crontab is available at `/etc/cron`.

## Syntax

```crontab
minute hour day_of_month month day_of_week command
```

To fine-tune your schedule you may use one of the following symbols:

| Symbol | Description          |
| ------ | -------------------- |
| \*     | Wildcard             |
| ,      | list multiple values |
| -      | range                |
| \*/n   | periodicity          |

Additionally, crontab can use special keywords:

- @reboot
- @yearly
- @annually
- @monthly
- @weekly
- @daily
- @midnight
- @hourly

## crontab commands

```bash
# View your crontab.
crontab -l
# Edit your crontab.
crontab -e
# Remove your crontab.
crontab -r
# Overwrite crontab.
crontab filename
# Overwrite crontab from stdin.
crontab -
# Act as another user.
crontab -u username <-e|-r|-l>
```



