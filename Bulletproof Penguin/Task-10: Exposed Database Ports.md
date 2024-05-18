## While not a vulnerability in itself, exposing database ports makes them prone to brute-force attacks and other exploits. Ensure that access to the reported database ports is restricted to the minimum necessary.

### What is the mysql_port_public flag?
Answer: HM{526e33142b54e13bb47b17056823ab60

Solution: edit the following mysql configuration file and restart the mysql server

thm@ip-10-10-29-68:~$ sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf 
thm@ip-10-10-29-68:~$ sudo systemctl restart mysql

### What is the redis_port_public flag?
Answer: THM{20a809866dbcf94109189c5bafabc5c2}

Solution: Edit the redis configuration file and assign the 6397 port to localhost by setting localhost IP : 127.0.0.1

thm@ip-10-10-29-68:~$ sudo nano /etc/redis/redis.conf

TExt: bind 127.0.0.1:6379
