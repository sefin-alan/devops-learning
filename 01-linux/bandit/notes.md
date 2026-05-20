# Notes

### Level 0-1: The password is stored in a file called readme located in the home directory

- [cat readme] to read the file

### Level 1-2: The password is stored in a file called - located in the home directory

- [cat ./-] to read the file 

What I learned: ./ prefix ensures that the shell treats '-' as the name (can also 'cat' the complete path)

### Level 2-3: The password is stored in a file called --spaces in this filename-- located in the home directory

- [cat ./--"spaces in this filename--] to read the file

### Level 3-4: The password is stored in a hidden file in the **inhere** directory

- [cd inhere] -> [ls -a] to list the hidden file, hidden filename was "...Hiding-From-You" -> [cat ...Hiding-From-You]

### Level 4-5: The password is stored in the only human-readable file in the **inhere** directory

- [cd inhere] -> [file./*] -> -file07 is the only text file -> [cat ./-file07]

What I learned: [file ./*](../notes/02-Commands.md) lists every file type in the directory

### Level 5-6: The password is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable, 1033 bytes in size, not executable

- [cd inhere] -> [[find](../notes/02-Commands.md) . -readable -size 1033c ! -executable] -> [/maybehere07/.file2] was the only file that matched the specified properties -> [cat maybehere07/.file2]

What I learned: The '.' after 'find' specifies the current directory, the 'c' after 1033 represents bytes, and  '!' reverses the next condition so instead of printing executable files using '-executable', '! -executable' will find the non-executables

### Level 6-7: The password is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size

- [find / -size 33c -user bandit7 - group bandit6 2>/dev/null] [/var/lib/dpkg/info/bandit7.password] was the only file left -> [cat /var/lib/dpkg/info/bandit7.password]

What I learned: The find command printed all the files with the specified properties but there were a lot of error messages so added [2>/dev/null] to clear output ->

### Level 7-8: The password is stored in the file data.txt next to the word millionth

- [grep "millionth" data.txt]

### Level 8-9: The password is stored in the file data.txt and is the only line of text that occurs only once

- [sort data.txt | uniq -u]

What I learned: [[sort] data.txt](../notes/02-Commands.md) sorts all the lines into alphabetical order, grouping identical lines together -> [uniq] filters out duplicate lines -> [-u] option only prints lines that appear once

### Level 9-10: The password is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters

- [strings data.txt | grep '=']

What I learned: [strings data.txt] extracts only human-readable text and [grep '='] filters and prints the lines containing =

### Level 10-11: The password is stored in the file data.txt, which contains base64 encoded data

- [base64 -d data.txt] 

What I learned: '-d' option decodes data

### Level 11-12: The password is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

- [cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'] 'a-zA-Z' is SET1 which are the characters to translate from, 'n-za-mN-ZA-M' is SET2 which are the characters to translate 

What I learned: The ROT13 cipher, so 'a' is mapped to 'n', 'b' is mapped to 'o' and so on, this is why SET2 starts with 'n' and goes to 'z' then back around to 'a-m' to complete the second half of the alphabet

### Level 12-13: The password is stored in the file data.txt, which is a **hexdump** of a file that has been repeatedly compressed

- [mktemp -d] -> [cp data.txt /tmp/tmp.9mXQpTeqeO] -> [cd /tmp/tmp.9mXQpTeqeO] -> [cat data.txt | [**xxd -r**](../notes/02-Commands.md) tempdata.txt] outputs into newly created file named 'tempdata.txt' -> [file tempdata.txt] printed file type [tempdata.txt: gzip compressed data] -> [**mv** tempdata.txt tempdata.txt.gz] -> [[**gzip -d**](../notes/02-Commands.md) tempdata.txt.gz] -> [tempdata.txt] -> [file tempdata.txt] (this process 'file, mv rename to filetype, filetype -d or tar -xf' is followed until file has been fully decompressed)

What I learned: Files have to be renamed to reflect their filetype before extracting them with that filetype's extraction option i.e. gzip -d extracts '.gz.' file. When extracting gzip and bzip2 the file is **replaced** by the extracted output, but with tar, the contents are extracted **alongside** the original archive, so a new file/s will appear next to it. A **hexdump** is a representation of a file's binary data displayed in hexadecimal format that is used to inspect raw file content.