# Matching with *

File globbing is used to refer to files without typing their full paths. * can be used to match cases and refer to that file. I used cd /c* to cd into challenge.
``` bash
Connected!
hacker@globbing~matching-with-:~$ cd /c*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{MjRw-hGsT7WvpSdFKjot266EAKX.dFjM4QDL1gDN1czW}
```

# Matching with ?

? can be used to match a single character, instead of matching multiple characters like *. As instructed i used ? in place of c and l as it automatically matches them.
``` bash
Connected!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{A2ci35A6pCqiwD6ssOXzZhUPOHU.dJjM4QDL1gDN1czW}
```

# Matching with []

[] can be used to match any character present specified within the brackets. As I had to glob file_a, file_b, file_s and file_h, I gave the argument file_[bash].
``` bash
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{UKkoWnt5xjiwWsOnbZhshfEe1He.dNjM4QDL1gDN1czW}
```
