# Credential-Harvesting-through-Phishing-Lab-Investigation
SOC lab simulating a credential harvesting phishing attack , investigated using Splunk, Wireshark, and Sysmon

# Phishing & Credential Harvesting Investigation Lab

## Overview
Simulated a full phishing campaign using GoPhish against an 
enterprise-style segmented network, then investigated the attack 
using Splunk SIEM and Wireshark packet analysis.

## Lab Environment
| Component | Tool/Config |
|---|---|
| Firewall/Router | pfSense (zone-based, 3 network segments) |
| Attacker Machine | Kali Linux — GoPhish, Postfix, Dovecot |
| Victim Machine | Windows 10 — Sysmon, Splunk Universal Forwarder |
| SIEM | Splunk Enterprise |
| Packet Capture | Wireshark |

## Attack Phases Investigated
1. Email delivery via typosquatting domain (linked-in.com)
2. Tracking pixel firing on email open
3. Credential submission via cloned LinkedIn login page
4. Covert browser redirection post-exfiltration

## MITRE ATT&CK Coverage
| Tactic | Technique |
|---|---|
| Reconnaissance | T1598 – Phishing for Information |
| Resource Development | T1583.001 – Acquire Domains | T1585.002 - Email Accounts | T1587 - Stage Capabilities |
| Initial Access | T1566 – Phishing |
| Execution | T1204.001 - User Execution: Malicious Link |
| Defense Evasion | T1036.007 – Lookalike Domains | T1531 / T1071.001 -  Traffic Signaling / Covert Redirection |
| Credential Access | T1557 – Adversary-in-the-Middle |
| Discovery | T1082 - System Information Discovery |
| Command & Control | T1071.001 – Web Protocols |

## Key Splunk Detections
- Sysmon Event ID 1 — Process creation (thunderbird.exe spawning msedge.exe)
- Sysmon Event ID 3 — Outbound connection to attacker IP
- Sysmon Event ID 22 — DNS query resolving kali.lab → 192.168.1.11

## Investigation Report
Full forensic report available in `/report/`

## Tools Used
GoPhish · Splunk Enterprise · Wireshark · Sysmon · pfSense · 
Postfix · Dovecot · Kali Linux · Windows 10
