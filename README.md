# 🔐 Cybersecurity Home Lab Environment

A complete virtual penetration testing lab built from scratch for hands-on security training and certification preparation.

![Lab Architecture](screenshots/lab-setup/18-final-lab-architecture.png)

## 📋 Overview

Virtual cybersecurity lab environment designed for offensive security practice, defensive monitoring, and incident response training. Built using VMware Workstation Pro on EndeavourOS Linux with isolated network segmentation for safe exploitation scenarios.

## 🏗️ Architecture

**Host System:**
- OS: EndeavourOS Linux (Arch-based) + KDE Plasma
- Virtualization: VMware Workstation Pro 17.6.4
- Hardware: AMD Ryzen 7 9800X3D, 64GB DDR5-6400
- Network: NAT (192.168.161.0/24)

**Virtual Machines:**

| VM | OS | Role | IP | Specs |
|----|----|------|-----|-------|
| Kali Linux | Kali 2025.4 | Attack Platform | .128 | 4GB RAM, 2 cores |
| Metasploitable 2 | Ubuntu 8.04 | Vulnerable Target | .129 | 512MB RAM, 1 core |
| WIN10-PC1 | Windows 10 Pro | Domain Client | .130 | 4GB RAM, 2 cores |
| WIN10-PC2 | Windows 10 Pro | Domain Client | .132 | 4GB RAM, 2 cores |
| WIN10-PC3 | Windows 10 Pro | Domain Client | .133 | 4GB RAM, 2 cores |
| Security Onion | Ubuntu-based | SIEM/IDS | .20 | 8GB RAM, 4 cores |
| DC01 | Windows Server 2022 | Domain Controller | .10 | 4GB RAM, 2 cores |

## 🎯 Scenarios Completed

### 1. Metasploitable 2 Exploitation
**Objective:** Compromise target and obtain root access

**Attack Chain:**
- Reconnaissance: `nmap -sV` discovered vsftpd 2.3.4
- Exploitation: Metasploit Framework (CVE-2011-2523)
- Post-Exploitation: Root shell access, system enumeration

**Result:** ✅ Full system compromise

**Tools:** nmap, Metasploit Framework, meterpreter

[📄 Full Documentation](docs/scenarios/scenario-1.txt)

![Exploitation Success](screenshots/exploitation/Screenshot_20260410_131505.png)

---

### 2. Windows SMB Enumeration
**Objective:** Discover and access network shares

**Attack Chain:**
- Port Scanning: Identified SMB ports (139, 445)
- Share Discovery: `smbclient` enumeration
- Access: Authenticated with weak credentials
- File Operations: Upload/download capability

**Result:** ✅ File-level access to shares

**Tools:** nmap, smbclient, PowerShell

[📄 Full Documentation](docs/scenarios/scenario-2.txt)

![SMB Access](screenshots/exploitation/Screenshot_20260410_144151.png)

---

### 3. Network Traffic Analysis
**Objective:** Capture and analyze attack signatures

**Activities:**
- Traffic Capture: Wireshark on attack interface
- Attack Re-execution: vsftpd exploitation while capturing
- Analysis: FTP protocol inspection, backdoor connection identification
- Signature Detection: TCP stream analysis

**Result:** ✅ Attack patterns identified

**Tools:** Wireshark, tcpdump, display filters

[📄 Full Documentation](docs/scenarios/scenario-3.txt)

![Wireshark Analysis](screenshots/network-analysis/17-tcp-stream.png)

## 🛠️ Skills Demonstrated
---

### 4. Kerberoasting Attack
**Objective:** Extract and crack Kerberos service tickets from Active Directory

**Attack Chain:**
- Setup: Created service account (sqlsvc) with SPN
- Ticket Extraction: `impacket-GetUserSPNs` to request Kerberos tickets
- Password Cracking: Hashcat with rockyou.txt wordlist

**Result:** ✅ Password cracked — `Password@123`

**Tools:** impacket-GetUserSPNs, hashcat

[📄 Full Documentation](docs/scenarios/scenario-4.txt)

---

### 5. Pass-the-Hash Attack
**Objective:** Authenticate to Domain Controller using NTLM hash

**Attack Chain:**
- Hash Extraction: `impacket-secretsdump` dumped all domain hashes
- Authentication: `crackmapexec` used hash without knowing password

**Result:** ✅ Pwn3d! — Full domain compromise

**Tools:** impacket-secretsdump, crackmapexec

[📄 Full Documentation](docs/scenarios/scenario-5.txt)


**Offensive Security:**
- Network reconnaissance and enumeration
- Vulnerability exploitation (Metasploit Framework)
- Post-exploitation techniques
- Credential harvesting
- Lateral movement preparation

**Defensive Security:**
- Network traffic analysis
- Attack signature identification
- SIEM deployment (Security Onion)
- Incident detection methodology

**System Administration:**
- Linux administration (Arch/Debian-based)
- Windows 10 configuration
- VMware virtualization
- Network segmentation (NAT)

**OPSEC Implementation:**
- MAC address randomization
- Tor integration
- Command history obfuscation
- Timezone masking (UTC)

## 🔍 Key Findings

**Vulnerabilities Identified:**
- [CRITICAL] vsftpd 2.3.4 Backdoor (CVE-2011-2523)
- [HIGH] Weak SMB share permissions
- [MEDIUM] Plaintext protocol usage (FTP)
- [MEDIUM] Windows Firewall disabled

**Security Recommendations:**
- Update vulnerable services
- Implement strong authentication
- Enable SMB signing
- Deploy network monitoring (IDS/SIEM)
- Use encrypted protocols (SFTP/SSH)

[📄 Complete Findings Report](docs/findings.txt)

## 📚 Documentation

- [Lab Architecture](docs/architecture.txt)
- [Security Findings](docs/findings.txt)
- [Scenario 1: Metasploitable](docs/scenarios/scenario-1.txt)
- [Scenario 2: Windows SMB](docs/scenarios/scenario-2.txt)
- [Scenario 3: Traffic Analysis](docs/scenarios/scenario-3.txt)

## 🎓 Certification Preparation

This lab supports preparation for:
- ✅ eCIR (EC-Council Certified Incident Responder)
- ✅ eCDFP (Certified Digital Forensics Professional)
- ✅ eCTHP (Certified Threat Hunting Professional)
- ✅ CEH (Certified Ethical Hacker)
- ✅ OSCP (Offensive Security Certified Professional)

**Skills align with:**
- SOC Analyst Level 1
- Junior Penetration Tester
- Security Operations roles

## 🔧 Tools Used

**Offensive:**
- Kali Linux 2025.4
- Metasploit Framework
- nmap
- smbclient
- meterpreter

**Defensive:**
- Wireshark
- Security Onion
- tcpdump

**Infrastructure:**
- VMware Workstation Pro 17.6.4
- EndeavourOS Linux

## 📊 Statistics

- **VMs Deployed:** 7
- **Scenarios Completed:** 5
- **Systems Compromised:** 2/2 targets (100%)
- **Screenshots:** 30+
- **Documentation Pages:** 5
- **PCAP Files:** 1

## 🚀 Future Enhancements

- [ ] Complete Security Onion SIEM deployment
- [ ] Additional attack scenarios (privilege escalation, persistence)
- [ ] Blue team exercises (incident response, forensics)
- [ ] Automated attack scripts

## 📝 License

This project is for educational purposes only. Do not use these techniques on systems you don't own or have explicit permission to test.

## 🤝 Connect

**LinkedIn:** [https://www.linkedin.com/in/bandar-amer/]
**GitHub:** [https://github.com/bandaramergit/]
**Portfolio:** [https://bandaramer.com/]

---

Built with 🔒 for cybersecurity education and hands-on learning.
