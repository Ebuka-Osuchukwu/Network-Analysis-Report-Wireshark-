# Project Title: Wireshark Packet Analysis – [Focusing on filtering and inspecting packets]
**Date:** 24-09-2025
**Platform:** TryHackMe  
**Difficulty:** Beginner 
**Time spent:** 2.5 hours

## Objective
To gain practical experience in capturing, filtering, and analysing network traffic using Wireshark, to understand how different protocols function, identify suspicious activity, and develop investigative and reporting skills relevant to cybersecurity operations.

## Environment
- Host: TryHackMe AttackBox / Wireshark
- Target IP: 10.10.235.77 (lab)
- Tools: Wireshark 3.6, Nmap 7.92

## Steps & Commands
1. Set up Wireshark

Installed Wireshark and selected the correct network interface for capturing.
Ensured traffic was captured from both live browsing sessions and PCAP files.
Captured Traffic
Browsed different websites (HTTP and HTTPS) to generate traffic.
Used command-line tools like ping (ICMP), nslookup (DNS), and basic browsing to simulate traffic.

2. Applied Filters
Used display filters to isolate protocols:

http – show HTTP traffic
https – show HTTPS traffic
tcp / udp – show transport layer packets
icmp – show ping requests/replies
arp – show ARP broadcasts and replies
dns – show domain resolution queries and responses

Applied filters for specific IPs: ip.addr == <IP>

3. Packet Dissection
Broke down packets using the OSI model (e.g., Ethernet header at Layer 2, IP at Layer 3, TCP/UDP at Layer 4, HTTP data at Layer 7).
Compared differences between HTTP (cleartext requests/responses) and HTTPS (encrypted data).

4. Advanced Analysis
Used Protocol Hierarchy (Statistics → Protocol Hierarchy) to view traffic distribution.
Used Endpoints and Conversations (Statistics menu) to identify hosts communicating on the network.
Exported capture slices for documentation.

5. Exploit PCAP Analysis
Loaded a sample Active Directory exploit PCAP file.
Identified suspicious traffic and attacker IP using filters (ip.addr == <attacker_ip>).
Noted unusual packet patterns consistent with credential dumping.

6. Documentation
Compiled findings into a technical report with screenshots and explanations.
Uploaded the report to GitHub to demonstrate technical and communication skills.

## Evidence
<img width="1919" height="881" alt="Screenshot 2025-09-24 171852" src="https://github.com/user-attachments/assets/edda7f72-0628-43e4-9c9a-77675d0614ef" />
<img width="1919" height="1010" alt="Screenshot 2025-09-24 134550" src="https://github.com/user-attachments/assets/57fc138c-0b89-4191-a13e-e5d86366b0c8" />

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
