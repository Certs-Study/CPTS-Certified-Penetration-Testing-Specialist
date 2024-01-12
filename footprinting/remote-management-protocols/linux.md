# Linux

### Rsync

```
sudo nmap -sV -p 873 127.0.0.1
```

```
RFS85@htb[/htb]$ nc -nv 127.0.0.1 873

(UNKNOWN) [127.0.0.1] 873 (rsync) open
@RSYNCD: 31.0
@RSYNCD: 31.0
#list
dev            	Dev Tools
@RSYNCD: EXIT
```

```
RFS85@htb[/htb]$ rsync -av --list-only rsync://127.0.0.1/dev

receiving incremental file list
drwxr-xr-x             48 2022/09/19 09:43:10 .
-rw-r--r--              0 2022/09/19 09:34:50 build.sh
-rw-r--r--              0 2022/09/19 09:36:02 secrets.yaml
drwx------             54 2022/09/19 09:43:10 .ssh

sent 25 bytes  received 221 bytes  492.00 bytes/sec
total size is 0  speedup is 0.00
```

The [R-commands](https://en.wikipedia.org/wiki/Berkeley\_r-commands) suite consists of the following programs:

* rcp (`remote copy`)
* rexec (`remote execution`)
* rlogin (`remote login`)
* rsh (`remote shell`)
* rstat
* ruptime
* rwho (`remote who`)

<table data-header-hidden><thead><tr><th></th><th width="168"></th><th width="68"></th><th width="110"></th><th></th></tr></thead><tbody><tr><td><strong>Command</strong></td><td><strong>Service Daemon</strong></td><td><strong>Port</strong></td><td><strong>Transport Protocol</strong></td><td><strong>Description</strong></td></tr><tr><td><code>rcp</code></td><td><code>rshd</code></td><td>514</td><td>TCP</td><td>Copy a file or directory bidirectionally from the local system to the remote system (or vice versa) or from one remote system to another. It works like the <code>cp</code> command on Linux but provides <code>no warning to the user for overwriting existing files on a system</code>.</td></tr><tr><td><code>rsh</code></td><td><code>rshd</code></td><td>514</td><td>TCP</td><td>Opens a shell on a remote machine without a login procedure. Relies upon the trusted entries in the <code>/etc/hosts.equiv</code> and <code>.rhosts</code> files for validation.</td></tr><tr><td><code>rexec</code></td><td><code>rexecd</code></td><td>512</td><td>TCP</td><td>Enables a user to run shell commands on a remote machine. Requires authentication through the use of a <code>username</code> and <code>password</code> through an unencrypted network socket. Authentication is overridden by the trusted entries in the <code>/etc/hosts.equiv</code> and <code>.rhosts</code> files.</td></tr><tr><td><code>rlogin</code></td><td><code>rlogind</code></td><td>513</td><td>TCP</td><td>Enables a user to log in to a remote host over the network. It works similarly to <code>telnet</code> but can only connect to Unix-like hosts. Authentication is overridden by the trusted entries in the <code>/etc/hosts.equiv</code> and <code>.rhosts</code> files.</td></tr></tbody></table>

```
sudo nmap -sV -p 512,513,514 10.0.17.2
```

```
rlogin 10.0.17.2 -l htb-student
```

```
RFS85@htb[/htb]$ rwho
```

```
rusers -al 10.0.17.5
```
