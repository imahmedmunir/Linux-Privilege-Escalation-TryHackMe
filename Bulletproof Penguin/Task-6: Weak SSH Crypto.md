
## There three weakness/vulnerabilites to be disabled or removed in order to have no threat over ssh connection

### Weak Key Exchange (KEX) Algorithm(s) Supported (SSH)

### What is the ssh_weak_kex flag?
Answer: THM{d9baf598ee934d79346f425a81bd693a}

Solution: Thek weak ssh key exchange algorithm used is diffi-hellman-group1-sha1

--> find directory of sshd_conf and remove the weak key exchange algorithm or comment it

thm@ip-10-10-29-68:~$ sudo nano  /etc/ssh/sshd_config (open the file and remove diffi-hellman algorithm)
thm@ip-10-10-29-68:~$ sudo systemctl restart sshd (restart ssh and get flag for weak key exchange)
thm@ip-10-10-29-68:~$ get-flags
{
  "ssh_weak_ciphers": "VULN",
  "ssh_weak_kex": "THM{d9baf598ee934d79346f425a81bd693a}",
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



### What is the ssh_weak_ciphers flag?
Answer: THM{9ff9c182cad601291d45951c01d0b2c7

Solution: as in first question, we remove weak key exchange algorithm. Now we have to remove 3 weak encryption algorithms from the "sshd_conf" file. After that , repeat the same procedure to restart ssh service and get the flag

thm@ip-10-10-29-68:~$ sudo nano  /etc/ssh/sshd_config
thm@ip-10-10-29-68:~$ sudo service sshd restart
thm@ip-10-10-29-68:~$ get-flags
{
  "ssh_weak_ciphers": "THM{9ff9c182cad601291d45951c01d0b2c7}",
  "ssh_weak_kex": "THM{d9baf598ee934d79346f425a81bd693a}",
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

### What is the ssh_weak_macs flag?
Answer: THM{e3d6b82f291b64f95213583dcd89b659}

Solution: Repeat the same procedure and open the ssh_config file to remove "hmac-md5-96" which is weal algorithm for message authentication code
thm@ip-10-10-29-68:~$ sudo nano  /etc/ssh/sshd_config
thm@ip-10-10-29-68:~$ sudo service sshd restart
thm@ip-10-10-29-68:~$ get-flags
{
  "ssh_weak_ciphers": "THM{9ff9c182cad601291d45951c01d0b2c7}",
  "ssh_weak_kex": "THM{d9baf598ee934d79346f425a81bd693a}",
  "ssh_weak_macs": "THM{e3d6b82f291b64f95213583dcd89b659}",
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
thm@ip-10-10-29-68:~$ 


