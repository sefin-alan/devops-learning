# Notes

### Level 0-1: The password is stored in a file called readme located in the home directory

- ran [cat readme] to read the file

### Level 1-2: The password is stored in a file called - located in the home directory

- ran [cat ./-] to read the file, ./ prefix ensures that the shell treats '-' as the name (can also 'cat' the complete path)

### Level 2-3: The password is stored in a file called --spaces in this filename-- located in the home directory

- ran [cat ./--"spaces in this filename--] to read the file

### Level 3-4: The password is stored in a hidden file in the **inhere** directory

- ran [cd inhere] followed by [ls -a] to list the hidden file, hidden filename was "...Hiding-From-You" so ran [cat ...Hiding-From-You]

### Level 4-5: The password is stored in the only human-readable file in the **inhere** directory

- [cd inhere] -> [file ./*] lists every file type in the directory -> -file07 is the only text file -> [cat ./-file07]

### The password is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable, 1033 bytes in size, not executable
