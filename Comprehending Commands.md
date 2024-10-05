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

#


