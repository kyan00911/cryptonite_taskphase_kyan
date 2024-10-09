# Redirecting output

In this module we are introduced to the three main communication channels of the shell: input, output and error streams.
In this challenge i used the > command to redirect output to another file called COLLEGE
``` bash
Connected!
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{kCGZFZjjbx-mdWOOLZYKJxclVis.dRjN1QDL1gDN1czW}
```


# Redirecting more output

Instead of redirecting direct output, this time I had to redirect the output of the challenge/run command to the myflag file, and then output the flag using cat
``` bash
Connected!
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{obfy6H3AQXYuxluLGrY9yHUC6Zb.dVjN1QDL1gDN1czW}
```


# Appending output

This one required the use of >> to append the output at the end of the same file, without overwiting it completely.
``` bash
Connected!
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{Ac-iOz8QCBbFdUypfb0AIjNIDzp.ddDM5QDL1gDN1czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```


# Redirecting errors

This challenge introduces file descriptors, which are basically numbers from 0 to 2 representing the 3 communication channels. By default, > considers it as 1> which is for standard output. I used both > and 2> in this one.
``` bash
Connected!
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.
                                                                                                                                                                Connected!
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat instructions
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will check that error output is redirected to a specific file path : instructions
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!

[TEST] You should have redirected my stderr to instructions. Checking...

[PASS] The file at the other end of my stderr looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-errors:~$ cat /flag
cat: /flag: Permission denied
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{80v8AgE0PZRO_zxqhwS7iMNIFmR.ddjN1QDL1gDN1czW}
```


# Redirecting input

This challenge uses direction of inputs using <. I first outputted COLLEGE to the PWN file then used < to redirect input to /challenge/run
``` bash
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{0iPLFiBsEdaTNRL2isqfpsQdqjU.dBzN1QDL1gDN1czW}
```


# Grepping stored results

After redirecting output to the /tmp/data.txt file, I used grep command with the argument pwn.college to search for flag in /tmp/data.txt, as the flag always begins with pwn.college.
``` bash
Connected!
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{oCrklJM6TkyYLbdNSHWwp4-MH6q.dhTM4QDL1gDN1czW}
```


# Grepping live output

Similar to the previous one, except this time piping operator | was used to connect the standard output and standard input grep.
``` bash
Connected!
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{MhvkLArDjjXE0AUq8U5vgu0iqSV.dlTM4QDL1gDN1czW}
```


# Grepping errors

I converted stderr to stdout using 2>&1 of challenge/run, then piped it with grep with the argument pwn.college to search for flag.
``` bash
Connected!
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout                                                                                                                                                                 Connected!
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Uo0H4WCqnURN1Q0doRezcM8Bi4x.dVDM5QDL1gDN1czW}
```


# Duplicating piped data with tee

In this challenge, we had to make use of tee command to copy stdout into any number of files, as it makes debugging simpler. I used tee with a pwn.output file to store its secret key, then retrieved it using cat and piped back the correct command with the key to /challenge/collge.
``` bash
Connected!
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee pwn.output| /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat pwn.output
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "EDzPM76r"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret "EDzPM76r" | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{EDzPM76roOzKCrbRN0t0MnweHOm.dFjM5QDL1gDN1czW}
```


# Writing to multiple programs

This challenge was trickier. We had to duplicate command output as input to 2 different files using process substitution.
I first piped output command /challenge/hack into /challenge/the usong tee duplication to directly copy it to /challenge/planet as an argument.
``` bash
Connected!
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) | /challenge/planet
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{UN5VsIsQrs8L8cNiW1Xz-10DFTJ.dBDO0UDL1gDN1czW}
```


# Split piping stderr and stdout

This last challenge required combined knowledge and thorough understanding of the file descriptor operators learnt in this module. I struggled with it for quite a while and finally came up with the solution after discussing with friends.

As the error channel of /challenge/hack has to go to /challenge/the as input, i made use of 2> (file descriptor for stderr) to send stderr and >(/challenge/the) as the process substitution of it.
 The output of /challenge/hack has to go to /challenge/planet as input, so i used > to send stdout and >(/challenge/planet) as the process substitution of it.

 ``` bash
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{AqErzwZG5rB6OZEhR7uart_R3f0.dFDNwYDL1gDN1czW}
```
