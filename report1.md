# Project Title: Wireshark Packet Analysis – [Focusing on filtering and inspecting packets]
**Date:** 24-09-2025
**Platform:** TryHackMe  
**Difficulty:** Beginner 
**Time spent:** 2.5 hours

## Objective
Short: e.g., "Understand basic packet capture and identify DNS exfiltration."

## Environment
- Host: Kali (VM) 2025.09
- Target IP: 10.10.1.5 (lab)
- Tools: Wireshark 3.6, tcpdump, Nmap 7.92

## Steps & Commands
1. Nmap scan: `nmap -sC -sV -oN nmap_scan.txt 10.10.1.5`
2. Capture traffic: `sudo tcpdump -i eth0 -w capture.pcap`
3. Open pcap in Wireshark and filter: `http.request || dns`

## Evidence
- `screenshot_01_nmap.png` — shows open ports 22,80
- `capture.pcap` — saved on repo
*(Include annotated screenshots here)*

## Findings
- Found HTTP basic auth on port 80 → credentials sent in cleartext.
- DNS queries to suspicious domain `exfil.example.com` indicating possible data exfiltration.

## Remediation
- Enforce HTTPS and HSTS.
- Block or monitor DNS requests to suspicious domains.
- Implement network egress filtering.

## Lessons Learned
- How to use Wireshark display filters to isolate suspicious flows.
- Next: practice extracting files from pcap with `tshark`.

## References
- TryHackMe room: [Room URL]
- Wireshark filters cheat sheet
