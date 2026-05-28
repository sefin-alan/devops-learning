# Level 13-14: The password is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14

## Password
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
## Method
Secure copy the ssh key to localhost, change the permissions, ssh into bandit14 using ssh key and read the file
```
ls
file sshkey.private
scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private .
chmod 600 sshkey.private
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14
```
**What I learned:** SSH keys are an alternative method of logging in via the SSH program. In order to use them, it must have the correct file permissions; specifically, the file must not have group or global permissions of any kind. The localhost is your current machine.

The : used in the scp -P command is used to specify which file is being copied from e.g.sshkey.private, followed by where its being copied to i.e. the current directory (.). The 'i' option in the ssh command, is used to specify the key file.



