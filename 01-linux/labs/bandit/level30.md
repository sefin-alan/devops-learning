# Level 30-31: There is a git repository at ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo via the port 2220. The password for the user bandit30-git is the same as for the user bandit30. From your local machine, clone the repository and find the password for the next level.

## Password
fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
## Method
This level starts similar to the previous three levels
```
cat README.md
just an epmty file... muahaha
```

Viewed the commit history to see if any changes were made
```
git log --all --oneline

e761c5d (HEAD, origin/master, origin/HEAD, master) initial commit of README.md
```
Used `--all` option to view commit history of **all** branches - only master branch which is the current one so password must be within something else

Checked for [tags](#password)
```
git tag

secret
```

View what the tag contains
```
git show secret

fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy
```

### What I learned:
Tags are essentially notes attached to any specific commit in a repo; they are permanently fixed to that commit. They can also store their own messages and content so are typically used to mark important points like software release versions. Think of them as a sticky note attached to a page in a book, where that page is the commit. 

- `git tag` is used to list all tags in a repo
- `git show` shows the content of a specific tag



