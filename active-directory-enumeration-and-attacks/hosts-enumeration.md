# Hosts Enumeration

```
sudo -E wireshark
```

```
sudo tcpdump -i ens224 
```

```
sudo responder -I ens224 -A 
```

```
fping -asgq 172.16.5.0/23
```

```
sudo nmap -v -A -iL hosts.txt -oN /home/htb-student/Documents/host-enum
```

```
nmap -A 172.16.5.100
```
