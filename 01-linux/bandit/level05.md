# Level 5-6: The password is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable, 1033 bytes in size, not executable

## Password
HWasnPhtq9AVKe0dmk45nxy20cvUa6EG
## Method
Use the 'find' command to locate the file, then read it
```
cd inhere
find . -readable -size 1033c ! -executable
cat maybehere07/.file2
```

**What I learned:** The '.' after 'find' specifies the current directory, the 'c' after 1033 represents bytes, and  '!' reverses the next condition so instead of printing executable files using '-executable', '! -executable' will find the non-executablesZ