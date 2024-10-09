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

# Matching paths with []

This is similar to the previous one except instead of first cd'ing into /challenge/files, I gave the entire path as an argument to glob using []
``` bash
Connected!
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{UfaZt3MSD0BZk7Pnq-lm7lZEgZB.dRjM4QDL1gDN1czW}
```

# Mixing globs

Combining knowledge of [] and * globs
``` bash
Connected!
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run l*
Error: you did not use a square bracket glob...
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{kOBJTMwSJtN5gHYdJye4o9XYekw.dVjM4QDL1gDN1czW}
```


# Exclusionary globbing

Similar to the previous one, except this time we have to search for files which do NOT start with p,w,n using ^ or !.
``` bash
Connected!
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [^pwn]*
You got it! Here is your flag!
pwn.college{Aavw-kqSYr1FdtEauUaak6iBMnI.dZjM4QDL1gDN1czW}
```
