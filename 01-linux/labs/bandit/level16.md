# Level 16-17: The password can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000

## Password
RSA Private Key
## Method
Scan ports in the range 31000 to 32000 to see which are open and speak SSL/TLS, submit password into the appropriate port, receive rsa private key and copy its contents, exit then create key file and paste contents into it, change permissions so that ssh program accepts the file, ssh -i into bandit17 with said file
```
nmap -p 31000-32000 -T4 -sV
echo 'kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx' | openssl s_client -connect -quiet localhost:31790
```
- Received RSA Private Key and exited
- Created privatekey.pem file and pasted RSA key contents into it via 'vim'
```
ls-l privatekey.pem
chmod 600 privatekey.pem
ssh -i privatekey.pem bandit14@bandit.labs.overthewire.org -p 2220
```



