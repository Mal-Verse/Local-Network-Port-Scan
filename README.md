# Local Network Port Scan (Kali Linux)

## Objective
Perform a TCP SYN scan on the local network to discover open ports, analyze potential security risks, and document findings. All IP addresses have been anonymized.

## Tools Used
- Kali Linux  
- Nmap (`-sS` TCP SYN scan)  
- Wireshark (optional)  
- PostgreSQL (optional, if storing scan results)

## Steps Performed
1. Find IP range: `ip a`  
2. Run scan: `sudo nmap -sS 10.x.x.x/24 -oN scan_results.txt -oX scan_results.xml`  
3. (Optional) Capture packets with Wireshark  
4. Save results in `scan_results.txt` and `scan_results.xml`  

## Results
- Host 10.x.x.2: open ports → 135/tcp (MSRPC), 445/tcp (Microsoft-DS / SMB), 1001/tcp (webpush), 1042/tcp (afrog), 1043/tcp (boinc), 2000/tcp (Cisco SCCP), 7778/tcp (interwise)  
- Host 10.x.x.3: all ports filtered  
- Host 10.x.x.15: all closed  

## Security Risks
- 135/tcp (MSRPC) & 445/tcp (SMB) → commonly targeted by worms and remote exploits  
- 1001, 1042, 1043, 2000, 7778 → uncommon services, increase attack surface if exposed  
- Filtered ports → minimal risk, firewall protection  
- Closed ports → safe, no exposed services

## Interview Questions & Answers
1. **What is an open port?**  
A port that accepts incoming connections because a service is listening.  

2. **How does Nmap perform a TCP SYN scan?**  
Sends SYN packets; if SYN-ACK is received, the port is open; if RST is received, the port is closed. Known as a “half-open” scan.  

3. **What risks are associated with open ports?**  
Attackers can exploit vulnerabilities, spread malware, perform brute force attacks, or launch denial-of-service attacks.  

4. **Explain the difference between TCP and UDP scanning.**  
- TCP: connection-oriented, reliable handshake  
- UDP: connectionless, harder to detect, may require multiple probes  

5. **How can open ports be secured?**  
Disable unused services, configure firewalls, patch software, and use VPNs for remote access.  

6. **What is a firewall's role regarding ports?**  
Controls which ports are accessible from outside, blocking unauthorized connections.  

7. **What is a port scan and why do attackers perform it?**  
A port scan probes a system to find open services. Attackers use it for reconnaissance to locate potential vulnerabilities.  

8. **How does Wireshark complement port scanning?**  
Wireshark captures network traffic, showing SYN, SYN-ACK, and RST packets to verify scanning behavior and analyze responses.

## PostgreSQL / Database Notes
(Optional) Scan results can be stored in PostgreSQL for further analysis, logging hosts, ports, services, and status.

# Refrence SS**
![Nmap Scan Command](your_nmap_command.png)
![Nmap Scan Results](your_nmap_results.png)
