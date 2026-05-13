# Commands

## Navigation
| Command | What it does |
|---------|-------------|
| ls | list files |
| ls -a | list hidden files |
| ls -R | view full nested directory structure |
| pwd | show current location |
| cd | navigate directories |
| cd ~ | shortcut to home directory |

## File Management
| Command | What it does |
|---------|-------------|
| cp | copy a file |
| cp -r| copy a directory |
| rm | remove a file |
| rmdir | remove empty directory |
| touch | create empty file/update timestamp |
| mkdir | create a directory |
| mkdir -p | creates a nested directory |
| head | displays first 10 lines of a file |
| tail | displays last 10 lines of a file|
| echo | displays a line of text/create a file |
| mv | move/rename a file |
| cat | read/create/combine/copy files |
| grep | search for specific pattern in a file |

## VIM

| Command | What it does |
|---------|-------------|
| :q | quits file |
| :wq | saves and quits file |
| 0 | moves to the beginning of a line |
| $ | moves to the end of a line |
| w | moves up by word |
| b | moves back by word |
| :linenumber | moves to specified line |
| /word | moves to specified word |
| n N | moves up and down each occurence of the specified word |
| :set number :set nonumber | enable and disable line number visibility |
| y | copies line |
| p | pastes line |
| dd | deletes a whole line |
| D | deletes from cursor to end of line |
| u | undo last change and view when it was made |
| Ctrl + R | redo last change |
| syntax on | enables highlighting of commands and keywords |


## Users and Permissions
| Command | What it does |
|---------|-------------|
| ls -l | list files with user permissions and timestamp |
| sudo | Run a single command with admin privileges |
| sudo su | Run multiple commands with admin privileges |
| whoami | view your current user |
| exit | return to normal user |
| sudo useradd username | adds a new user with specified username |
| sudo passwd username | sets password for new user |
| su - username | switch to specified user |
| sudo usermod -aG sudo username | grant user sudo access |
| sudo deluser newuser sudo | remove user sudo access |
| sudo groupadd groupname | create new group |
| sudo groupdel groupname | delete specified group |
| sudo gpasswd -d username groupname | remove user from specified group |
| chmod | change the permissions of a file or directory |
| chown username filename| change the owner of file or directory |
| chgrp groupname filename | change the group of a file or directory|
| chown username:groupname | change the owner and group of a file or directory|
| chown -R | change the owner and group of a file or directory as well as its contents |
