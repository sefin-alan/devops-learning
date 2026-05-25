# Level 13-14: The password is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14

## Password
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
## Method
Use the SSH private key to login to the next level
```
scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private .
chmod 600 sshkey.private
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14
```
