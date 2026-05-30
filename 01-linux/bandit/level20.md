# Level 20-21: There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level. If the password is correct, it will transmit the next password.

## Password
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
## Method
Set up a listener on a localhost port with the password ready to send and run this process in the background
```
echo '0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO' | nc -nlvp 1234 &
```
Then use the setuid binary to access the listener port
```
./suconnect 1234
```

**What I learned:**
- The '-l' flag puts nc into listen mode, so it waits for an incoming connection 
- The '-v' flag means verbose, so it shows more details of what's happening in the terminal
- The '-p' flag in specifies the port number i.e. the port that will be listened to
- The '&' operator allows a process to run in the background i.e. nc ran in the background so that I could run ./suconnect at the same time instead of the terminal being stuck inside nc waiting for a connection