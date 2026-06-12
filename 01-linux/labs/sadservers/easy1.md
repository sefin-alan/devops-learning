# Scenario: "Saint John"- what is writing to this log file?

## Description: A developer created a testing program that is continuously writing to a log file /var/log/bad.log and filling up disk. You can check for example with tail -f /var/log/bad.log. This program is no longer needed. Find it and terminate it. Do not delete the log file

### Method
Find the PID (process ID) for the program that is writing to /var/log/bad.log
```
ps -axu | grep bad

admin        589  0.0  1.7  12508  8288 ?        S    00:13   0:00 /usr/bin/python3 /home/admin/badlog.py
admin        705  0.0  0.1   5264   640 pts/1    S<+  00:15   0:00 grep bad
```
There is only one process writing to badlog.py

Terminate the process using its PID
```
kill -9 589
```

**What I learned:** `ps -axu` lists every process in the system and `kill` with the `-9` option **forcefully** terminates a process by sending the **SIGKILL** signal which cannot be caught, blocked, or ignored by the target process, ensuring immediate termination.