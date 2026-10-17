# Wireshark Traffic Analysis — SSH Brute-force Detection

This sub-project captures and analyzes network traffic during an SSH
brute-force attack against the same Kali/Ubuntu lab used in the main
vulnerability assessment, demonstrating attack detection at the packet
level rather than just the attack outcome.

## Captures

- `captures/ssh-bruteforce-capture.pcapng` — single connection attempt,
  captured after SSH hardening (PasswordAuthentication disabled).
  Hydra connects once and is immediately rejected (1 TCP stream).

- `captures/multi-attempt-bruteforce.pcapng` — captured with
  PasswordAuthentication temporarily re-enabled to demonstrate the
  full brute-force pattern. Shows 6 separate TCP streams from the same
  source IP to port 22, each ~4-5 seconds apart, the classic
  brute-force signature of repeated rapid connection attempts.

## Analysis

- `bruteforce-conversations-view.png` — Wireshark's Conversations view
  showing the 6 repeated connection attempts, demonstrating how a
  brute-force attack is visible as a traffic pattern even without
  decrypting the payload.

- `bruteforce-stream-view.png` — Follow TCP Stream view of a single
  SSH session, showing that while the connection attempts are visible,
  SSH's encryption means the actual password attempts themselves are
  never exposed in the capture.

## Key takeaway

SSH's encryption protects credential confidentiality even under active
attack, but the *pattern* of repeated connection attempts remains
visible and detectable at the network level, which is what tools like
fail2ban (already deployed in the main lab) use to identify and block
brute-force attempts.
