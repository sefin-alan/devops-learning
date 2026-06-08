# Level 19-20: The password can be found in /etc/bandit_pass, after you have used the setuid binary.

## Password
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
## Method
Use the SUID which runs as the bandit20 user, to temporarily gain read permission for the password file
```
./bandit20-do cat /etc/bandit_pass/bandit20
```

**What I learned:** A 'setuid' allows users to run an executable with the permissions of the owner. The setuid binary will have an 's' in the file permissions.