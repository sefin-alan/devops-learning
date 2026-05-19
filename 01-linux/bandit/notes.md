# Notes

### Level 0-1: The password is stored in a file called readme located in the home directory

- [cat readme] to read the file

### Level 1-2: The password is stored in a file called - located in the home directory

- [cat ./-] to read the file, ./ prefix ensures that the shell treats '-' as the name (can also 'cat' the complete path)

### Level 2-3: The password is stored in a file called --spaces in this filename-- located in the home directory

- [cat ./--"spaces in this filename--] to read the file

### Level 3-4: The password is stored in a hidden file in the **inhere** directory

- [cd inhere] -> [ls -a] to list the hidden file, hidden filename was "...Hiding-From-You" -> [cat ...Hiding-From-You]

### Level 4-5: The password is stored in the only human-readable file in the **inhere** directory

- [cd inhere] -> [file ./*](../notes/02-Commands.md) lists every file type in the directory -> -file07 is the only text file -> [cat ./-file07]

### Level 5-6: The password is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable, 1033 bytes in size, not executable

- [cd inhere] -> [[find](../notes/02-Commands.md) . -readable -size 1033c ! -executable] the '.' after 'find' specifies the current directory, the 'c' after 1033 represents bytes, and  '!' reverses the next condition so instead of printing executable files using '-executable', '! -executable' will find the non-executables -> [/maybehere07/.file2] was the only file that matched the required properties -> [cat maybehere07/.file2]

### Level 6-7: The password is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size

- [find / -size 33c -user bandit7 - group bandit6] printed all the files with these properties but there were a lot of error messages so added [2>/dev/null] to clear output -> [/var/lib/dpkg/info/bandit7.password] was the only file left -> [cat /var/lib/dpkg/info/bandit7.password]

### Level 7-8: The password is stored in the file data.txt next to the word millionth

- [grep "millionth" data.txt]

### Level 8-9: The password is stored in the file data.txt and is the only line of text that occurs only once

- [sort data.txt | uniq -u] -> [[sort] data.txt](../notes/02-Commands.md) sorts all the lines into alphabetical order, grouping identical lines together -> [uniq] filters out duplicate lines -> [-u] option only prints lines that appear once

### Level 9-10: The password is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters

- [strings data.txt | grep '='] -> [strings data.txt] extracts only human-readable text -> [grep '='] filters and prints the lines containing =

### Level 10-11: The password is stored in the file data.txt, which contains base64 encoded data

- 