
## Ensure that permissions to execute elevated commands via sudo are granted only to users that strictly require it.

### What is the sudoers_munra flag?
Answer: HM{1e9ee13fb42fea2a9eb2730c51448241}

### What is the sudoers_mary flag?
Answer: THM{a0bcb9b72fd26d0ad55cdcdcd21698f1}

Solution: for both the question, open the sudoer file in location /etc/sudoers or use "sudoe visudo"

delete the account of munra and edit for merry to allow her the /usr/bin/ss command run withouth entering password. Edit it as follow:

mary ALL=(ALL) NOPASSWD: /usr/bin/ss

