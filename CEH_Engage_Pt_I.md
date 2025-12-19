## Part I  
Footprinting and Reconnaissance  
Scanning Networks  
Enumeration  
Vulnerability Analysis

---

**Q1. Footprinting complete on a web application. Analyze report and ID hostname associated with IP xxx.xxx.xxxx**

**Answer:** henry.ns.cloudflare.com

**Explanation:**  
The hostname was identified through footprinting analysis of the web application’s associated IP address.

---

**Q2. Identify the number of live machines excluding the gateway in 192.168.10.0/24 subnet (Host Discovery)**

**Answer:** 5

**Explanation:**  

Host discovery using Nmap: `nmap -sn xxx.xxx.xxx.*`  

Host, service, and OS discovery: `nmap -sS -sV -O xxx.xxx.xxx.*`

> 💡 Save scan output as a `.nmap` file to the desktop.  
> This file can be opened in Notepad for future reference.

---

**Q3. Identify the IP address of a Linux-based machine with port 22 open in the target network**

**Answer:** 192.168.10.111

**Explanation:**  

Perform OS and service discovery using Nmap:  
`nmap -p 22 -T4 -O -v <target subnet>`

---

**Q4. Find the IP address of the Domain Controller machine in 192.168.0.0/24**

**Answer:** 192.168.0.222

**Explanation:**  

Perform Nmap scan for open LDAP services (ports 389, 636):  
`nmap -p 389,636 <target subnet>`  

Or use LDAP root DSE script:  
`nmap -p 389 --script ldap-rootdse <target subnet>`  

Port 88 (Kerberos) may also be open.

---

**Q5. Perform a host discovery scan and identify the NetBIOS_Domain_Name of the host at 192.168.0.222**

**Answer:** SKILL.CEH

**Explanation:**  

Use Nmap service discovery:  
`nmap -sV -A <target IP>`
