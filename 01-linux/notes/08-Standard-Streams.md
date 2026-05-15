# Standard Streams

## Key Concepts

There are 3 standard streams:
- **stdin** (standard input): provides input to a command, typically by typing on the keyboard or redirecting from a file using the redirect operator (<)
- **stdout** (standard output): the output of the commands that is displayed in the terminal
- **stderr** (standard error): used for sending error messages e.g. when a command fails or permission is denied
- [>] also overwrites the contents of a file,  while the append operator [>>] is used to **add** content

### File Descriptors

- stdin = 0 (< or 0<)
- stdout = 1 (> or 1>)
- stderr = 2 (2>)

Useful Tips: 
- use **&>** to redirect both stdout and stderr at the same time, this is useful for viewing where a command succeeded and where it failed
- **/dev/null** is essentially a black hole for output as anything that is redirected here is discarded, this is useful for supressing stdout, stderr or both that you don't need

### Practical Examples

**stdin and stdout**

echo "This is a test file" > input.txt'

cat < input.txt

- ["This is a test file" >] and [< input.txt] are the standard inputs
- [>] redirects **stdout** away from the terminal and into input.txt
- [<] redirects input.txt into cat via **stdin**

Important Note: Both [cat input.txt] and [cat < input.txt>] display the same output, but (<) means that the contents are being redirected into cat as opposed to it reading the file directly

**stderr**

ls example

ls: cannot access 'example': No such file or directory

ls example 2> error.txt

cat error.txt

ls: cannot access 'example': No such file or directory

- [ls: cannot access 'example': No such file or directory] is the stderr
- [2>] redirects stderr to error.txt

ls example my_directory_copy/ &> all_outputs.txt

cat all_outputs.txt

ls: cannot access 'example': No such file or directory

my_directory_copy:
hello.txt

- **[&>]** redirects both stderr (the error message) and stdout (the directory listing) into all_outputs.txt
- stdout: the contents of my_directory_copy/ were displayed (command succeeded)
- stderr: error message for ls example (command failed)