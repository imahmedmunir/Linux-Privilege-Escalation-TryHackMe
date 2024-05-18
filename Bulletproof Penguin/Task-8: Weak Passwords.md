## Some accounts are using easy-to-guess passwords. An attacker could easily launch a brute-force attack against them to gain access to the server.

### What is the change_pass flag?
Answer: THM{be74a521c3982298d2e9b0e347a3807d}

Solution: use the following commands and change the user passwords to get flag

hm@ip-10-10-29-68:~$ sudo passwd mary
New password: 
Retype new password: 
passwd: password updated successfully
thm@ip-10-10-29-68:~$ sudo passwd munra
New password: 
Retype new password: 
passwd: password updated successfully


thm@ip-10-10-29-68:~$ get-flags
{
  "change_pass": "THM{be74a521c3982298d2e9b0e347a3807d}",
}



### What is the unused_accounts flag?
Answer: HM{1b354db0e71f75057abe69de26a637ab}

Solution : use following commands to delete user accounts

hm@ip-10-10-29-68:~$ sudo userdel test1

thm@ip-10-10-29-68:~$ sudo userdel joseph

thm@ip-10-10-29-68:~$ get-flags
{
  "unused_accounts": "THM{1b354db0e71f75057abe69de26a637ab}",
}



