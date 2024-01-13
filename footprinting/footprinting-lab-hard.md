# Footprinting Lab - Hard



{% code overflow="wrap" %}
```
nmap -sV -sC 10.129.179.145

PORT    STATE SERVICE
22/tcp  open  ssh
110/tcp open  pop3
143/tcp open  imap
993/tcp open  imaps
995/tcp open  pop3s
```
{% endcode %}

### SSH

```
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.2p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
```

### IMAP

{% code overflow="wrap" %}
```
143/tcp open  imap     Dovecot imapd (Ubuntu)
| ssl-cert: Subject: commonName=NIXHARD
|_imap-capabilities: more ENABLE IDLE post-login have listed LITERAL+ Pre-login SASL-IR capabilities ID STARTTLS LOGIN-REFERRALS IMAP4rev1 AUTH=PLAINA0001 OK

993/tcp open  ssl/imap Dovecot imapd (Ubuntu)
|_imap-capabilities: ENABLE IDLE more have listed LITERAL+ Pre-login SASL-IR post-login capabilities AUTH=PLAINA0001 LOGIN-REFERRALS IMAP4rev1 ID OK
```
{% endcode %}

```
sudo nmap 10.129.179.145 -sV -p110,143,993,995 -sC
```

```
openssl s_client -connect 10.129.179.145:imaps
```

### POP3

{% code overflow="wrap" %}
```
110/tcp open  pop3     Dovecot pop3d
| ssl-cert: Subject: commonName=NIXHARD
|_pop3-capabilities: STLS RESP-CODES UIDL PIPELINING CAPA AUTH-RESP-CODE USER SASL(PLAIN) TOP

995/tcp open  ssl/pop3 Dovecot pop3d
|_pop3-capabilities: SASL(PLAIN) RESP-CODES CAPA TOP AUTH-RESP-CODE USER PIPELINING UIDL
```
{% endcode %}

```
curl -k 'pop3://10.129.179.145' 
```
