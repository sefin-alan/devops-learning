# Level 26-27: Following on from the previous level, grab the password for bandit27!

## Password
upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB
## Method
Carrying on from the previous level, while in the sub-shell within `vim`, find the password for bandit27


Use `ls` to list the contents of bandit26 home directory
```
ls
bandit27-do text.txt
```

Find what type of file 'bandit27-do' is
```
file bandit27-do
```
- It's a setuid, meaning that it can be used to run an executable with the owner's privileges
- Refer back to [level 19](level19.md)

Use the setuid to read the password file for bandit27, as bandit27 is the owner

```
./bandit27-do cat /etc/bandit_pass/bandit27
```
