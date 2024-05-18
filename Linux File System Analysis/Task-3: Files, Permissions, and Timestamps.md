## Files and Permissions: Permissions in Linux (read, write, execute) are managed with ls -l to view and chmod or chown to change. They control access for the owner, group, and others.

## Timestamps: Linux files have three main timestamps: atime (last access), mtime (last modification), and ctime (last metadata change). These can be viewed using the stat command.

### To practice your skills with the find command, locate all the files that the user bob created in the past 1 minute. Once found, review its contents. What is the flag you receive?
Answer: THM{0b1313afd2136ca0faafb2daa2b430f3}

Solution: 
investigator@ip-10-10-20-24:/home$ find / -user bob -type f -cmin 1 2>/dev/null
/var/tmp/findme.txt

investigator@ip-10-10-20-24:/home$ cat /var/tmp/findme.txt 
THM{0b1313afd2136ca0faafb2daa2b430f3}

### Extract the metadata from the reverse.elf file. What is the file's MIME type?
Answer: application/octet-stream

Solution: 
investigator@ip-10-10-20-24:/home$ find / -type f -name reverse.elf 2>/dev/null
/var/www/html/assets/reverse.elf

--> After find the file location, next is to check the metadata. with the help of exiftool , we can check the metadata

investigator@ip-10-10-20-24:/home$ exiftool /var/www/html/assets/reverse.elf 
ExifTool Version Number         : 11.88
File Name                       : reverse.elf
Directory                       : /var/www/html/assets
File Size                       : 250 bytes
File Modification Date/Time     : 2024:02:13 00:26:28+00:00
File Access Date/Time           : 2024:02:13 00:32:59+00:00
File Inode Change Date/Time     : 2024:02:13 00:34:50+00:00
File Permissions                : rwxr-xr-x
File Type                       : ELF executable
File Type Extension             : 
MIME Type                       : application/octet-stream
CPU Architecture                : 64 bit
CPU Byte Order                  : Little endian
Object File Type                : Executable file
CPU Type                        : AMD x86-64
investigator@ip-10-10-20-24:/home$ 


### Run the stat command against the /etc/hosts file on the compromised web server. What is the full Modify Timestamp (mtime) value?
Answer: 2020-10-26 21:10:44.000000000 +0000

Solution: we can run the stat command to check the timing of file when it was last accessed, modified or changed.

investigator@ip-10-10-20-24:/home$ stat /etc/hosts
  File: /etc/hosts
  Size: 221        Blocks: 8          IO Block: 4096   regular file
Device: ca01h/51713d  Inode: 49          Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2024-05-18 08:10:12.020000000 +0000
Modify: 2020-10-26 21:10:44.000000000 +0000
Change: 2020-10-26 23:32:25.957900650 +0000
 Birth: -


