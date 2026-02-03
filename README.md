# CEH Engage – Capture The Flag (Red Team Simulation)

## Overview

CEH Engage is a hands-on Capture The Flag (CTF) practice range designed to simulate a real-world red team engagement.  

All four parts of the Engage environment involve a single target organization and require the application of techniques learned throughout the Certified Ethical Hacker (CEH) course. The purpose of this range is to bridge the gap between theory and practice by applying offensive security concepts in a realistic enterprise scenario.

The environment is divided into four progressive sections that together represent a single continuous assessment. Each phase builds upon the previous one, requiring chaining multiple techniques together rather than solving isolated tasks.

- Part I – Footprinting, scanning, enumeration, and vulnerability analysis  
- Part II – System exploitation, credential attacks, and service abuse  
- Part III – Web attacks, session hijacking, and post-exploitation techniques  
- Part IV – Wireless, mobile, IoT/OT, cloud, and cryptography-related challenges  

This repository contains my walkthrough and notes as I worked through each phase and applied red team tools and techniques to solve the challenges presented.

---

## Scenario

Operated as part of the Red Team for **CEHORG**, an IT services organization focused on advanced information security research.  

Following an increase in cybersecurity incidents across its distributed network, the organization initiated a comprehensive security assessment. My role was to evaluate the enterprise environment by identifying vulnerabilities across internal and external systems and demonstrating potential risk through controlled exploitation.


## Network Architecture

The simulated enterprise network reflects a realistic corporate environment with multiple zones and segmented subnets.

### Front Office / External Access
- Public-facing systems
- Customer kiosks
- Guest Wi-Fi connectivity
- Internet-accessible resources

### Demilitarized Zone (DMZ)
- Web servers
- Mail servers
- Public services exposed to the internet

### Militarized / Internal Zones
- Application servers
- Department resources
- Internal services and sensitive systems
- Segmented subnet architecture for isolation

### Enterprise Design Characteristics
- Multiple interconnected subnets
- Separate security zones
- Controlled routing between networks
- Replicated topology across satellite offices
- Internal and external attack surfaces

---

## Tools Utilized

- Nmap
- Wireshark
- Hydra
- Metasploit Framework
- SQLMap
- Burp Suite
- Netcat
- John the Ripper
- Hashcat
- OpenVAS
- Steghide
- Standard Linux utilities and scripting


## Skills Demonstrated

- Network reconnaissance and mapping  
- Host and service enumeration  
- Credential attacks and brute forcing  
- Packet capture and traffic analysis  
- Web application testing  
- SQL injection exploitation  
- Privilege escalation  
- Post-exploitation techniques  
- Multi-stage attack chaining  
- Structured documentation and reporting  

---

## Notes

All walkthroughs, explanations, and documentation in this repository are written in my own words and reflect my personal methodology and understanding of the techniques applied during the engagement.
