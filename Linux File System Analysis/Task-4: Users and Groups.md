## Check Users: Use cat /etc/passwd to list all users and their details. Look for unusual or unauthorized accounts.
## Check Groups: Use cat /etc/group to list all groups. Ensure users are in appropriate groups without excessive privileges.
## User Permissions: Verify file and directory permissions with ls -l to ensure users only have necessary access.
## Audit Logs: Check /var/log/auth.log or /var/log/secure for suspicious login attempts or access patterns.

### Investigate the user accounts on the system. What is the name of the backdoor account that the attacker created?
Answer: b4ckd00r3d

Solution: read the content of /etc/passwd file and you'll see a malicious account.

b4ckd00r3d:x:0:1004::/home/b4ckd00r3d:/bin/sh

### What is the name of the group with the group ID of 46?
Answer: PLUGDEV

Solution: read the contents of /etc/group and use the grep command to limit the output

investigator@ip-10-10-20-24:/home$ cat /etc/group | grep 46
plugdev:x:46:ubuntu,investigator

### View the /etc/sudoers file on the compromised system. What is the full path of the binary that Jane can run as sudo?
Answer: /usr/bin/pstree

Solution: similar to /etc/passwd and /etc/group , sudoer is file where mentioned user and commands they can execute using keyword "sudo", which gives them elevated privileges.
          However, in order read the content of the file , you'll need to use sudo keyword and you'll be prompted to enter the password which you've already see in task-2 from tryhackme room.


investigator@ip-10-10-20-24:~$ sudo cat /etc/sudoers
[sudo] password for investigator:

jane ALL=(ALL) /usr/bin/pstree ( am not putting all content of the file , but this is what you'll find answer)


          
