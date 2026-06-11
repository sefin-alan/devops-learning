# Level 21-22: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Password
tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q
## Method
List the cron.d directory's contents
```
ls -la /etc/cron.d/
```
Read the cronjob for bandit22
```
cat /etc/cron.d/cronjob_bandit22
```
Read the script that's being run
```
cat /usr/bin/cronjob_bandit22.sh
```
This script makes a file in the /tmp directory readable by all users, then copies the password for the bandit22 user into it
```
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```