# Identifying Users

### Kerbrute - Internal AD Username Enumeration

This resource contains wordlists for creating statistically likely usernames for use in username-enumeration, simulated password-attacks, and other security testing tasks.

{% embed url="https://github.com/ropnop/kerbrute/releases/tag/v1.0.3" %}

Usernames Wordlist: [https://github.com/insidetrust/statistically-likely-usernames](https://github.com/insidetrust/statistically-likely-usernames)

```
./kerbrute_linux_amd64 
```

```
echo $PATH
```

```
sudo mv kerbrute_linux_amd64 /usr/local/bin/kerbrute
```

```
kerbrute userenum -d INLANEFREIGHT.LOCAL --dc 172.16.5.5 jsmith.txt -o valid_ad_users
```

There are several ways to gain SYSTEM-level access on a host, including but not limited to:

* Remote Windows exploits such as MS08-067, EternalBlue, or BlueKeep.
* Abusing a service running in the context of the `SYSTEM account`, or abusing the service account `SeImpersonate` privileges using [Juicy Potato](https://github.com/ohpe/juicy-potato). This type of attack is possible on older Windows OS' but not always possible with Windows Server 2019.
* Local privilege escalation flaws in Windows operating systems such as the Windows 10 Task Scheduler 0-day.
* Gaining admin access on a domain-joined host with a local account and using Psexec to launch a SYSTEM cmd window

By gaining SYSTEM-level access on a domain-joined host, you will be able to perform actions such as, but not limited to:

* Enumerate the domain using built-in tools or offensive tools such as BloodHound and PowerView.
* Perform Kerberoasting / ASREPRoasting attacks within the same domain.
* Run tools such as Inveigh to gather Net-NTLMv2 hashes or perform SMB relay attacks.
* Perform token impersonation to hijack a privileged domain user account.
* Carry out ACL attacks.
