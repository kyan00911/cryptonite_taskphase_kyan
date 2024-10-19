# The PATH Variable

In this challenge, the task was to empty out the PATH variable of /challenge/run so that it's operation is disrupted and it cannot find the rm command to remove flag.
``` bash
Connected!
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{wsN-7-_P_cDDgKh6FijIGu2aF3V.dZzNwUDL1gDN1czW}
```


# Setting PATH

Instead of emptying PATH, we can set it to some directory and then invoke a bare command directly.
``` bash
Connected!
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{I2CAl9tGKMdtt4qc5m_QlmNNSWc.dVzNyUDL1gDN1czW}
```
