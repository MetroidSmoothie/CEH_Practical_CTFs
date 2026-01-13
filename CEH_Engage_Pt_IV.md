## CEH Engage – Part IV  
Hacking Wireless Networks  
Hacking Mobile Platforms  
IoT and OT Hacking  
Cloud Computing  
Cryptography Modules

---

**Q1. An employee's mobile device within CEHORG has been compromised, resulting in an encrypted message BCtetx.txt placed on the Android OS. The password required to decrypt the file is stored on EH-workstation-1. Decrypt the file and provide the extracted information. (Note: Password file pawned.txt is stored in the Documents folder.) (Format: *aaaaAN*NaN)**

**Answer:** (ryptD3(0d3

**Explanation:**  

Open terminal in the PhoneSploit directory and launch:
`python3 phonesploitpro.py`

- Select option **1** to enter the phone IP  
- Use option **14** (`pwd / cd / ls`) to navigate to `sdcard/Download`  
- Use option **8** to download the `Download` directory  

Use BC Text Encoder Utility on Windows to decode the file using the password `Pa$$w0rd`.

---

**Q2. A compromised Android device is suspected of containing malicious applications. Extract all installed APK files and determine the CRC value ending with “614c”. This CRC value is believed to be a crucial component of a larger security breach investigation. Determine the complete CRC value as answer (Format: NNaaNNNa)**

**Answer:** 53ac614c

**Explanation:**  

Connect via PhoneSploit and navigate to APK extraction:
- Use option **N** twice to reach next menus
- Select **36** (Extract APK from Installed App)
- Select **2** for `com.cxinventor.file.explorer`

Run terminal in installs APK directory, run:
`crc32 <apk_filename>`

---

**Q3. A ZIP archive containing redundant images of a physical signature has been compromised.  Your role as an ethical hacker involves a forensic examination of the archive's contents to pinpoint the image file associated with an MD5 hash value ends with sequence "24CCB". Determine the original signature file name as answer. (Format: aN*aaa)**

**Answer:** k4.png

**Explanation:**  

Extract the ZIP archive and open the directory in PowerShell.  
Run:
`get-filehash <filename> -algorithm md5`

Compare hash values to identify the matching file.

---

**Q4. As a cybersecurity analyst, you are investigating a potential phishing campaign targeting Ruby, an employee at a local tech company. You have access to Ruby’s call log from the past few days, stored on an Android device within the target subnet 192.168.10.0/24. Identify the call in the log that is most likely a phishing attempt and provide the suspected phone number. (Format: +N (NNN) NNN-NNNN )**

**Answer:** +1 (555) 678-9012

**Explanation:**  

Note: Dumping call log does not work
Dump call logs from:
`sdcard/calls/call_log_dump`

Review entries requesting sensitive information such as SSN.

---

**Q5. Analyze the network capture file And_Dos.pcapng and determine the severity level of the DoS attack. (Format: Aaaaaaa)**

**Answer:** Warning

**Explanation:**  

Open the capture file in Wireshark.  
Navigate to:
`Analyze → Expert Information`

Review the severity classification.

---

**Q6. Analyze the MQTT.pcapng file and determine the alert percentage in the “High_humidity” message. (Format: NN)**

**Answer:** 50

**Explanation:**  

In Wireshark:
- Go to **Edit → Find Packet**
- Search parameter ‘String’ → `High_humidity`
- Right-click the packet → **Follow TCP Stream**

---

**Q7. Decrypt the file cryt-128-06encr.hex and identify the encryption algorithm and hidden text. (Format: Aaaaaaa/**aa**aA*a)**

**Answer:** Twofish/@!ph@|tE*t

**Explanation:**  

Use CrypTool on the Windows VM.  
Based on filename indicators:
- Key length: 128
- Key: 6

Perform cryptanalysis using the Twofish algorithm.

---

**Q8. Decrypt the VeraCrypt volume “MyVeracrypt” and determine the number of files inside. (Hint: Password: veratest) (Format: N)**

**Answer:** 4

**Explanation:**  

Import the volume into VeraCrypt, mount it, and decrypt.  
Navigate to the mounted drive and count files in the `S2` folder.

---

**Q9. Retrieve the contacts dump from an Android phone on one of the target subnets and identify the country code for the contact named “Maddy”. (Format: NN)**

**Answer:** 61

**Explanation:**  

Use PhoneSploit to extract contacts.  
Navigate through pages using option **N** until locating “Maddy”.

---

**Q10. Analyze the MQTT.pcapng file and determine the topic length of the “High_temperature” message. (Format: NN)**

**Answer:** 16

**Explanation:**  

Using 'String' parameter -> Search Wireshark for `High_temperature`.  
Inspect the MQTT header to identify the topic length field.

---

**Q11. Retrieve KEYCODE-5 used on an employee’s mobile phone using PhoneSploit. (Format: Aaaaa*Aaaaaa)**

**Answer:** Power Button

**Explanation:**  

In PhoneSploit:
- Select option **39** (Use Keycodes)
- Navigate to KEYCODE-5

---

**Q12. An employee has stored confidential access ID information on their Android device. Access and delete the file covertly and provide the numeric account information. (Format: NNNNNNNN)**

**Answer:** 80099889

**Explanation:**  

Use PhoneSploit to navigate to the Music directory.  
Access the file, retrieve the numeric data, and delete it.

---

**Q13. Retrieve a screenshot of an LOIC attack from a compromised Android device and determine the number of HTTP packets sent per second. (Format: NN)**

**Answer:** 23

**Explanation:**  

The screenshot is located in the Music directory.  
Review the image to identify packet transmission rate.

---

**Q14. Verify file integrity within the “Archive” folder and identify the file that has been tampered with. (Exclude file extension.) (Format: Aaaaaa)**

**Answer:** 

**Explanation:**  

Run:
`md5sum <filename>`

Compare results against hashes listed in `FileHashes.txt` to identify the altered file.

---

**Q15. Decrypt the VeraCrypt volume “secret” and determine the number of files stored inside. (Hint: Password: test) (Format: N)**

**Answer:** 6

**Explanation:**  

Mount and decrypt the VeraCrypt volume.  
Count the number of files present within the decrypted directory.
