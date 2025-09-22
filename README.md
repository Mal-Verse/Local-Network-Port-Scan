# Local Network Port Scan (Kali Linux)

## Objective
Perform a TCP SYN scan on the local network to discover open ports and analyze potential security risks.

## Tools Used
- Kali Linux
- Nmap (`-sS` SYN scan)
- PostgreSQL (optional, if storing scan results)
- Wireshark (optional)

## Steps Performed
1. Find IP range using:
   ```bash
   ip a
My local subnet: 10.x.x.x/24

Run Nmap scan:

bash
Copy code
sudo nmap -sS 10.x.x.x/24 -oN scan_results.txt -oX scan_results.xml
(Optional) Capture packets with Wireshark to analyze scan traffic.

Save results (scan_results.txt and scan_results.xml).

Results
Host	Open Ports & Services	Status
10.x.x.x	135/tcp → MSRPC
445/tcp → Microsoft-DS (SMB)
1001/tcp → webpush
1042/tcp → afrog
1043/tcp → boinc
2000/tcp → Cisco SCCP
7778/tcp → interwise	Open / Active
10.x.x.x	All ports filtered	Protected
10.x.x.x	All ports closed	Safe (Kali)

Security Risks
SMB (445) and MSRPC (135) → known vulnerabilities, could be exploited.

Multiple uncommon open ports → increase attack surface.

Filtered ports → host is protected by firewall.

Closed ports → safe configuration.

Interview Questions & Answers
What is an open port?
A port that accepts incoming connections because a service is listening.

How does Nmap perform a TCP SYN scan?
Sends SYN packets; if SYN-ACK is received, the port is open; if RST, the port is closed. This is also called a “half-open” scan.

What risks are associated with open ports?
Attackers can exploit vulnerable services, perform brute force attacks, spread malware, or launch denial-of-service attacks.

Explain the difference between TCP and UDP scanning.

TCP: connection-oriented, uses 3-way handshake, more reliable.

UDP: connectionless, harder to detect, requires more probing to confirm open/closed status.

How can open ports be secured?

Disable unused services

Configure firewalls to block unnecessary ports

Keep software patched

Use VPNs for remote access

What is a firewall's role regarding ports?
It controls which ports are accessible from outside, blocking unauthorized access to services.

What is a port scan and why do attackers perform it?
A port scan probes a system to discover which services are running. Attackers use it for reconnaissance to find vulnerabilities.

How does Wireshark complement port scanning?
Wireshark captures network packets, allowing you to analyze SYN, SYN-ACK, and RST traffic to verify scan behavior.

PostgreSQL / Database Notes
(Optional) If you store results in PostgreSQL, you could log each host, port, service, and status for further analysis.

![Nmap Scan Command](your_nmap_command.png)
![Nmap Scan Results](your_nmap_results.png)

