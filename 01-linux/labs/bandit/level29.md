# Level 29-30: There is a git repository at ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo via the port 2220. The password for the user bandit29-git is the same as for the user bandit29. From your local machine, clone the repository and find the password for the next level.

## Password
qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
## Method
The start of this level is the same as the previous two levels
```
# Bandit Notes
Some notes for level30 of bandit.

## credentials

- username: bandit29
- password: <no passwords in production>
```

Checked the commit history of README.md to see if any changes were made
```
git log README.md

commit ccda64bae05a06bd418b662bfe9b72ef3d839d78 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Fri Apr 3 15:17:38 2026 +0000

    fix username

commit d12b10ac12b5e1a2482190bd384d5f6943b83578
Author: Ben Dover <noone@overthewire.org>
Date:   Fri Apr 3 15:17:38 2026 +0000

    initial commit of README.md
```
This only showed the commit history for the [master branch](#what-i-learned) because that's the default branch that I'm on, as indicated by `HEAD ->`

Viewed the commit history of all branches in compact view
```
git log --all --oneline

ccda64b (origin/master, origin/HEAD, master) fix username
4a8f414 (HEAD, origin/dev) add data needed for development
8335f3d (origin/sploits-dev) add some silly exploit, just for shit and giggles
d12b10a initial commit of README.md
e401587 add gif2ascii
```

Password is most likely in "add data needed for development", switch to its branch and view the README.md contents.
```
git checkout 4a8f414
cat README.md

# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL
```

### What I learned:
The top commit (ccda64b) had these 3 branch labels (master,origin/master,origin/HEAD) because they are all currently in sync. The labels for the commits lower in the history like origin/splots-dev and HEAD,origin/dev are behind **master** meaning that those versions have not got the 'fix username' and 'add data needed for development' changes which is why they were less likely to have the password for the level.
Branch Labels:
`master` - the main/default local branch
`origin/master` - the remote copy of master (on github) 
`origin/HEAD` - the default branch on the remote server
`origin/dev` and `origin/sploits-dev` - separate branches

The commits without a branch label are commits that no branch label is currently pointing at. They are essentially shared ancestors that **all** branches grew from but they aren't being pointed at because the other branch tips have moved forward to the newer commits.

When `git log --all` displays commits, it only shows the branch label at the most recent commit of each branch.