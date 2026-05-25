# Level 9-10: The password is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters

## Password
FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey
## Method
Extract the readable text and filter for the lines containing =
```
strings data.txt | grep '='
```

**What I learned:**[strings data.txt] extracts only human-readable text and [grep '='] filters and prints the lines containing =

