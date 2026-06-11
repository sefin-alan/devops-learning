# Level 32-33: After all this git stuff, it’s time for another escape. Good luck!

## Password
tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0
## Method
Attempted to list the contents of the directory including hidden files
```
>> ls -la
sh: 1: LS: Permission denied
$SHELL

WELCOME TO THE UPPERCASE SHELL
```
- Every command I attempted was being converted into upppercase, so I used `$SHELL` and found that this was due to this custom "UPPERCASE SHELL" being used
- However, `sh:` shows that there is an underlying shell beneath uppercase shell as that is the one printing the error
- Numerical/symbolic commands won't be affected by the forced conversion into uppercase character

Used `$0` to bypass the uppercase program and launch the default shell
```
>> $0
$ cat /etc/bandit_pass/bandit33
```

**What I learned:** Multiple shells can run on top of eachother; this was the case in this level where the uppercase shell was above /bin/sh, intercepting the commands and converting them into uppercase characters before passing them down to /bin/sh to execute. `$0` expands to the path/name of the currently executing shell so running `$0` spawned a new /bin/sh session directly, bypassing the uppercase shell which is why commands weren't being turned into uppercase characters anymore. This switch to the direct /bin/sh session is indicated by the change in shell prompt from the uppercase shell (>>) to the default prompt for /bin/sh ($). 