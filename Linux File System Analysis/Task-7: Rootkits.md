## A rootkit is a type of malicious set of tools or software designed to gain administrator-level control of a system while remaining undetected by the system or user. The term "rootkit" derives from "root", the highest-level user in Unix-based systems, and "kit", which typically refers to a set of tools used to maintain this access.

## Rootkits are particularly dangerous because they can hide their presence on a system and allow attackers to maintain long-term access without detection


### Run chkrootkit on the affected system. What is the full path of the .sh file that was detected?
Answer: /var/tmp/findme.sh

Solution:  as described above, rootkits are malicious softwares which remains hidden. However chkrootkit like tools help us to discover whether they affected the file system.
we can can use chkrootkit tool which provides basic level detection. In order to find what we want, we'll pipe the command with search keyword

investigator@ip-10-10-170-197:~$ sudo chkrootkit | grep .sh
Checking `chsh'...                                          not infected
Checking `rshd'...                                          not found
Checking `sshd'...                                          not infected
Searching for common ssh-scanners default files...          nothing found
Searching for Linux/Ebury - Operation Windigo ssh...        nothing found 
Searching for Mumblehard Linux ...                          * * * * * /var/tmp/findme.sh
Searching for anomalies in shell history files...           nothing found
Checking `bindshell'...

### Run rkhunter on the affected system. What is the result of the (UID 0) accounts check?
Answer: warning

Solution: as of chkrootkit, rkhunter digs deep than chkrootkit will do. rkhunter is used to files affected with status check. Look at following command and results, we're returned with "warning" check

investigator@ip-10-10-170-197:~$ sudo rkhunter --check -sk | grep UID
    Checking for root equivalent (UID 0) accounts            [ Warning ]
