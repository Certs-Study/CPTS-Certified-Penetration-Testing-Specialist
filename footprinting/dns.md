# 🟢 DNS

There are several types of DNS servers that are used worldwide:

* DNS root server
* Authoritative name server
* Non-authoritative name server
* Caching server
* Forwarding server
* Resolver

| **Server Type**                | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `DNS Root Server`              | he root servers of the DNS are responsible for the top-level domains (`TLD`). As the last instance, they are only requested if the name server does not respond. Thus, a root server is a central interface between users and content on the Internet, as it links domain and IP address. The [Internet Corporation for Assigned Names and Numbers](https://www.icann.org/) (`ICANN`) coordinates the work of the root name servers. There are `13` such root servers around the globe. |
| `Authoritative Nameserver`     | Authoritative name servers hold authority for a particular zone. They only answer queries from their area of responsibility, and their information is binding. If an authoritative name server cannot answer a client's query, the root name server takes over at that point.                                                                                                                                                                                                           |
| `Non-authoritative Nameserver` | Non-authoritative name servers are not responsible for a particular DNS zone. Instead, they collect information on specific DNS zones themselves, which is done using recursive or iterative DNS querying.                                                                                                                                                                                                                                                                              |
| `Caching DNS Server`           | Caching DNS servers cache information from other name servers for a specified period. The authoritative name server determines the duration of this storage.                                                                                                                                                                                                                                                                                                                            |
| `Forwarding Server`            | Forwarding servers perform only one function: they forward DNS queries to another DNS server.                                                                                                                                                                                                                                                                                                                                                                                           |
| `Resolver`                     | Resolvers are not authoritative DNS servers but perform name resolution locally in the computer or router.                                                                                                                                                                                                                                                                                                                                                                              |

```
dig soa www.inlanefreight.com
```

### **DIG - NS Query**

```
dig ns inlanefreight.htb @10.129.19.202
```

### **DIG CHAOS - Version Query**

```
dig CH TXT version.bind 10.129.120.85
```

### **DIG - ANY Query**

```
dig any inlanefreight.htb @10.129.14.128
```

### **DIG - AXFR Zone Transfer**

```
dig axfr inlanefreight.htb @10.129.14.128
```

### Sub Domain Enumeration

{% code overflow="wrap" %}
```
dnsenum --dnsserver 10.129.129.164 --enum -p 0 -s 0 -o subdomains.txt -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt inlanefreight.htb
```
{% endcode %}

**DIG - AXFR Zone Transfer - Internal**

```
dig axfr internal.inlanefreight.htb @10.129.172.83
```

**Subdomain Brute Forcing**

{% code overflow="wrap" %}
```bash
for sub in $(cat /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt);do dig $sub.inlanefreight.htb @10.129.129.164 | grep -v ';\|SOA' | sed -r '/^\s*$/d' | grep $sub | tee -a subdomains.txt;done
```
{% endcode %}

### **Querying: PTR Records for an IP Address**

```
nslookup -query=PTR 10.129.129.164
```

```
dig -x 31.13.92.36 @1.1.1.1
```

```
for sub in $(cat /usr/share/seclists/Discovery/DNS/fierce-hostlist.txt);do dig $sub.dev.inlanefreight.htb @10.129.129.164 | grep -v ';\|SOA' | sed -r '/^\s*$/d' | grep $sub | tee -a subdomains.txt;done
dev1.dev.inlanefreight.htb. 604800 IN	A	10.12.3.6
ns.dev.inlanefreight.htb. 604800 IN	A	127.0.0.1
win2k.dev.inlanefreight.htb. 604800 IN	A	10.12.3.203
```
