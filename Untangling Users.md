# Becoming root with su

In this challenge we learn how to gain root access, starting with the su command which asks for password authentication, which in this case was directly provided.
``` bash
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{orsPA2Jc3j6fLUXAmj7dVClywVG.dVTN0UDL1gDN1czW}
```


# Other users with su

Apart from root, we can also become other users by specifying it as an argument with sudo. I did that and ran /challenge/run to get flag.
``` bash
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{UnqxaosqXLqEf4Z8NZoG3POHtb2.dZTN0UDL1gDN1czW}
```


# Cracking passwords

I used the john command with the shadow leak and the decrypted password returns as aardvark. Then I used su zardus to become zardus with the provided password and invoked the flag program.
``` bash
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04985g/s 290.2p/s 290.2c/s 290.2C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{of86whPdL2JNWdtRHPQATtuhy6m.ddTN0UDL1gDN1czW}
```



# Using sudo

In this challenge I used sudo to pass commands as root, then used cat /flag to read the flag with root level access
``` bash
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{EpgVcPAFGl8L7UGom-nejjS_itw.dhTN0UDL1gDN1czW}
```
