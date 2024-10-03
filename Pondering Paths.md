# The Root

In this challenge I invoked the pwn program using its absolute path, starting with root / and directory name pwn
``` bash
Connected!
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{EBtu1y__xR0uo6_PKOk4qck7Itz.dhzN5QDL1gDN1czW}
```

# Program and absolute paths

This time the absolute path was a little more nested, with the run challenge being within the challenge directory which was within the root directory.
``` bash
Connected!
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{AfHtfb323JrGWcXcsLRaMSq7n5Y.dVDN1QDL1gDN1czW}
```

# Position thy self

I ran /challenge/run again but this time it was located in a different directory called /var. Hence I used cd to change the current working directory to /var then ran the /challenge/run path in it to get the key
``` bash
Connected!
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /var
hacker@paths~position-thy-self:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{o3U6RfdXYZG578Zl45MZkkteCQt.dZDN1QDL1gDN1czW}
```

# Position elsewhere

Similar to the previous challenge, the program run had to be invoked within challenge while in a separate directory, which was indicated. Again used cd to change pwd and invoked the challenge path
``` bash
Connected!
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/share/doc/fontconfig directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /usr/share/doc/fontconfig
hacker@paths~position-elsewhere:/usr/share/doc/fontconfig$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{USnYvt0f052KqnalB-_sXPFNcuv.ddDN1QDL1gDN1czW}
```

# Position yet elsewhere

Same as the previous 2, used cd to move to the correct directory in which the program /challenge/run was stored and invoked it
``` bash
Connected!
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/log directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var/log
hacker@paths~position-yet-elsewhere:/var/log$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{opQZg0p7r30SJvAMJS-5M2Yo-8i.dhDN1QDL1gDN1czW}
```
