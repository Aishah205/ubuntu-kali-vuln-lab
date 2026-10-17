# Findings Report — Ubuntu/Kali Vulnerability Assessment Lab

| Finding | Risk Rating | Evidence | Remediation | Verified Fixed |
|---|---|---|---|---|
| SSH password authentication + root login enabled | High | Hydra cracked testuser (labpassword123) on first attempt — see docs/hydra-ssh-result.txt | Disabled PasswordAuthentication and PermitRootLogin in sshd_config; installed fail2ban | Yes — Hydra now fails with "does not support password authentication" |
| SQL Injection in DVWA | Critical | Payload 1' OR '1'='1 dumped entire user table at security level Low — see screenshots/sqli-low-result.png | Raised DVWA security level to High | Yes — same payload now returns a single record — see screenshots/sqli-high-result.png |
| Missing security headers (X-Frame-Options, X-Content-Type-Options) | Low | Confirmed via Nikto scan — see docs/nikto-initial.txt | Not addressed in this pass | No — open finding, recommend adding headers via Apache config |
| ETag inode disclosure (CVE-2003-1418) | Low | Confirmed via Nikto scan | Not addressed in this pass | No — open finding |
