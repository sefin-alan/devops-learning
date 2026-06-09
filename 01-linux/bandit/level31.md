# Level 31-32: There is a git repository at ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30. From your local machine, clone the repository and find the password for the next level.

## Password
3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K
## Method
The start of this level is the same as the previous four levels
```
cat README.md

This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

Created key.txt and added requested content to within repo, then pushed it to the remote repo
```
echo 'May I come in?' > key.txt

git stage key.txt
hint: use -f if you really want to add them
```
There was something preventing the key.txt file from being staged

Viewed all files including hidden ones
```
ls -a
. .. .git .gitignore key.txt README.txt

cat .gitignore
*.txt
```
The .gitignore file is essentially telling git to ignore **any** (represented by *) .txt files which is why `git stage` wasn't working as it should

Forced the file to be staged
```
git stage -f key.txt
git commit -m "Added question to key.txt"

[master 2e2a6ae] Added question to key.txt
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt

git push
```

**What I learned:** `git stage` is interchangeable with `git add`. The `-f` flag was used to force the file into the staging area as the .gitignore file was preventing any text files or '*.txt' from being staged. '.gitignore' files are useful in real projects for files that you don't want to be pushed to a repo, e.g. password or config files containing sensitive information or log files that change constantly and aren't useful to track