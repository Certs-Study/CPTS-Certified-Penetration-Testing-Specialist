---
description: Pentesting Internet Message Access Protocol port 143 or 993
---

# 🟢 IMAP

### **IMAP Commands**

| **Command**                     | **Description**                                                                                               |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `1 LOGIN username password`     | User's login.                                                                                                 |
| `1 LIST "" *`                   | Lists all directories.                                                                                        |
| `1 CREATE "INBOX"`              | Creates a mailbox with a specified name.                                                                      |
| `1 DELETE "INBOX"`              | Deletes a mailbox.                                                                                            |
| `1 RENAME "ToRead" "Important"` | Renames a mailbox.                                                                                            |
| `1 LSUB "" *`                   | Returns a subset of names from the set of names that the User has declared as being `active` or `subscribed`. |
| `1 SELECT INBOX`                | Selects a mailbox so that messages in the mailbox can be accessed.                                            |
| `1 UNSELECT INBOX`              | Exits the selected mailbox.                                                                                   |
| `1 FETCH <ID> all`              | Retrieves data associated with a message in the mailbox.                                                      |
| `1 CLOSE`                       | Removes all messages with the `Deleted` flag set.                                                             |
| `1 LOGOUT`                      | Closes the connection with the IMAP server.                                                                   |

### IMAP Port Numbers

| Port Number | Description             | Protocol |
| ----------- | ----------------------- | -------- |
| 143         | IMAP (Plain Text)       | TCP/UDP  |
| 993         | IMAP over SSL (TLS/SSL) | TCP      |

### Scan IMAP using Nmap

```
sudo nmap 10.129.14.128 -sV -p110,143,993,995 -sC
```

### Authenticate in Plain Text

```
curl -k 'imap://10.129.14.128' --user robin:robin -v
```

### Authenticate using SSL/TLS

```
curl -k 'imaps://10.129.14.128' --user robin:robin -v
```

### Interact with IMAP Server

To interact with the IMAP or POP3 server over SSL, we can use `openssl`, as well as `ncat.`

```
openssl s_client -connect 10.129.172.83:imaps
```

```
nmap -v -sV --version-intensity=5 --script imap-capabilities -p T:143 10.129.172.83
```

```
openssl s_client -connect 10.129.189.29:imaps
1 LOGIN robin robin
1 LIST "" *
1 LIST "" "%"
1 SELECT INBOX
1 FETCH 1 all
1 SELECT DEV.DEPARTMENT.INT
1 FETCH 1 all
A1 STATUS INBOX (MESSAGES UNSEEN RECENT)
1 FETCH 1 body[text]
```
