# ubuntu-kali-vuln-lab

Home lab: vulnerability assessment and hardening exercise using Kali and Ubuntu

# Ubuntu–Kali Vulnerability Assessment & Hardening Lab

This project was performed entirely in an isolated local lab (VirtualBox NAT Network)
against VMs I own and configured myself, for educational purposes.
No external systems were scanned or accessed.

## Summary

A full attack-and-defend cycle against a deliberately vulnerable Ubuntu Server
target, performed from Kali Linux: reconnaissance, exploitation, hardening,
and re-verification.

**Tools used:** nmap, nikto, gobuster, Hydra, DVWA (Damn Vulnerable Web App), fail2ban, UFW

**Key findings:**
- SSH weak password authentication — exploited via Hydra, fixed by disabling password auth
- SQL Injection in DVWA — exploited and remediated by raising application security level
- Missing Apache security headers — identified, documented as an open finding

See [findings-report.md](findings-report.md) for the full summary table.

## Walkthrough

1. [Reconnaissance](docs/01-recon.md)
2. [Exploitation](docs/02-exploitation.md)
3. [Hardening](docs/03-hardening.md)
4. [Verification](docs/04-verification.md)
