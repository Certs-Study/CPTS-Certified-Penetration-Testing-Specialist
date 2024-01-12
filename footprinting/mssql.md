---
description: o
---

# 🟢 MSSQL

<table data-full-width="false"><thead><tr><th></th><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td><a href="https://docs.microsoft.com/en-us/sql/tools/mssql-cli?view=sql-server-ver15">mssql-cli</a></td><td><a href="https://docs.microsoft.com/en-us/sql/powershell/sql-server-powershell?view=sql-server-ver15">SQL Server PowerShell</a></td><td><a href="https://www.heidisql.com/">HeidiSQL</a></td><td><a href="https://www.macsqlclient.com/">SQLPro</a></td><td><a href="https://github.com/SecureAuthCorp/impacket/blob/master/examples/mssqlclient.py">Impacket's mssqlclient.py</a></td></tr></tbody></table>

```
[msf](Jobs:0 Agents:0) auxiliary(admin/mssql/mssql_enum) >> use scanner/mssql/mssql_ping
[msf](Jobs:0 Agents:0) auxiliary(scanner/mssql/mssql_ping) >> set rhosts 10.129.201.248
rhosts => 10.129.201.248
[msf](Jobs:0 Agents:0) auxiliary(scanner/mssql/mssql_ping) >> run

[*] 10.129.201.248:       - SQL Server information for 10.129.201.248:
[+] 10.129.201.248:       -    ServerName      = ILF-SQL-01
[+] 10.129.201.248:       -    InstanceName    = MSSQLSERVER
[+] 10.129.201.248:       -    IsClustered     = No
[+] 10.129.201.248:       -    Version         = 15.0.2000.5
[+] 10.129.201.248:       -    tcp             = 1433
[+] 10.129.201.248:       -    np              = \\ILF-SQL-01\pipe\sql\query
[*] 10.129.201.248:       - Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed

```

```
[msf](Jobs:0 Agents:0) auxiliary(scanner/mssql/mssql_ping) >> use admin/mssql/mssql_enum
[msf](Jobs:0 Agents:0) auxiliary(admin/mssql/mssql_enum) >> options 

Module options (auxiliary/admin/mssql/mssql_enum):

   Name                 Current Setting  Required  Description
   ----                 ---------------  --------  -----------
   PASSWORD             Password1        no        The password for the specified username
   RHOSTS               10.129.201.248   yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.html
   RPORT                1433             yes       The target port (TCP)
   TDSENCRYPTION        false            yes       Use TLS/SSL for TDS data "Force Encryption"
   USERNAME             backdoor         no        The username to authenticate as
   USE_WINDOWS_AUTHENT  false            yes       Use windows authentification (requires DOMAIN option set)


View the full module info with the info, or info -d command.

[msf](Jobs:0 Agents:0) auxiliary(admin/mssql/mssql_enum) >> set USE
set USERNAME             set USE_WINDOWS_AUTHENT  
[msf](Jobs:0 Agents:0) auxiliary(admin/mssql/mssql_enum) >> set USE_WINDOWS_AUTHENT true
USE_WINDOWS_AUTHENT => true
[msf](Jobs:0 Agents:0) auxiliary(admin/mssql/mssql_enum) >> run
```
