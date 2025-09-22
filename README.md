# Local Network Port Scan (Kali Linux)

## Objective
Brief description of the task.

## Tools Used
- Kali Linux
- Nmap
- PostgreSQL (if used for storing scan results)

## Steps Performed
1. Find IP range: `ip a`
2. Run scan: `sudo nmap -sS 10.x.x.x/24 -oN scan_results.txt -oX scan_results.xml`
3. (Optional) Capture packets with Wireshark
4. Save results

## Results
- Host 10.x.x.x: open ports → list
- Host 10.x.x.x: filtered ports
- Host 10.x.x.x: all closed

## Security Risks
- SMB / RPC → potential exploits
- Unnecessary open ports → attack surface

## Interview Questions & Answers
1. What is an open port? …  
2. How does Nmap perform a TCP SYN scan? …  
… continue all 8 Q&A

## PostgreSQL / Database Notes
(Optional) Any info about storing or processing scan results in PostgreSQL.

