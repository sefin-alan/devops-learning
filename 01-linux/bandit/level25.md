# Level 25-25: Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

## Password
s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ
## Method
Find the shell for user bandit26, switch back to /bin/bash shell
```
cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```
- This output has been broken down [here](#what-i-learned)

Inspected the shell script file
```
cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```
- export TERM=linux is setting an evironment variable, TERM defines the terminal type
- `more` allows you to read the contents of a large text file one screenful at a time i.e. it is displaying '~/text.txt' which is a large 'bandit26' icon, `less` is similar to `more` but has more features e.g. allows you to scroll both forwards and backwards through a file whereas `more` only goes forwards
- exit 0 is what is causing you to be kicked out of bandit26 immediately upon login

- It's possible to break out of the `more` command and go into vim if whatever is being read, is larger than what can fit on the screen
- You can minimise the screen so that the text is too large to fit on the screen, causing `more` to pause and partially load whatever is able to fit on the screen
- From there, vim commands become available e.g. :set shell? - to see the current shell, :set shell=/bin/bash - to set the shell to bash, :shell - to open a sub-shell

I exited and copied the sshkey for bandit26 to my home directory so that I can `ssh` into bandit26 from my local terminal; as bandit does not allow you to login from one bandit user straight to another bandit user

```
exit
scp -P 2220 bandit25@bandit.labs.overthewire.org:~/bandit26.sshkey ~/
```
- scp uses -P while ssh uses lowercase -p when specifying the port
- You first specify the file that will be copied i.e. ~/bandit26.sshkey, then the destination ~/ (my home directory).
- [~/] is a shortcut for the home directory, the full path can also be used.

Used the private key to login to bandit26 via default user
```
ssh -i bandit26@bandit.labs.overthewire.org -p 2220
```
- Before hitting enter, I minimised the screen so that `more` would be forced to freeze
- This is because it would only be able to partially load the text file relative to the size of the screen
- I am still able to maximise the screen while it's in this frozen state, which looks like this:

![alt text](../images/morefreeze.png)


From here, I hit 'v' to open `vim` from within `more` and then ran these `vim` commands in this order:
Set the shell to Bash, changing it from showtext
```
:set shell=/bin/bash
```

Displayed the current shell to ensure the change was made, which displayed `shell=/usr/bin/bash` meaning that the change was successful
```
:set shell?
```

Opened a sub-shell within vim which is now a Bash sub-shell.
```
:shell
```


I'm now able to interact with the filesystem as I'm now using an interactive shell (Bash) as opposed to showtext which was just a script with no ability to accept or process commands; and since I logged in as bandit26 in the beginning via `ssh -i`, I am interacting with the filesystem as bandit26 so I can now read the password file
```
cat /etc/bandit_pass/bandit26
```

### What I learned:

`cat /etc/passwd` can be used to view user and group info. In this level, it displayed the following:
```
[bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext]  
```
- bandit26 is the username
- x is where passwords used to be, the x indicates that the password is stored in the /etc/shadow file which is where passwords are now typically stored (/etc/shadow is only readable by root, which is why passwords were moved to there from /etc/passwd, which is readable by everyone)
- 11026 is the user numerical id, followed by the group numerical id
- bandit level 26 is a comment field
- /home/bandit26 is the home folder for that particular user
- /usr/bin/showtext is the **shell**

(Every time you login, a shell is started based on what's configured in /etc/passwd for that user. This is normally a standard shell like /bin/bash or /bin/zsh but in this level, bandit26 has been set to a custom shell (showtext)).