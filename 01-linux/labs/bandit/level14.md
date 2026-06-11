# Level 14-15: The password can be retrieved by submitting the password of the current level to port 30000 on localhost

## Password
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
## Method
Use nc (netcat) to send the password to port 30000
```
nc localhost 30000
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
```

**What I learned:** 'nc' is used to connect to and communicate with a specific IP address and port, to send and recieve data over a network connection i.e. 'nc localhost 30000' connects to the current machine (localhost), on port 30000. The Bandit server had a service listening on port 30000 on localhost; this service was programmed to recieve the current level's password and return the next one.