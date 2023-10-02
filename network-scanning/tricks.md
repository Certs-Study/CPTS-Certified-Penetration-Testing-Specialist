# 🟢 Tricks

```
--stats-every=5s	Shows the progress of the scan every 5 seconds.
```

```
--script banner,smtp-commands	Uses specified NSE scripts.
```

{% code overflow="wrap" %}
```
-A	Performs service detection, OS detection, traceroute and uses defaults scripts to scan the target.
```
{% endcode %}

```
sudo nmap 10.129.2.28 -p 80 -sV --script vuln 
```

```
-O	Performs operation system detection scan.
-S	Scans the target by using different source IP address.
```

SYN-Scan From DNS Port

{% code overflow="wrap" %}
```shell-session
sudo nmap 10.129.2.28 -p50000 -sS -Pn -n --disable-arp-ping --packet-trace --source-port 53
```
{% endcode %}
