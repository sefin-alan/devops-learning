# Level 18-19: The password is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

## Password
cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8
## Method
Run ssh with an argument to read the password file as soon as you login
```
ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat readme"
```

**What I learned:** Passing a command directly into ssh bypasses the interactive shell which is why the logout was not triggered. This concept is used a lot in DevOps for running remote commands on servers.