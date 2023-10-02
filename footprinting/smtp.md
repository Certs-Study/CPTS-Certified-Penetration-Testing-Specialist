---
description: Pentesting SMTP for CPTS
---

# 🟢 SMTP

### The Basics of SMTP

SMTP, the Simple Mail Transfer Protocol, is a set of rules that govern how electronic mail is transmitted and received over the Internet. It's the standard protocol used for sending and relaying emails between servers. The process involves multiple components, one of which is the use of specific ports to facilitate communication.

### SMTP Ports Explained

Ports are communication endpoints in a computer network, and they enable data exchange between different applications. SMTP utilizes specific ports to handle various aspects of email communication. Let's take a closer look at the primary SMTP ports:

| Port Number | Description                 | Security    |
| ----------- | --------------------------- | ----------- |
| 25          | Traditional SMTP Port       | Unencrypted |
| 587         | Submission Port             | StartTLS    |
| 465         | SSL/TLS Encrypted Port      | SSL/TLS     |
| 2525        | Unofficial Alternative Port | Unencrypted |

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

**Default Configuration**

```
cat /etc/postfix/main.cf | grep -v "#" | sed -r "/^\s*$/d"
```

### SMTP Commands

| Command      | Description                                                                                                               | Example                                                                                                                               |
| ------------ | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| EHLO/HELO    | Initiates the conversation with the server and identifies the client. EHLO is an extended version of the HELO command.    | EHLO example.com                                                                                                                      |
| MAIL FROM    | Specifies the sender's email address.                                                                                     | MAIL FROM: [sender@example.com](mailto:sender@example.com)                                                                            |
| RCPT TO      | Specifies the recipient's email address. This command can be repeated to specify multiple recipients.                     | RCPT TO: [recipient1@example.com](mailto:recipient1@example.com)\<br>RCPT TO: [recipient2@example.com](mailto:recipient2@example.com) |
| DATA         | Indicates the start of the email message data. The email content, including headers and body, is sent after this command. | DATA                                                                                                                                  |
| Subject      | Sets the subject of the email.                                                                                            | Subject: This is the subject of the email                                                                                             |
| From         | Specifies the sender's name or organization.                                                                              | From: John Doe [sender@example.com](mailto:sender@example.com)                                                                        |
| To           | Specifies the recipient's name or organization.                                                                           | To: Jane Smith [recipient@example.com](mailto:recipient@example.com)                                                                  |
| CC           | Sets carbon copy recipients.                                                                                              | CC: [cc@example.com](mailto:cc@example.com)                                                                                           |
| BCC          | Sets blind carbon copy recipients. BCC recipients are not visible to other recipients.                                    | BCC: [bcc@example.com](mailto:bcc@example.com)                                                                                        |
| Date         | Specifies the date and time the email was composed.                                                                       | Date: Wed, 28 Jul 2023 12:00:00 +0000                                                                                                 |
| Reply-To     | Specifies the email address to which replies should be sent.                                                              | Reply-To: [replyto@example.com](mailto:replyto@example.com)                                                                           |
| Content-Type | Defines the type and encoding of the email content.                                                                       | Content-Type: text/plain; charset="utf-8"                                                                                             |
| QUIT         | Closes the connection with the SMTP server.                                                                               | QUIT                                                                                                                                  |

Remember that when interacting with an SMTP server using these commands, each command should be followed by a newline character (CRLF) to properly terminate the command.

### Open Relay

```
sudo nmap 10.129.14.128 -p25 --script smtp-open-relay -v
```

### The Significance of Encryption

In today's cybersecurity landscape, data privacy and protection are paramount. SMTP supports encryption methods such as SSL (Secure Sockets Layer) and TLS (Transport Layer Security) to secure email transmissions. Encryption ensures that sensitive information, including email content and user credentials, remains encrypted and safe from prying eyes during transit.

### SMTP Pentesting Tools

| Tool                 | Description                                                                                        |
| -------------------- | -------------------------------------------------------------------------------------------------- |
| Metasploit Framework | A powerful penetration testing tool with various SMTP modules for testing vulnerabilities.         |
| Nmap                 | A versatile network scanner to identify open SMTP ports and perform basic enumeration.             |
| OpenVAS              | A vulnerability scanner to identify weaknesses in SMTP servers and configurations.                 |
| smtp-user-enum       | A tool for SMTP user enumeration to identify valid email addresses on a target server.             |
| Sendmail             | A mail transfer agent to simulate SMTP communication and test SMTP server security.                |
| Netcat (nc)          | A general-purpose networking utility to interact with SMTP servers and manually test for vulns.    |
| Swaks                | A feature-rich SMTP testing tool to send custom emails, test authentication, and check for relays. |
| MailSniper           | An open-source tool for searching through email inboxes and performing SMTP-related attacks.       |
| Enum4linux           | Originally for SMB, can also be used for SMTP user enumeration in specific scenarios.              |
| EHLO/HELO Testing    | Basic SMTP testing using telnet to connect to the server and manually issue EHLO/HELO commands.    |

Remember to use these tools responsibly and with proper authorization to avoid legal and ethical issues. Happy and ethical penetration testing!

### SMTP Attacks

| Attack Type                 | Description                                                                                                                                 |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Email Spoofing              | Forging the sender's email address to appear as if it's from a different source.                                                            |
| Email Phishing              | Sending deceptive emails to trick recipients into revealing sensitive information.                                                          |
| Man-in-the-Middle (MITM)    | Intercepting and possibly altering communication between the email client and server.                                                       |
| Brute-Force Attacks         | Repeatedly attempting different username and password combinations to gain unauthorized access.                                             |
| Email Bombing               | Flooding an email inbox with an overwhelming number of emails, causing denial of service.                                                   |
| Email Relay Attacks         | Exploiting open email relays to send spam or malicious emails through a compromised server.                                                 |
| SMTP User Enumeration       | Determining valid email addresses by exploiting SMTP server responses.                                                                      |
| SMTP Command Injection      | Manipulating SMTP commands to execute arbitrary code on the SMTP server.                                                                    |
| SMTP Header Injection       | Injecting malicious content into email headers to trick email clients into unintended actions.                                              |
| Denial of Service (DoS)     | Overwhelming SMTP servers with excessive traffic, causing email service disruption.                                                         |
| Email Harvesting            | Using automated tools to gather email addresses for spam campaigns or other malicious purposes.                                             |
| Email Eavesdropping         | Intercepting unencrypted emails during transmission to access sensitive information.                                                        |
| Email Attachment Exploits   | Exploiting vulnerabilities in email attachments to execute malware on the recipient's system.                                               |
| Malicious Email Attachments | Sending attachments or links to infected files or websites to trick recipients into downloading malware or revealing sensitive information. |

It's essential to stay aware of these attack types and implement appropriate security measures to protect against SMTP-based threats.

### How to send an Email using Telnet?

```
telnet 10.129.14.128 25
```

### Footprinting the SMTP Service

```
sudo nmap 10.129.172.83 -sC -sV -p25
```

**Nmap - Open Relay**

```
sudo nmap 10.129.14.128 -p25 --script smtp-open-relay -v
```

### Enumerate SMTP Users

```
smtp-user-enum -M VRFY -U list.txt -t 10.129.172.83
```

Sometimes we may have to work through a web proxy. We can also make this web proxy connect to the SMTP server. The command that we would send than would look something like this:&#x20;

```
CONNECT 10.129.14.128:25 HTTP/1.0
```

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>



{% file src="../.gitbook/assets/footprinting-wordlist.txt" %}
