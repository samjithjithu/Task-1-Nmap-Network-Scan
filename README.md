# Task 1: Basic Network Scanning with Nmap

## 🎯 Objective
Perform a network scan to identify open ports and services on a target system using Nmap.

## 🛠 Tools Used
- Nmap 7.94SVN
- Kali Linux (Attacker Machine)
- Metasploitable 2 (Target VM)

---

## 🚀 Steps Performed

### ✅ 1. Identified Target IP
We used `ifconfig` on the Metasploitable VM to find its IP:
inet addr:192.168.18.4

### ✅ 2. Ran Nmap Service and Version Scan
Command:
```bash
nmap -sS -sV -O -T5 192.168.18.4

Explanation:

-sS: TCP SYN scan (stealthy)
-sV: Detect service versions
-O: OS detection
-T5: Faster timing template (aggressive)

🔍 Findings Summary

Port     	Service	       Version	                               Risk Explanation

21	       FTP	        vsftpd 2.3.4	              Known backdoor vulnerability (CVE-2011-2523).
22	       SSH         	OpenSSH 4.7p1           	Old version, possible brute force attack surface.
23	      Telnet	      Linux telnetd           	Unencrypted communication, vulnerable to sniffing.
80	       HTTP	        Apache 2.2.8	         Outdated, possible directory traversal & RCE exploits.
3306	    MySQL	        MySQL 5.0.51a                 	   Weak/default credentials risk.
5432   	PostgreSQL	    PostgreSQL 8.3.0           	May expose sensitive DB data if misconfigured.
5900	     VNC	       VNC Protocol 3.3	         Unencrypted remote desktop, brute-force possibility.
6667      	IRC	U        nrealIRCd	                        Known backdoor (CVE-2010-2075).

📝 The target OS was detected as Linux 2.6.x.
