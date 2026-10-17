# Phase 5 — Verification

## SSH Brute-force (Hydra)
Before: password found in first attempt (testuser / labpassword123)
After: target does not support password authentication (method reply 4)
Fix confirmed: Hydra can no longer attempt password-based login.

## SQL Injection (DVWA)
Before: payload 1' OR '1'='1 at security level Low returned all user records
After: same payload at security level High returns only one record (admin)
Fix confirmed: see screenshots/sqli-low-result.png and screenshots/sqli-high-result.png

## Web Server Headers (Nikto)
Before and after scans show identical findings — missing X-Frame-Options,
missing X-Content-Type-Options, ETag inode disclosure (CVE-2003-1418).
These were not addressed in this hardening pass and remain open findings
for future remediation.
