# Level 28-29: There is a git repository at ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo via the port 2220. The password for the user bandit28-git is the same as for the user bandit28. From your local machine, clone the repository and find the password for the next level.

## Password
4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
## Method
The start of this level is the same as the previous level
```
cd repo
```

Read the README.md file
```
cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx
```

Listed the commit history to see if or when any changes were made to the README.md file
```
git log README.md

commit 00daa614aac60bd2981c381484191eb7bc4dcfd9 (HEAD -> master, origin/master, origin/HEAD, README.md)
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Apr 3 15:17:37 2026 +0000

    fix info leak

commit a1487fd098591dfa210ede70ba60f7093f47d20d
Author: Morla Porla <morla@overthewire.org>
Date:   Fri Apr 3 15:17:37 2026 +0000

    add missing data

commit eaef76e40b22863d8085130677ae53e13ae1a9c6
Author: Ben Dover <noone@overthewire.org>
Date:   Fri Apr 3 15:17:37 2026 +0000

    initial commit of README.md
```

The password is most likely in the second commit where 'missing data' was added, switch to this commit using its commit hash then read the file to view its content at that stage
```
git checkout a1487fd098591dfa210ede70ba60f7093f47d20d
HEAD is now at a1487fd add missing data
cat README.md
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7
```

**What I learned:** Using `git checkout` on a specific commit puts you in **detached HEAD** state, meaning that you're no longer on a branch, and `git log` will only show the commit history up to that commit. You can run `git checkout master` to get back to the full history. 

**Important Note**: `--` before a filename is important for ensuring that `git` treats the following input as a file.

`git log` has many useful options like:
- `--oneline` compacts the commit history into one-line view
- `-n 5` displays the last 5 commits
- `--graph` provides a visual branch/merge tree