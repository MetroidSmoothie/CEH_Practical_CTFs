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
`nslookup -type=NS example.com`

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

---

**Q6. Perform an intense scan on 192.168.0.222 and find the DNS_Tree_Name of the machine in the network**

**Answer:** SKILL.CEH.com

**Explanation:**  

The DNS tree name is revealed in the results of the Nmap scan performed in Question 5.

---

**Q7. While performing a security assessment against the CEHORG network, one machine was found running a vulnerable OpenSSH service. Identify the OpenSSH version (Target network: 192.168.10.0/24)**

**Answer:** 8.9p1

**Explanation:**  

Identify hosts with port 22 open:  
`nmap -p 22 -sV 192.168.10.0/24 --open`  

Run an aggressive scan on the identified host:  
`nmap -sV -A -v <target IP>`

---

**Q8. A server hosting a website vulnerable to blind SQL injection was found to be running MySQL. Determine the OS hosting the database (Target network: 172.30.10.0/24)**

**Answer:** Ubuntu

**Explanation:**  

Scan the subnet for MySQL services:  
`nmap -sV -A -v <target subnet>`  

Or directly locate MySQL service:  
`nmap -p 3306 172.30.10.0/24 --open`  

Then perform an aggressive scan on the identified host:  
`nmap -A 172.30.10.99`

<img width="760" height="483" alt="image" src="https://github.com/user-attachments/assets/0ef05ae9-d664-492f-b6bd-7a9ac573be8b" />

---

**Q9. Perform an intense scan on target subnet 192.168.10.0/24 and determine the IP address of the machine hosting the MSSQL database service**

**Answer:** 192.168.10.0

**Explanation:**  

Perform an aggressive scan:  
`nmap -A -v <target subnet>`  

Or scan directly for MSSQL service:  
`nmap -p 1433 <target subnet>`

---

**Q10. Perform a DNS enumeration on www.certifiedhacker.com and identify the name servers used by the domain**

**Answer:** ns2.bluehost.com, ns1.bluehost.com

**Explanation:**  

Use DNS enumeration tools:  
`dig ns www.certifiedhacker.com`  

Or perform a WHOIS lookup.

---

**Q11. Find the IP address of the machine running SMTP service on the 172.30.10.0/24 network**

**Answer:** 172.30.10.200

**Explanation:**  

Scan for SMTP service:  
`nmap -p 25 172.30.10.0/24 --open`

---

**Q12. Perform an SMB Enumeration on 172.30.10.200 and determine whether Message Signing is required**

**Answer:** No

**Explanation:**  

Perform SMB service enumeration:  
`nmap -p 445 -sV -A 172.30.10.200`

<img width="518" height="373" alt="image 1" src="https://github.com/user-attachments/assets/8e5cbc2c-4bc7-4545-a781-a892ab908cb8" />

---

**Q13. Conduct a Common Weakness Enumeration on Weakness ID 276 and identify the name associated with the ID**

**Answer:** Incorrect Default Permissions

**Explanation:**  

Search the CWE database or perform a Google search for CWE-276.

---

**Q14. Perform vulnerability scanning for a Linux host in the 192.168.10.0/24 network using OpenVAS and determine the QoD percentage for vulnerabilities with medium severity**

**Answer:** 70

**Explanation:**  

Use the OpenVAS application on the desktop  
or deploy OpenVAS using Docker:  
`docker run -d -p 443:443 --name openvas mikesplain/openvas`  

Navigate to `https://127.0.0.1`

---

**Q15. Perform a vulnerability scan on the host at 192.168.10.144 using OpenVAS and identify any FTP-related vulnerability**

**Answer:** FTP Unencrypted Cleartext Login

**Explanation:**  

Perform vulnerability scanning using OpenVAS and review FTP-related findings.
