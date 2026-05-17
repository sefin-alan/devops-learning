# Environment Variables and Aliases

## Key Concepts

- a **variable** is a named value that can be stored and reused
- an **environment variable** is a variable stored in the shell that holds information used by the system and commands
- a **[shell](/01-linux/notes/03-Shells-and-Programs.md)** is the environment in which variables are set and accessed

Some examples of Environment Variables are:

- $HOME: gives path of home directory
- $PATH: tells the system where to look for executable files
- $EDITOR: gives default file editor
- $HOSTNAME: gives name of the host
- $LANG: gives the default system language
- $PWD: gives the path of present working directory
- $UID: gives user ID of current user
- $USER: gives the username of the current user
- $SHELL - the shell program in use

## Setting Environment Variables

There are 2 ways of setting environment variables:

- **Temporary Setting**: 'export NAME = VALUE' temporarily sets environment variable in the current terminal session

**Example:** 

![alt text](../images/tempexportenv.png)
- [echo $HOME] accesses the the environment variable
- [export MY_VAR="Hello World"] sets the variable MY_VAR with the value "Hello World"
- [echo $MY_VAR] used to ensure it has been set

- **Permanent Setting**: adding 'export NAME = VALUE' into 'vim .bashrc or .zshrc' permanently sets environment variable so it loads automatically everytime the shell starts

**Example:**
- [vim .zshrc] accesses the configuration file
- [export MY_VAR="Hello World"] is added to a new line, then save and exit
- [source .zshrc] applies changes without restarting the terminal
- [echo $MY_VAR] used after restarting terminal, to ensure it has been set permanently

*Bashrc and Zshrc are configuration files located in the home directory containing configuration of specific shells.

![alt text](../images/zshrcbashrc.png)

## Adding to Environment Variables

- to add directories to existing environment variables e.g. $PATH, run [export PATH=$PATH:/home/ubuntu]
- any executable script in **/home/ubuntu** will be recognised as a program as $PATH is where the system looks for executables

**Example:**

![alt text](../images/add$PATH.png)

- [export PATH=$PATH] the PATH variable will be updated along with what it already contains ($PATH)
- [:/home/ubuntu] the colon signifies that the following directories will be added
- [echo $PATH] view the PATH environment variable to see that the change has been made

The system will now look for executables in the **/home/ubuntu** directories so it can run any executable script within it.

![alt text](../images/addscript.png)

- [vim greet.sh] creates and opens the greet.sh file
- [#!/bin/bash
'# A simple script to greet the user'
echo "Hello, $USER! Welcome to $HOSTNAME."] the script that was inserted into greet.sh
- [chmod +x greet.sh] grants execute permission to greet.sh, turning it into an executable file
- [./greet.sh] runs the executable file

## Aliases








