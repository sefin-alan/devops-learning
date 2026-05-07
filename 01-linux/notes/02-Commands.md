# Commands

- ls -F: Lists files with indicators (/ for directories) to easily distinguish between files and folders

- ls -a: Lists all files, including hidden 'dotfiles'

- ls -l: Displays user permissions and timestamp for the creation of a file or directory

- mkdir: Creates a new directory, so mkdir hello would create the folder "hello"

- rmdir: Removes a directory. so rmdir hello would remove the folder "hello" (rmdir only applies to directories, **rm** would be used for a file)

- touch: Creates an empty file, so touch hello.txt would create the hello.txt file, can also update timestamp of existing file

- cat: Primarily used to read contents of a file but can also be used to create a new file, combine files into a new file, and copy the contents of one file into another file using '>> (filename)'

- mv: Used to move or rename files

- grep: Used to search for specific pattern/content of text within a file, highlights the pattern you request e.g. grep "hello" file.txt, highlights "hello" only.

- sudo: Runs a single command with admin privileges, normal permissions resume for the next command

- echo: Displays a line of text, can also create a file by giving it a file name that does not already exist

- head: Displays first 10 strings of a file - tail: Displays last 10 string of a file

- cp: Copies a file or directory

- rm: Removes a file