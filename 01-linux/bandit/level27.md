# Level 27-28: There is a git repository at ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo via the port 2220. The password for the user bandit27-git is the same as for the user bandit27. From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

## Password
Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
## Method
Ensure git is installed locally, clone the repository to local machine, find the password inside it

Check if git has been installed, `git version` also works
```
git --version
git version 2.43.0
```

`git clone` the ssh remote repo url with the port number included, otherwise it will default to port 22 which is not open
```
git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
Cloning into 'repo'...
```

Viewed contents of current directory and verified that 'repo' has been cloned to it
```
ls
my_directory greet.sh repo
cd repo
cat README
The password to the next level is: Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN
```

**What I learned:** To specify the port number, use : after the url