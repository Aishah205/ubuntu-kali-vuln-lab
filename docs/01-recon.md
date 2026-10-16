# Phase 2 — Reconnaissance

## Tools used
nmap, nikto, gobuster

## Open ports (nmap)
- 21/tcp — FTP (vsftpd 3.0.5)
- 22/tcp — SSH (OpenSSH 9.6p1)
- 80/tcp — HTTP (Apache 2.4.58)

## Web server findings (nikto)
- Missing X-Frame-Options header (clickjacking risk)
- Missing X-Content-Type-Options header (MIME-sniffing risk)
- ETag inode disclosure (CVE-2003-1418)
- Allowed methods: OPTIONS, HEAD, GET, POST

## Directory enumeration (gobuster)
- /config, /database, /docs, /external, /tests — exposed internal directories
- /phpinfo.php — accessible, discloses PHP/server configuration (notable finding)
- /.htpasswd, /.htaccess, /.hta — present but blocked (403)

Full raw output: see nmap-initial.txt and nikto-initial.txt in this folder.
