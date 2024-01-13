# Introduction

### Authentication

Authentication, at its core, is the validation of your identity by presenting a combination of three main factors to a validation mechanism. They are;

1. Something you know (a password, passcode, pin, etc.).
2. Something you have (an ID Card, security key, or other MFA tools).
3. Something you are (your physical self, username, email address, or other identifiers.)

### Linux

| **ID**   | **Cryptographic Hash Algorithm**                                      |
| -------- | --------------------------------------------------------------------- |
| `$1$`    | [MD5](https://en.wikipedia.org/wiki/MD5)                              |
| `$2a$`   | [Blowfish](https://en.wikipedia.org/wiki/Blowfish\_\(cipher\))        |
| `$5$`    | [SHA-256](https://en.wikipedia.org/wiki/SHA-2)                        |
| `$6$`    | [SHA-512](https://en.wikipedia.org/wiki/SHA-2)                        |
| `$sha1$` | [SHA1crypt](https://en.wikipedia.org/wiki/SHA-1)                      |
| `$y$`    | [Yescrypt](https://github.com/openwall/yescrypt)                      |
| `$gy$`   | [Gost-yescrypt](https://www.openwall.com/lists/yescrypt/2019/06/30/1) |
| `$7$`    | [Scrypt](https://en.wikipedia.org/wiki/Scrypt)                        |

**Windows Authentication Process Diagram**

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

### **LSASS**

[Local Security Authority Subsystem Service](https://en.wikipedia.org/wiki/Local\_Security\_Authority\_Subsystem\_Service) (`LSASS`) is a collection of many modules and has access to all authentication processes that can be found in `%SystemRoot%\System32\Lsass.exe`

| **Authentication Packages** | **Description**                                                                                                                                                                                                                                                |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Lsasrv.dll`                | The LSA Server service both enforces security policies and acts as the security package manager for the LSA. The LSA contains the Negotiate function, which selects either the NTLM or Kerberos protocol after determining which protocol is to be successful. |
| `Msv1_0.dll`                | Authentication package for local machine logons that don't require custom authentication.                                                                                                                                                                      |
| `Samsrv.dll`                | The Security Accounts Manager (SAM) stores local security accounts, enforces locally stored policies, and supports APIs.                                                                                                                                       |
| `Kerberos.dll`              | Security package loaded by the LSA for Kerberos-based authentication on a machine.                                                                                                                                                                             |
| `Netlogon.dll`              | Network-based logon service.                                                                                                                                                                                                                                   |
| `Ntdsa.dll`                 | This library is used to create new records and folders in the Windows registry.                                                                                                                                                                                |

### **SAM Database**

The [Security Account Manager](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc756748\(v=ws.10\)?redirectedfrom=MSDN) (`SAM`) is a database file in Windows operating systems that stores users' passwords. It can be used to authenticate local and remote users.&#x20;

This file is located in `%SystemRoot%/system32/config/SAM` and is mounted on HKLM/SAM. SYSTEM level permissions are required to view it.

the Domain Controller (`DC`) must validate the credentials from the Active Directory database (`ntds.dit`), which is stored in `%SystemRoot%\ntds.dit`.

\


\
Credential Manager

```powershell-session
PS C:\Users\[Username]\AppData\Local\Microsoft\[Vault/Credentials]\
```

**NTDS**

* User accounts (username & password hash)
* Group accounts
* Computer accounts
* Group policy objects
