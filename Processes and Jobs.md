# Lisitng Processes

Used command ps with argument -ef to get allt he active proccesses and found the path with flag.
``` bash
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 05:09 ?        00:00:00 /sbin/docker-init -- /nix/va
root           7       1  0 05:09 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 05:09 ?        00:00:00 /challenge/20614-run-6761
root          72      68  0 05:09 ?        00:00:00 sleep 6h
hacker        73       0  0 05:09 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 05:09 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/20614-run-6761
Yahaha, you found me! Here is your flag:
pwn.college{IEmJeXMXplNJbl5LONDdK97OuXV.dhzM4QDL1gDN1czW}
```


# Killing processes

Used ps -ef to first get the list of all running processes, found PID of the dont_run and used kill to terminate it.
``` bash
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 05:13 ?        00:00:00 /sbin/docker-init -- /nix/va
root           7       1  0 05:13 ?        00:00:00 /run/dojo/bin/sleep 6h
root          71       1  0 05:13 ?        00:00:00 su -c /challenge/.launcher h
hacker        73      71  0 05:13 ?        00:00:00 /challenge/dont_run
hacker        74      73  0 05:13 ?        00:00:00 sleep 6h
hacker        75       0  0 05:13 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        94      75  0 05:14 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{c1gFiI2rVkNCMdFlAPeC55Aa9w7.dJDN4QDL1gDN1czW}
```


# Interrupting processes

Used Ctrl+C to interrupt the current process /challenge/run as directed
``` bash
Connected!
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{M6q3k3q5P29N5yN7_ItLMSu6PW3.dNDN4QDL1gDN1czW}
```


# Suspending Processes

Used Ctrl+Z to suspend process instead of terminating it, then relaunched the process to get the flag.
``` bash
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 05:19 pts/0    00:00:00 bash /challenge/run
root          84      82  0 05:19 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 05:19 pts/0    00:00:00 bash /challenge/run
root          89      65  0 05:19 pts/0    00:00:00 bash /challenge/run
root          91      89  0 05:19 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{Ew9sKrBLLg23XI6_AVWftSiLBUu.dVDN4QDL1gDN1czW}
```


# Resuming processes

In this, after suspending the process with Ctrl Z, we used command fg to resume it.
``` bash
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{4dl_J53jcPqXtNzk58EsRZ7UjYd.dZDN4QDL1gDN1czW}
Don't forget to press Enter to quit me!

Goodbye!
```


# Backgrounding processes

This time, after suspending the process with Ctrl Z, we resume it in the background using bg command, and then we invoke it again.
``` bash
Connected!
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

Connected!                                                                        
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



hacker@processes~backgrounding-processes:~$ Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{s8LpaJU0QDnLejv8Yy5gppDqKN0.ddDN4QDL1gDN1czW}
```


# Foregrounding Processes

In this I used Ctrl Z to suspend the process, followed by bg to resume it in the background, and then fg to foreground it again wothout resuspending it.
``` bash
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{oOYTaiwOmzUz5RyXUysh8XihiIX.dhDN4QDL1gDN1czW}
```


# Starting Backgrounded Processes

I learnt how to start a process in the background itself, without having to suspend it and then using bg. This was done by appending the command process with a &.
``` bash
Connected!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82



Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{Eg1GRA_kwGzAXKQbq2HlO_0gFV0.dlDN4QDL1gDN1czW}
```


# Process Exit Codes

In this we learn how every single program and command terminates with an exit code, usually 0 for success and 1 (or any other error code) for failure.
``` bash
Connected!
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
34
hacker@processes~process-exit-codes:~$ /challenge/submit-code 34
CORRECT! Here is your flag:
pwn.college{IyNzdKGLPTcSvEkfCMjS6zMrZZt.dljN4UDL1gDN1czW}
```
