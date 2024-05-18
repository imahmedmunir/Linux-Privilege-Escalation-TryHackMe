## The remote host is running a Telnet service that allows cleartext logins over unencrypted connections. An attacker can uncover login names and passwords by sniffing traffic to the Telnet service.

### Take down the telnet service.
### Take down the service in port 69/udp.

### you can stop the telnet service or remove it using "systemctl stop telnet" or "sudo apt remove telnet"



### What other cleartext service is running on port 69/udp?
Answer: tftp

Solution: in order to find what's running on port 69, use the command 

thm@ip-10-10-29-68:~$ sudo lsof -i :69
COMMAND PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
inetd   479 root    8u  IPv4  20399      0t0  UDP *:tftp 



### What is the cleartext_services flag?
Answer: THM{33704d74ec53c8cf50daf817bea836a1}

Solution: as we've two task , firstly we checked the name of service running on 69 port and it's tftp. Now , we've to stop this service by using following commands and get flag.
hm@ip-10-10-29-68:~$ sudo systemctl stop inetd 
thm@ip-10-10-29-68:~$ get-flags
{
  "ssh_weak_ciphers": "VULN",
  "ssh_weak_kex": "VULN",
  "ssh_weak_macs": "VULN",
  "redis_nopass": "THM{ae4e5bb7aac2c2252363ca466f10ffd0}",
  "redis_port_public": "VULN",
  "mysql_port_public": "VULN",
  "snmp_public": "THM{aa397a808d527fd71f023c78d3c04591}",
  "nginx_asroot": "THM{bebb02b22bb56b2f79ba706975714ee2}",
  "unused_accounts": "VULN",
  "change_pass": "VULN",
  "sudoers_mary": "VULN",
  "sudoers_munra": "VULN",
  "cleartext_services": "THM{33704d74ec53c8cf50daf817bea836a1}",
  "anon_ftp": "VULN"
}


