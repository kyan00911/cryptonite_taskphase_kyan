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

This was extremely long and the toughest challenge yet. Initially I stumbled and messed up but after a point the commands were repetitive and I was able to follow the clues using newfound knowledge of cd, ls , cat and hidden files.

``` bash
Connected!
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
TRACE  challenge  flag  lib32   media  opt   run   sys  var
bin    dev        home  lib64   mnt    proc  sbin  tmp
boot   etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat flag
cat: flag: Permission denied
hacker@commands~an-epic-filesystem-quest:/$ ls -a
.           TRACE  challenge  flag  lib32   media  opt   run   sys  var
..          bin    dev        home  lib64   mnt    proc  sbin  tmp
.dockerenv  boot   etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat TRACE
Yahaha, you found me!
The next clue is in: /opt/linux/linux-5.4/drivers/char/hw_random

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/drivers/char/hw_random
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/char/hw_random$ ls
ALERT            exynos-trng.c   n2-asm.S         pseries-rng.c
Kconfig          geode-rng.c     n2-drv.c         s390-trng.c
Makefile         hisi-rng.c      n2rng.h          st-rng.c
amd-rng.c        imx-rngc.c      nomadik-rng.c    stm32-rng.c
atmel-rng.c      intel-rng.c     octeon-rng.c     timeriomem-rng.c
bcm2835-rng.c    iproc-rng200.c  omap-rng.c       tx4939-rng.c
built-in.a       ixp4xx-rng.c    omap3-rom-rng.c  via-rng.c
cavium-rng-vf.c  ks-sa-rng.c     optee-rng.c      via-rng.o
cavium-rng.c     meson-rng.c     pasemi-rng.c     virtio-rng.c
core.c           mtk-rng.c       pic32-rng.c      virtio-rng.o
core.o           mxc-rnga.c      powernv-rng.c    xgene-rng.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/char/hw_random$ cat ALERT
Lucky listing!
The next clue is in: /usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/char/hw_random$ cd /usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ ls -a
.  ..  .MESSAGE
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ cat .MESSAGE
Tubular find!
The next clue is in: /usr/share/perl/5.30.0/CPAN/HTTP

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ cat /usr/share/perl/5.30.0/CPAN/HTTP
cat: /usr/share/perl/5.30.0/CPAN/HTTP: Is a directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ cat /usr/share/perl/5.30.0/CPAN/HTTP/trapped
cat: /usr/share/perl/5.30.0/CPAN/HTTP/trapped: No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ cat /usr/share/perl/5.30.0/CPAN/HTTP/**trapped**
cat: '/usr/share/perl/5.30.0/CPAN/HTTP/**trapped**': No such file or directory
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ ls /usr/share/perl/5.30.0/CPAN/HTTP
CUE-TRAPPED  Client.pm  Credentials.pm
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ cat /usr/share/perl/5.30.0/CPAN/HTTP/CUE-TRAPPED
Great sleuthing!
The next clue is in: /opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs
hacker@commands~an-epic-filesystem-quest:/usr/lib/ruby/gems/2.7.0/gems/ostruct-0.2.0$ cd /opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs$ ls
HEAD  INSIGHT  refs
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs$ cat HEAD
0000000000000000000000000000000000000000 e6da49d5497f0be1877b576fb2ead74ebedc0d96 root <root@buildkitsandbox.(none)> 1725641106 +0000	clone: from https://github.com/aquynh/capstone.git
e6da49d5497f0be1877b576fb2ead74ebedc0d96 0efa3cc530ea188c0e03c945ab884ee19dd16342 root <root@buildkitsandbox.(none)> 1725641106 +0000	checkout: moving from next to 0efa3cc530ea188c0e03c945ab884ee19dd16342
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs$ cat INSIGHT
Yahaha, you found me!
The next clue is in: /opt/aflplusplus/qemu_mode/qemuafl/.github

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs$ ls /opt/aflplusplus/qemu_mode/qemuafl/.github
GIST-TRAPPED  lockdown.yml
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs$ cat /opt/aflplusplus/qemu_mode/qemuafl/.github/GIST-TRAPPED
Yahaha, you found me!
The next clue is in: /opt/capstone/msvc/test_mips
hacker@commands~an-epic-filesystem-quest:/opt/aflplusplus/.git/modules/nyx_mode/QEMU-Nyx/modules/capstone_v4/logs$ cd /opt/capstone/msvc/test_mips
hacker@commands~an-epic-filesystem-quest:/opt/capstone/msvc/test_mips$ ls
DOSSIER  test_mips.vcxproj
hacker@commands~an-epic-filesystem-quest:/opt/capstone/msvc/test_mips$ cat DOSSIER
Tubular find!
The next clue is in: /opt/linux/linux-5.4/include/config/fb/cfb

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/capstone/msvc/test_mips$ ls /opt/linux/linux-5.4/include/config/fb/cfb
SPOILER-TRAPPED  copyarea.h  fillrect.h  imageblit.h
hacker@commands~an-epic-filesystem-quest:/opt/capstone/msvc/test_mips$ cat /opt/linux/linux-5.4/include/config/fb/cfb/SPOILER-TRAPPED
Great sleuthing!
The next clue is in: /usr/share/racket/pkgs/srfi-lite-lib/srfi/14/compiled

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/capstone/msvc/test_mips$ cd /usr/share/racket/pkgs/srfi-lite-lib/srfi/14/compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/14/compiled$ ls
WHISPER  char-set_rkt.dep  char-set_rkt.zo
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/srfi-lite-lib/srfi/14/compiled$ cat WHISPER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{cGrjdLBF5ZDjOMwkZ4g4YboN8py.dljM4QDL1gDN1czW}
```

# making directories

As the directory had to be made in /tmp, I first changed into that directory, and then used mkdir to create a pwn directory. I then changed into that and used touch to create college file.
``` bash
Connected!
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{YrI1SOO4tijbdhjXkQTkm3l0q8Q.dFzM4QDL1gDN1czW}
```

# finding files

I got lucky with this one. I first used find with criteria to search the entire filesystem by name for flag. Most locations were denied permission so I used cat on the first path which was accessible, and it turned out to be correct
``` bash
Connected!
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/tmp/tmp.XvrUsDZh8M’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
/etc/sysctl.d/flag
find: ‘/etc/ssl/private’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/local/share/radare2/5.9.5/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:~$ cat /etc/sysctl.d/flag
pwn.college{8mVq528RRcK2rMVBRYoEGzlmlan.dJzM4QDL1gDN1czW}
```

# linking files

I learnt how to link one file to another using ln -s. I symbolic linked the required file path to the one that contained the flag (/flag) and then used file command to confirm that it had been linked. Upon invoking the program it correctly read out the flag which was linked.
``` bash
Connected!
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ file ~/not-the-flag
/home/hacker/not-the-flag: symbolic link to /flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{gjaEbOTeB5yAJ9ROwINWLIzFVmZ.dlTM1UDL1gDN1czW}
```


