Part 1: 

Footprinting and Reconnaissaince

Scanning Networks

Enumeration

Vulnerability Analysis

1. Footprinting complete on a web application. Analyze report and ID hostname associated with IP xxx.xxx.xxxx

Answer: henry.ns.cloudflare.com

Explanation: 

1. Identify the number of live machines excluding the gateway in 192.168.10.0/24 subnet **(Host Discovery)**

Answer: 5

Explanation: 

Host discovery using nmap: ***nmap -sn xxx.xxx.xxx.**** 

Host, service, port discover: ***nmap -sS -sV -O xxx.xxx.xxx.****

<aside>
💡

Save scan as .nmap file to desktop, can view in notepad for future reference 

</aside>

1. Identify the IP address of a Linux-based machine with port 22 open in the target network

Answer: 192.168.10.111

Explanation: 

Perform OS / Service discovery using nmap: ***nmap -p 22 -T4 -O -v <target subnet>***

1. Find the IP address of the Domain Controller machine in 192.168.0.0/24

Answer: 192.168.0.222

Explanation: 
Perform nmap scan for open ldap service (port 389,636): ***nmap -p 389,636 <target subnet>***

or ***nmap -p 389 --script ldap-rootdse <target subnet>***

Port 88 (Kerberos) may also be open

1. Perform a host discovery scanning and identify the NetBIOS_Domain_Name of the host at 192.168.0.222. 

Answer: SKILL.CEH

Explanation: 

Use nmap service discovery: ***nmap -sV -A <target IP>***

1. Perform an intense scan on 192.168.0.222 and find out the DNS_Tree_Name of the machine in the network. 

Answer: SKILL.CEH.com

Explanation: 

Nmap command for #5 shows this

1. While performing a security assessment against the CEHORG network, you came to know that one machine in the network is running OpenSSH and is vulnerable. Identify the version of the OpenSSH running on the machine. Note: Target network 192.168.10.0/24. (Format: N.NaN)

Answer: 8.9p1

Explanation: 

Can search for open port 22 on subnet and then probe individual machine: ***nmap*** ***-p 22 -sV 192.168.10.0/24 --open***

Run ***nmap -sV -A -v <target IP>*** (This scan may take a while) 

1. During a security assessment, it was found that a server was hosting a website that was susceptible to blind SQL injection attacks. Further investigation revealed that the underlying database management system of the site was MySQL. Determine the machine OS that hosted the database. Note: Target network 172.30.10.0/24 (Format: Aaaaaa)

Answer: Ubuntu 

Explanation: 

Scan the subnet: ***nmap -sV  -A -v <target subnet>*** and then search for IP with mysql service 

or 

***nmap -p 3306 172.30.10.0/24 --open*** to search for the IP with mysql service port open

***nmap -A 172.30.10.99*** to aggressively scan that IP

![image.png](attachment:de8a5632-f5dc-47f6-bbf7-dcdf2b85176c:image.png)

1. Perform an intense scan on target subnet 192.168.10.0/24 and determine the IP address of the machine hosting the MSSQL database service. (Format: NNN.NNN.NN.NNN)

Answer: 192.168.10.0

Explanation: 

***nmap -A -v <target subnet>*** or ***nmap -p 1433 <target subnet>***

Find IP with open MSSQL service 

1. Perform a DNS enumeration on www.certifiedhacker.com and find out the name servers used by the domain. (Format: aaN.aaaaaaaa.aaa, aaN.aaaaaaaa.aaa)

Answer: ns2.bluehost.com, ns1.bluehost.com

Explanation: ***dig ns www.certifiedhacker.com*** or WHOis lookup

1. Find the IP address of the machine running SMTP service on the 172.30.10.0/24 network. (Format: NNN.NN.NN.NNN)

Answer: 172.30.10.200
Explanation: 
***nmap -p 25 172.30.10.0/24 --open***

1. Perform an SMB Enumeration on 172.30.10.200 and check whether the Message signing feature is required. Give your response as Yes/No

Answer: No
Explanation: 
***nmap -p 445 -sV -A 172.30.10.200***

![image.png](attachment:17fa6bca-b9f6-4b78-b241-bb7b198d3f09:image.png)

1. Conduct a Common Weakness Enumeration on the Weakness ID 276 and identify the name associated with the ID. (Format: Aaaaaaaaa Aaaaaaa

Answer: Incorrect Default Permissions
Explanation: Google search or CWE search

1. Perform vulnerability scanning for the Linux host in the 192.168.10.0/24 network using OpenVAS and find the QoD percentage of vulnerabilitiy with severity level as medium. (Format: NN)

Answer: 70 
Explanation:

Use OpenVAS application on desktop or run ***docker run -d -p 443:443 --name openvas mikesplain/openvas*** and navigate to 127.0.0.1

1. Perform a vulnerability scan on the host at 192.168.10.144 using OpenVAS and identify any FTP-related vulnerability. (Format: AAA Aaaaaaaaa Aaaaaaaaa Aaaaa )

Answer: FTP Unencrypted Cleartext Login
Explanation: Utilize OpenVAS
