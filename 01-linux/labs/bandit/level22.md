# Level 22-23: A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed

## Password
0Zf11ioIjMVN551jX3CmStKLYqjk54Ga
## Method
This level starts similarly to the previous level
```
cat /usr/bin/cronjob_bandit23.sh
```
Copied the script into the terminal
```
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```
The output of whoami is piped through **md5sum** to generate a unique hash, which becomes the filename in /tmp/ where the password is

Replicated the script so that bandit23 is output as the username instead of my current user(bandit22), to reveal the password file location for bandit23 in /tmp/
```
#!/bin/bash

myname=$(echo bandit23)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```
The script then returned the below
```
Copying passwordfile /etc/bandit_pass/bandit23 to /tmp/8ca319486bfbbc3663ea0fbe81326349
```
So all that is left is to read the file
```
/tmp/8ca319486bfbbc3663ea0fbe81326349
```

**What I learned**: **md5sum** takes an input and generates a unique hash from it; the script then used this in 'cat /etc/bandit_pass/$myname > /tmp/$mytarget' to create a unique filename '/tmp/'.

**md5sum** outputs the hash and a filename or - after the hash, **'cut'** was used to extract just the hash. The **'-d' option** (delimiter) with ' ' as the argument, splits the output at every space. **'-f 1'** specifies field 1, meaning everything before the first space. This meant that it only grabbed 8ca319486bfbbc3663ea0fbe81326349 which became the filename in /tmp/