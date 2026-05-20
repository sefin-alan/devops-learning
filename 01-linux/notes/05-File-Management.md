# File Management

## Key Concepts

- The 3 essential commands for managing files are: **cp**, **mv**, **rm**, which allow you to copy, move, remove files or directories respectively
- You can create nested directories with [mkdir -p](02-Commands.md) and view them all recursively with [ls -R](02-Commands.md)
- 'rmdir' can only remove an empty directory, [rm -r](../notes/02-Commands.md) removes a directory and its contents

### Practical Examples

[**cp**](../notes/02-Commands.md)

[cp file.txt backup.txt] copies file contents of file.txt to backup.txt
[cp file.txt my_directory] copies file contents of file.txt to my_directory

[**mv**](../notes/02-Commands.md)

[mv file.txt newname.txt] renames file.txt to newname.txt
[mv file.txt my_directory] moves file.txt to my_directory

[**rm**](../notes/02-Commands.md)

[rm file.txt] deletes file.txt
[rm -r my_directory] deletes my_directory and its contents

[**mkdir -p**](../notes/02-Commands.md)

[mkdir -p project/src/components] creates a **[nested directory](#nested-directory)**. 'project' contains '/src/' contains contains '/components' so it cannot be deleted with rm since it is not an empty directory. **'ls -R'** can be used to view this directory structure in its entirety, and **'rm -r'** will remove the whole structure. **'rmdir'** could be used to remove '/components' alone as it is an empty directory.

## Dealing with Spaces in Folder Names

- To create a directory with a space in its name e.g. "My Project", the name must be either encapsulated in speech marks, or have the words be separated with a backslash ( \ )
- As a command, it would look like this: 'mkdir "My Project"' or 'mkdir My\ Project\ 2'
- This same concept applies when navigating to such a directory

## Definitions

### Nested Directory
Refers to when there are directories within directories e.g. devops-learning/01-linux/notes