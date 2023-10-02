# 🟢 POP3

**POP3 Ports**

| Port Number | Description             | Protocol |
| ----------- | ----------------------- | -------- |
| 110         | POP3 (Plain Text)       | TCP/UDP  |
| 995         | POP3 over SSL (TLS/SSL) | TCP      |

Please note that POP3 typically uses TCP (Transmission Control Protocol) for communication, but the table also includes UDP (User Datagram Protocol) as some older implementations might use it. However, UDP is not commonly used for POP3.&#x20;

The secure version of POP3 (POP3S) utilizes SSL/TLS encryption to protect communications.

**POP3 Commands**

| **Command**     | **Description**                                             |
| --------------- | ----------------------------------------------------------- |
| `USER username` | Identifies the user.                                        |
| `PASS password` | Authentication of the user using its password.              |
| `STAT`          | Requests the number of saved emails from the server.        |
| `LIST`          | Requests from the server the number and size of all emails. |
| `RETR id`       | Requests the server to deliver the requested email by ID.   |
| `DELE id`       | Requests the server to delete the requested email by ID.    |
| `CAPA`          | Requests the server to display the server capabilities.     |
| `RSET`          | Requests the server to reset the transmitted information.   |
| `QUIT`          | Closes the connection with the POP3 server.                 |

### Scan POP3 with Nmap

```
sudo nmap 10.129.63.193 -sV -p110,995 -sC
```

### Connect to POP3 Server

```
curl -k 'pop3://10.129.63.193' --user robin:robin
```

```
openssl s_client -connect 10.129.63.193:pop3s
```

```
curl -k 'pop3s://10.129.63.193' --user robin:robin
```

```
openssl s_client -connect 10.129.63.193:995
```

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

### Mutt - Command line Email Client

One of the popular and widely used command-line email clients is "mutt." Mutt allows you to read, send, and manage emails directly from the terminal. Here's how you can use mutt to download emails.

```bash
sudo apt-get update
sudo apt-get install mutt
```

```
vi ~/.muttrc
```

```
set from = "your_email@gmail.com"
set realname = "Your Name"
set imap_user = "your_email@gmail.com"
set imap_pass = "your_gmail_password"
set folder = "imaps://imap.gmail.com/"
set spoolfile = "+INBOX"
set postponed = "+[Gmail]/Drafts"
set header_cache=~/.mutt/cache/headers
set message_cachedir=~/.mutt/cache/bodies
set certificate_file=~/.mutt/certificates
set move = no
```

```
mutt
```

Mutt provides various commands to manage emails.&#x20;

For example:

* `d`: Delete the currently selected email.
* `s`: Save the currently selected email to a mailbox.
* `r`: Reply to the currently selected email.
* `q`: Quit mutt.
