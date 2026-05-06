# Linux File System

## Key Concepts

![alt text](../images/ScreenshotLFS.png)
- bin directory contains essential binary executables like **[ls](02-Commands.md)**,**[pwd](02-Commands.md)**,sudo
- dev holds device files which represent devices attached to the system like discs and terminals
- etc contains system-wide integration files, user account info, and shell scripts which are used to boot and initialise the file system

## Creating and Updating Files

- **[touch](02-Commands.md)**' creates an empty file but if used on an existing file, it will update the timestamp for its creation which can be viewed by ls -l
- **[echo](02-Commands.md)** is used to display a **[string](#string)** that is passed as an **[argument](#argument)**
- echo "Hello World" just displays Hello World, but this output can be redirected to another file (e.g myfile.txt) using a > so in full, echo "Hello World" > myfile.txt which will generate or overwrite the first string with "Hello World in the respective file
- To add text to an existing file without overwriting the first line, you can use >> instead of > to add additional content, then verify that this has been done by using **[cat](02-Commands.md)** to read the contents of the file













## Definitions

### Argument 
Refers to what is passed into the command that you're running

### String
Refers to a line of text, "Hello World" was the string that was passed as an argument to echo
