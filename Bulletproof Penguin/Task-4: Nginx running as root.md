## he nginx server is running as user "root". An attacker could leverage this to gain privileged access to the server by abusing a vulnerable web application hosted by nginx.
## An attacker might abuse the vulnerablilites hosted by nginx server to get access to server. So, change the user from root to suggested user


### What is the nginx_asroot flag?
Answer: THM{bebb02b22bb56b2f79ba706975714ee2}"


Solution: firstly find the nginx.conf file location , edit it by change user root to suggested "www-data" user. As you open the configuration file, first thing is the user. Change the user and restart the server

thm@ip-10-10-29-68:~$ find / -type f -name nginx.conf 2>/dev/null
/etc/nginx/nginx.conf
thm@ip-10-10-29-68:~$ sudo nano /etc/nginx/nginx.conf 
thm@ip-10-10-29-68:~$ sudo systemctl restart nginx.service
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
  "cleartext_services": "VULN",
  "anon_ftp": "VULN"
}
