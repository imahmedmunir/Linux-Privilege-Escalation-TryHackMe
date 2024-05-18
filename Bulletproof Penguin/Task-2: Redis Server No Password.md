# Link on TryHackMe : [Bulletproof Penguin](https://tryhackme.com/r/room/bppenguin)

## IN this room, our job is to fix the vulnerabilites which have already been addressed. 

### What is the redis_nopass flag?
Answer: THM{ae4e5bb7aac2c2252363ca466f10ffd0}

Solution: first you need to find where exactly the redis.conf file is located so that you can edit it. After that we'll edit the file with nano text editor and use ctrl+w to search for requirepass to find the vulnerability. 
We'll remove the comment (#) and save the file and restart the redis server. As informed in task-1, use "get-flags" command to find flag after fixing the vulnerability.

thm@ip-10-10-29-68:~$ find / -type f -name redis.conf 2>/dev/null
/etc/redis/redis.conf

thm@ip-10-10-29-68:~$ sudo nano /etc/redis/redis.conf (edit the file , remove comment from requirepass)

thm@ip-10-10-29-68:~$ sudo systemctl restart redis (restart)

thm@ip-10-10-29-68:~$ get-flags

{
  "ssh_weak_ciphers": "VULN",
  "ssh_weak_kex": "VULN",
  "ssh_weak_macs": "VULN",
  "redis_nopass": "THM{ae4e5bb7aac2c2252363ca466f10ffd0}",
  "redis_port_public": "VULN",
  "mysql_port_public": "VULN",
  "snmp_public": "VULN",
  "nginx_asroot": "VULN",
  "unused_accounts": "VULN",
  "change_pass": "VULN",
  "sudoers_mary": "VULN",
  "sudoers_munra": "VULN",
  "cleartext_services": "VULN",
  "anon_ftp": "VULN"
}


