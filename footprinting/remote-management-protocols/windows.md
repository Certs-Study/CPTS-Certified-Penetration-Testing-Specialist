# Windows

The main components used for remote management of Windows and Windows servers are the following:

* Remote Desktop Protocol (`RDP`)
* Windows Remote Management (`WinRM`)
* Windows Management Instrumentation (`WMI`)

### RDP

```
nmap -sV -sC 10.129.201.248 -p3389 --script rdp*
```

```
nmap -sV -sC 10.129.201.248 -p3389 --packet-trace --disable-arp-ping -n
```

We can see that the `RDP cookies` (`mstshash=nmap`) used by Nmap to interact with the RDP server can be identified by `threat hunters` and various security services such as [Endpoint Detection and Response](https://en.wikipedia.org/wiki/Endpoint\_detection\_and\_response) (`EDR`), and can lock us out as penetration testers on hardened networks.

**RDP Security Check**

{% code overflow="wrap" %}
```
RFS85@htb[/htb]$ git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check
RFS85@htb[/htb]$ ./rdp-sec-check.pl 10.129.201.248
```
{% endcode %}

```
xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248
```

### WinRM

```
nmap -sV -sC 10.129.201.248 -p5985,5986 --disable-arp-ping -n
```

```
evil-winrm -i 10.129.201.248 -u Cry0l1t3 -p P455w0rD!
```

{% embed url="https://docs.microsoft.com/en-us/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-7.2" %}

### WMI

{% code overflow="wrap" %}
```
/usr/share/doc/python3-impacket/examples/wmiexec.py Cry0l1t3:"P455w0rD!"@10.129.201.248 "hostname"
```
{% endcode %}
