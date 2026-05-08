# File Management

## Key Concepts

- The 3 essential commands for managing files are: [cp](02-Commands.md), [mv](02-Commands.md), [rm](02-Commands.md), which allow you to copy, move, remove files or directories respectively
- You can create nested directories with [mkdir -p](02-Commands.md) and view them all recursively with [ls -R](02-Commands.md)
- 'rmdir' can only remove an empty directory, 'rm -r' removes a directory and its contents

### Practical Example

'mkdir -p project/src/components' will create a **[nested directory](#nested-directory)**. As 'project' contains '/src/' which contains '/components', it cannot be deleted with rm since it is not an empty directory. ls -R can be used to view this directory structure in its entirety, and 'rm -r' will remove the whole structure. 'rmdir' could be used to remove '/components'alone as it is an empty directory.

## Definition

### Nested Directory
Refers to when there are directories within directories e.g. devops-learning/01-linux/notes