# Level 15-16: The password can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption

## Password
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
## Method
Input password of current level to port 30001 using SSL/TLS encryption
```
echo '8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo' | openssl s_client -quiet -connect localhost:30001
```

**What I learned:** SSL/TLS are both networking protocols which enable devices to communicate using an ecrypted connection. They are usually used with other protocols e.g. HTTPS which allows for encrypted webpage communication (useful for keeping banking details and passwords from going across the network in clear text).

openssl s_client -connect is essentially like using nc but for a service that requires SSL/TLS encryption. The -quiet flag supresses the SSL certificat information so that you can see the response first.