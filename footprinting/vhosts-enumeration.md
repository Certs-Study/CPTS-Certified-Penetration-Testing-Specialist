# 🟢 vHosts Enumeration

```
curl -s http://192.168.10.10
```

```
curl -s http://192.168.10.10 -H "Host: randomtarget.com"
```

```
/opt/useful/SecLists/Discovery/DNS/namelist.txt
```

{% code overflow="wrap" %}
```
cat ./vhosts | while read vhost;do echo "\n********\nFUZZING: ${vhost}\n********";curl -s -I http://10.129.240.54 -H "HOST: ${vhost}.inlanefreight.htb" | grep "Content-Length: ";done
```
{% endcode %}

```
curl -s http://10.129.240.54 -H "Host: www.inlanefreight.htb"
```

```
ffuf -w ./vhosts -u http://10.129.240.54 -H "HOST: FUZZ.inlanefreight.htb" -fs 612
```

vHosts Enumeration

<pre data-overflow="wrap"><code><strong>ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -H "Host: FUZZ.inlanefreight.htb" -u http://inlanefreight.htb
</strong></code></pre>

{% code overflow="wrap" %}
```
ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -H "Host: FUZZ.inlanefreight.htb" -u http://inlanefreight.htb -fs 1495
```
{% endcode %}
