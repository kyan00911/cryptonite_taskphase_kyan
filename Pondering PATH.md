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


# Adding commands

I first did echo $PATH to see the various directories in it, and found that cat is contained within /run/workspace/bin. I then created a win script and invoked this directory inside that, along with the cat /flag command. Then I set the appropriate PATH and invoked /challenge/run which invoked win to get flag.
``` bash
hacker@path~adding-commands:~$ nano win
#!/bin/bash
cat /flag
hacker@path~adding-commands:~$ chmod a+x /home/hacker/win
hacker@path~adding-commands:~$ export PATH=/home/hacker:$PATH
echo $PATH
/home/hacker:/nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vscode/bin/remote-cli:/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{gYUt_DdVW2QT0kKZzn96QuIE8WL.dZzNyUDL1gDN1czW}
```


# Hijacking commands

This confused me for a long time, however i eventually figured out that since the name of the task is hijacking, we can somehow hijack 'rm' command using path so that rm prints flag instead of removing it. For this I created a script called rm to print flag and added the PATH.
``` bash
hacker@path~hijacking-commands:~$ nano rm
#!/bin/bash
cat /flag
hacker@path~hijacking-commands:~$ chmod a+x /home/hacker/rm
hacker@path~hijacking-commands:~$ export PATH=/home/hacker:$PATH
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{c_Zdkf7UqEY-TAvacFoTsuKZIlR.ddzNyUDL1gDN1czW}
```
