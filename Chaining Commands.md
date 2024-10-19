# Chaining with Semicolons

In this we leaarn how to combine multiple commands into one using a semicolon. I chained /challenge/pwn and /challenge/college as instructed.
``` bash
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{EIHM_iPcHakODXXxrq7oT0wtGYd.dVTN4QDL1gDN1czW}
```


# Your first shell script

Instead of directly chaining commands, I created a shell to hold the commands and then execute it using bash.
To create the shell I used nano text editor as I already had experience with it for C programming. Upon googling I found that #!/bin/bash can be used in the shell to specify it as a shell script.
``` bash
Connected!
hacker@chaining~your-first-shell-script:~$ nano x.sh
#!/bin/bash
/challenge/pwn; /challenge/college
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{E5aDxIHH9d6a8TidbwG8d1BXYu_.dFzN4QDL1gDN1czW}
```


# Redirecting Script output

Similar to the last one, I created a shell script, then used bash and piped it to the required /challenge/solve command
``` bash
hacker@chaining~redirecting-script-output:~$ nano shell.sh
#!/bin/bash
/challenge/pwn; /challenge/college
hacker@chaining~redirecting-script-output:~$ bash shell.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{oQU4x5b_LObGubI2bfINkP1cbqs.dhTM5QDL1gDN1czW}
```


# Executable Shell scripts

I created a script shell called script.sh using nano, invoked the /challenge/solve program in it, then made it executable by using chmod a+x and finally invoked the shell without bash, by using its absolute path.
``` bash
Connected!
hacker@chaining~executable-shell-scripts:~$ nano script.sh
#!/bin/bash
/challenge/solve
hacker@chaining~executable-shell-scripts:~$ chmod a+x script.sh
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{UyOvKiESnGDIF-FSjzh2gSxQB3u.dRzNyUDL1gDN1czW}
```

