## Simple Network Management Protocol (SNMP) is a protocol which can be used by administrators to remotely manage a computer or network device. There are typically 2 modes of remote SNMP monitoring. These modes are roughly 'READ' and 'WRITE' (or PUBLIC and PRIVATE).

## If an attacker is able to guess a PUBLIC community string, they would be able to read SNMP data (depending on which MIBs are installed) from the remote device. This information might include system time, IP addresses, interfaces, processes running, etc.


### What is the snmp_public flag?
Answer: THM{aa397a808d527fd71f023c78d3c04591}

Solution: as it's told that snmp should not be public as it can be vulnerable. However , the decide solution of snmpv3 is also not supported right now. Next solution is just to change the configuration from public to private or assign specific name.

find the snmpd.conf file and edit the following lines : 
from : 
Read-only access to everyone to the systemonly view
rocommunity  Public  default -V systemonly
rocommunity6 Public  default -V systemonly

to: 
# Read-only access to everyone to the systemonly view
rocommunity  Test123  default -V systemonly
rocommunity6 Test2  default -V systemonly



thm@ip-10-10-29-68:~$ ls -la /etc/snmp/
total 16
drwxr-xr-x   2 root root 4096 Sep  7  2023 .
drwxr-xr-x 112 root root 4096 May 18 11:59 ..
-rw-r--r--   1 root root  510 Jun 23  2020 snmp.conf
-rw-------   1 root root 3021 Jul 14  2023 snmpd.conf
thm@ip-10-10-29-68:~$ sudo nano /etc/snmp/snmpd.conf 
[sudo] password for thm: 
Sorry, try again.
[sudo] password for thm: 
thm@ip-10-10-29-68:~$ get-flags
{
  "ssh_weak_ciphers": "VULN",
  "ssh_weak_kex": "VULN",
  "ssh_weak_macs": "VULN",
  "redis_nopass": "THM{ae4e5bb7aac2c2252363ca466f10ffd0}",
  "redis_port_public": "VULN",
  "mysql_port_public": "VULN",
  "snmp_public": "THM{aa397a808d527fd71f023c78d3c04591}",
  "nginx_asroot": "VULN",
  "unused_accounts": "VULN",
  "change_pass": "VULN",
  "sudoers_mary": "VULN",
  "sudoers_munra": "VULN",
  "cleartext_services": "VULN",
  "anon_ftp": "VULN"
}

