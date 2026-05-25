# Level 6-7: The password is stored somewhere on the server and has all of the following properties: owned by user bandit7, owned by group bandit6, 33 bytes in size

## Password
morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj
## Method
Use the 'find' command to locate the file and clear the stderr, then read the file
```
find / -size 33c -user bandit7 - group bandit6 2>/dev/null 
cat /var/lib/dpkg/info/bandit7.password
```

**What I learned:** The find command printed all the files with the specified properties but there were a lot of error messages so added [2>/dev/null] to clear output ->