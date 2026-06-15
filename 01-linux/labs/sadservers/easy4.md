# "Taipei": Come a-knocking

## Description: There is a web server on port :80 protected with Port Knocking. Find the one "knock" needed (sending a SYN to a single port, not a sequence) so you can `curl localhost`

## Method
Confirmed port 80 was closed
```
curl localhost

curl: (7) Failed to connect to localhost port 80: Connection refused
```

Scan for open ports on localhost
```
nmap localhost

Starting Nmap 7.80 ( https://nmap.org )
Nmap scan report for localhost (127.0.0.1)
Host is up.

PORT STATE SERVICE
22/tcp open ssh
8080/tcp open http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.05 seconds
```

```
knock localhost 22:tcp
nmap localhost

PORT STATE SERVICE
22/tcp open ssh
80/tcp open http
8080/tcp open http-proxy
```
Port 80 is now open

Complete the solution
```
curl localhost

Who is there?admin-ip-1234
```

**What I learned:** **Port Knocking** is a security technique that keeps ports closed until a specific "knock" (SYN packet) is sent to a predefined port. Once the correct port has been knocked, the server opens the protected port temporarily. This concept is used in the real world to hide servies from port scanners.

**SYN** stands for synchronise and when any device wants to connect to another, it sends a SYN packet first. The other device then responds with a **SYN-ACK** (synchronise-acknowledge) and the requesting device sends an ACK to confirm. This is called the **TCP three-way handshake**.

By default, `nmap` sends a SYN packet to every port it scans. This means running `nmap localhost` was knocking every port simultaneously, and revealed port 22 and 8080 as potential knock ports which is knocking why either or both ports worked.

`knock` sends a SYN packet to a specific port deliberately and provides no output when run.

`curl` is used to send HTTP requests to a web server i.e. `curl localhost` sends a request to port 80 on your own machine.