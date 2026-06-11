# OverTheWire Bandit

Practice challenges working through the OverTheWire Bandit wargame.

Each level documents:
- The objective
- Commands and concepts used
- What I learned

## Levels

### Linux Fundamentals

- [Level 0 → 1](./level0.md) — Reading files from the command line
- [Level 1 → 2](./level1.md) — Handling special characters in filenames
- [Level 2 → 3](./level2.md) — Working with spaces in filenames
- [Level 3 → 4](./level3.md) — Discovering hidden files and directories
- [Level 4 → 5](./level4.md) — Identifying file types with `file`
- [Level 5 → 6](./level5.md) — Finding files based on size and attributes
- [Level 6 → 7](./level6.md) — Searching files by ownership and permissions

### Data Analysis & Text Processing

**Key tools:** `grep`, `sort`, `uniq`, `strings`, `find`

- [Level 7 → 8](./level7.md) — Pattern matching with `grep`
- [Level 8 → 9](./level8.md) — Identifying unique values in datasets
- [Level 9 → 10](./level9.md) — Extracting readable data from binary files

### Encoding, Compression & Data Transformation

**Key tools:** `base64`, `xxd`, `gzip`, `bzip2`, `tar`

- [Level 10 → 11](./level10.md) — Base64 decoding
- [Level 11 → 12](./level11.md) — ROT13 transformation
- [Level 12 → 13](./level12.md) — Hex dumps, file carving, and recursive decompression

### Networking & Secure Communications

**Key tools:** `ssh`, `nc`, `openssl`, `nmap`

- [Level 13 → 14](./level13.md) — SSH key-based authentication
- [Level 14 → 15](./level14.md) — Communicating with services using Netcat
- [Level 15 → 16](./level15.md) — Establishing SSL/TLS connections
- [Level 16 → 17](./level16.md) — Port scanning and service enumeration
- [Level 17 → 18](./level17.md) — Comparing files to identify credential changes

### Privilege Escalation & Access Control

**Key concepts:** SUID binaries, restricted shells, privilege separation

- [Level 18 → 19](./level18.md) — Bypassing restricted shell behavior
- [Level 19 → 20](./level19.md) — Leveraging SUID programs
- [Level 20 → 21](./level20.md) — Inter-process communication and privileged services
- [Level 25 → 26](./level25.md) — Accessing systems through managed SSH keys
- [Level 26 → 27](./level26.md) — Escaping restricted environments via Vim
- [Level 32 → 33](./level32.md) — Exploiting shell behavior to gain command execution

### Security Automation & Scheduled Tasks

**Key concepts:** Cron jobs, automation, workflow analysis, brute-force scripting

- [Level 21 → 22](./level21.md) — Auditing scheduled tasks
- [Level 22 → 23](./level22.md) — Analyzing automated scripts
- [Level 23 → 24](./level23.md) — Leveraging scheduled task execution
- [Level 24 → 25](./level24.md) — Automating password discovery attacks

### Version Control & Source Code Investigation

**Key tools:** `git`, commit history, branches, tags

- [Level 27 → 28](./level27.md) — Repository cloning and inspection
- [Level 28 → 29](./level28.md) — Commit history analysis
- [Level 29 → 30](./level29.md) — Branch investigation
- [Level 30 → 31](./level30.md) — Tag enumeration
- [Level 31 → 32](./level31.md) — Source code review and hidden credential discovery