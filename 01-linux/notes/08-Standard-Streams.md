# Standard Streams

## Key Concepts

There are 3 standard streams:
- stdin (standard input): provides input to a command, typically by typing on the keyboard or redirecting from a file using the redirect operator (<)
- stdout (standard output): the output of the commands that is displayed in the terminal
- stderr (standard error): used for sending error messages e.g. when a command fails or permission is denied

### Practical Examples

**Standard Input**

echo "This is a test file" > input.txt'
cat < input.txt

- ["This is a test file" >] and [< input.txt] are the standard inputs
- [>] redirects **stdout** to input.txt
- [<] redirects input.txt into cat via **stdin**

Important Note: Both [cat input.txt] and [cat < input.txt>] display the same output, but (<) means that the contents are being redirected into cat as opposed to it reading the file directly