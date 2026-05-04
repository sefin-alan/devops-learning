# Shells and Programs

## Key Concepts

- Shells are command interpreters which take user input, determine how to execute it (built-in, binary, or script) and communciates this to the OS to run it
- Shells like Bash always interpret your input, but it only interprets program logic when the program is a script
- "echo $SHELL" displays the default login shell, "echo $PATH" displays the directories that the shell searches through for executables when you run a command

## Programs, Binaries, and Scripts
- A Program is any set of instructions
- A Binary is a compiled program that can be executed by the OS without needing an interpreter
- A Script is a program written in a text-based language that requires an interpreter so that it can be executed

## The Command Process

- When you run a command like ls, the shell looks through each directory listed in the Path environment variable to find the executable ls file
- Once it has been found, the shell asks the OS to execute that program, which then prints the directory contents. 
- ls is a **Binary** because it is a compiled exectuable file (/bin/ls), meaning that it already contains machine code instructions that can therefore be run by the OS without needing an interpreter

## Different Types of Shells

- Each Shell has its own features and capabilities, but they all serve the same fundamental purpose of being a means to interact with the OS

There are different types of shells such as: Bash, Fish, Zsh, Ksh, Csh/Tcsh. The main features of some are listed below:

**Bash:**

- Job Control
- Command Line Editing
- Shell Aliases and Functions
- Unlimited size command history
- Integer arithmetic with support for multiple number bases (2-64)

**Zsh:**

- Startup files
- Filename generation
- Login/Logout watching
- Concept Index
- Closing comments
- Variable and Key index

**Ksh:**

- Powerful Shell
- Complete scripting features
- Advanced scripting capabilities
- Used mainly in legacy UNIX systems

