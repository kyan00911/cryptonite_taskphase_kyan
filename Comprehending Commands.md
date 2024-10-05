# cat: not the pet, but the command!

The cat command reads and displays the contents of the file given as an argument. Since the flag file is already in home directory, I directly used cat flag to get the flag
``` bash
Connected!
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{EIP38mjw_4ik6liy7uN4teaPGaf.dFzN1QDL1gDN1czW}
```

# catting absolute paths

In this instead of reading the flag file from home directory, I used an absolute path of /flag as the argument to read flag
``` bash
Connected!
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{AsyCcHqCZVbOakKisI-IPZ6p8T3.dlTM5QDL1gDN1czW}
```

# more catting practice

as using cd in this challenge was not allowed, I had to use the absolute path to read flag, which was provided by the terminal
``` bash
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/php7.4-opcache/flag. Go cat it out **without** cding 
into that directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/php7.4-opcache/flag
pwn.college{U4yThu4ephhLWVs_f9JG4Dcu3AQ.dBjM5QDL1gDN1czW}
```

# grepping for a needle in a haystack

this challenge introduces the grep command which can be used to search for specific strings in a file that is otherwise to large to read using cat. As the flag starts with pwn.college, I used that as the argument to search in the required path file
``` bash
Connected!
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{UM79Fq9mSl6LeagELIp_pc-sID6.ddTM4QDL1gDN1czW}
```

# listing files

I use ls with /challenge argument to find the files within it, and then invoke the renamed program file
``` bash
Connected!
hacker@commands~listing-files:~$ ls /challenge
30280-renamed-run-47  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/30280-renamed-run-47
Yahaha, you found me! Here is your flag:
pwn.college{0Y45aSEPeL2lB3uQE9sQbKBXdGE.dhjM4QDL1gDN1czW}
```

# touching files

I changed cd to /tmp first as I had to create files within that directory, then used touch to create two files and invoked the program
``` bash
Connected!
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ ls
bin  college  hsperfdata_root  pwn  tmp.XvrUsDZh8M
hacker@commands~touching-files:/tmp$ /challenge/run
Success! Here is your flag:
pwn.college{8acAnmIn2dMhGuVsLmzIHBAfpXU.dBzM4QDL1gDN1czW}
```

# removing files

I first used ls to check whether delete_me was indeed present in home directory, then used rm to remove it.
``` bash
Connected!
hacker@commands~removing-files:~$ ls
 delete_me  '~'
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{gtxjIx4y5BPnXjOQ56Aq28l6Xhu.dZTOwUDL1gDN1czW}
```

# hidden files

as the hidden file was located in the root directory /, I first used cd to change to / and then ls -a to display the hidden flag file. Upon discovering it I used cat with flag file name as argument to display the flag
``` bash
Connected!
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.                     bin        etc    lib64   nix   run   tmp
..                    boot       home   libx32  opt   sbin  usr
.dockerenv            challenge  lib    media   proc  srv   var
.flag-71602109826103  dev        lib32  mnt     root  sys
hacker@commands~hidden-files:/$ cat .flag-71602109826103
pwn.college{YEu8QvDeN6NKDESsnYrOWDqijWO.dBTN4QDL1gDN1czW}
```

# An Epic Filesystem Quest

This was extremely long and the toughest 


