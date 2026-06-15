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

**What I learned:** **Port Knocking** is a security technique that keeps ports closed until a specific "knock" (SYN packet) is sent to a predefined port. Once the correct port has been knocked, the server opens the protected port temporarily

By default nmap sends a SYN packet to every port it scans
This means running nmap localhost was actually knocking every port simultaneously without you realising
That's why both port 22 and 8080 worked — nmap had already sent a SYN to both during the scan
knock command
Sends a SYN packet to a specific port deliberately
Silent by default — no output when run
knock localhost 8080 — sends one knock to port 8080
curl
Used to send HTTP requests to a web server
curl localhost — sends a request to port 80 on your own machine
Key takeaway:
Port knocking is a lightweight security method — no password needed, just knowing which port to knock
Used in real world to hide services from port scanners

SYN stands for synchronise — it's the first step in establishing a TCP connection.
When any device wants to connect to another it sends a SYN packet first, essentially saying "I want to start a connection". The other device then responds with a SYN-ACK (synchronise-acknowledge) and then the requesting device sends an ACK to confirm — this is called the TCP three-way handshake