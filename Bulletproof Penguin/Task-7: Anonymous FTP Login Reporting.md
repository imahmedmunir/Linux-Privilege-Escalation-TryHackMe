## There is ftp service provider which easily can give access as described it allows anonymous and ftp login 


### What is the anon_ftp flag?
Answer: THM{f20b5ff5a3d4c779e99c3a93d1f68c6d}


solution: This time look for vsftpd.config file and disable anonymous or delete it. Following are commands to find the file location and edit it.

thm@ip-10-10-29-68:~$ find /etc/ -type f -name *ftp* 2>/dev/null

/etc/vsftpd.conf


thm@ip-10-10-29-68:~$ sudo nano /etc/vsftpd.conf (edit the file )

thm@ip-10-10-29-68:~$ sudo service vsftpd restart
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
  "anon_ftp": "THM{f20b5ff5a3d4c779e99c3a93d1f68c6d}"
}
