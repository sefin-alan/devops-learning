# Users and Permissions

## Key Concepts

- Every file and directory has permissions that control who can read,write or execute it
- A "Permission Denied" error may cccur when you try to write to a location you don't have access to. (Navigate to home directory with cd ~ where you have full write permissions)
- You can also use [ls -l](02-Commands.md) to view permissions where you may see -rwxr-xr-- which shows what each user type is allowed to do

## The 'sudo' Command

- The ['sudo' command](02-Commands.md), meaning superuser do. provides elevated privileges to a **permitted** user
- 'sudo !! tab' is a shortcut that uploads the previous command 
- Editing system files also require superuser privileges e.g. Using 'vim etc/hosts' won't allow editing or saving, warnings will occur stating that the file is a 'readonly'; using 'sudo vim etc/hosts' will allow you to make these changes
- sudo ls /root lists the contents of the root directory and can only be read by those with sudo permission

## The Root User

- 'sudo su' switches you to the root user altogether, use 'whoami' to view your current user
- The '#' at the end of your username also shows that you are the root user, use ['exit'](02-Commands.md) to return to normal user
- rm -rf / delete
- All sudo commands you have used are logged in `/var/log/auth.log', run 'sudo tail /var/log/auth.log' to see recent activity

## Users

- New users can be added with 'sudo useradd' and set with their own passwords using 'sudo passwd', you can switch to them with 'su' meaning substitute user

Practical Example: 'sudo useradd newuser, sudo passwd newuser, su - newuser
(newuser is the example username)

- a warning may occur when switching to the new user immediately after creating it, this is because the directory for it does not exist, use 'whoami' to ensure you are in the new user
### Granting and Revoking 'sudo' Access

- to grant this new user sudo privileges, run 'sudo usermod -aG sudo newuser' in your normal user who is already in the sudo group
- to remove sudo privileges from this user, run 'sudo deluser newuser sudo' in your normal user



