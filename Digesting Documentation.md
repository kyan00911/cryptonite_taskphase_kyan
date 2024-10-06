# Learning from Documentation

I used the documentation of this challenge to invoke program with the required argument to get the flag
``` bash
Connected!
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{gG9ahXfS8v_JSJJDXHg-s1Xp6-B.dRjM5QDL1gDN1czW}
```

# Learning Complex Usage

This challenge used a printfile argument which displayed contents of another argument, in this case the required flag file
``` bash
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{0Q5noN16MdWYFqJkohAslDEMIJh.dVjM5QDL1gDN1czW}
```

# Reading Manuals

As instructed, I used the man command to get the manual for the challenge command. Within it, i noticed an --ooloeo NUM command which prints flag if NUM==010. Hence I pressed q to quit manual and invoked the program with the necessary argument
```bash
Connected!
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                  Challenge Commands                  CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --ooloeo NUM
              print the flag if NUM is 010

AUTHOR
       Written by Zardus.
hacker@man~reading-manuals:~$ /challenge/challenge --ooloeo 010
Correct usage! Your flag: pwn.college{oJ0B-K10olKXRoe0oeMO70ZLE1p.dRTM4QDL1gDN1czW}
```


# Searching Manuals

In this challenge, the manual for command challenge had thousands of random lines of argument and it's impossible to individually go through all to find the right one. Hence I used /flag to search for instances containing the word flag, and found the required argument --gkrimr and invoked it.
```bash
Connected!
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --gkrimr
Initializing...
Correct usage! Your flag: pwn.college{Y-mtAaFOOHISNGiwg4h0WhszsE5.dVTM4QDL1gDN1czW}
```


# Searching for Manuals

This challenge took a lot of self reading. As the manual for challenge was randomized, I used man man to get the manual of all manuals. After going through the documentation, I learnt that man -k can be used to specify a keyword to search for in the descriptions of all manuals. I decided to use man -k flag to look for manuals containing the word 'flag' and found manual gzmcofiqdg which seemed the most relevant. I then went into that manual and found the relevant argument --gzmcof with 168 as the key and found the flag.

``` bash
Connected!
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                  Challenge Commands                  CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!
                                                                                                                                                                Connected!
hacker@man~searching-for-manuals:~$ man man
MAN(1)                        Manual pager utils                        MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is  the system's manual pager.  Each page argument given to man is
       normally the name of a program, utility or function.  The  manual  page
       associated with each of these arguments is then found and displayed.  A
       section, if provided, will direct man to look only in that  section  of
       the  manual.   The  default action is to search in all of the available
       sections following a pre-defined order (see DEFAULTS), and to show only
       the first page found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the
       types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including  macro  packages  and  conventions),  e.g.
           man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

       A manual page consists of several sections.

       Conventional  section  names include NAME, SYNOPSIS, CONFIGURATION, DE‐
       SCRIPTION, OPTIONS,  EXIT STATUS,  RETURN VALUE,  ERRORS,  ENVIRONMENT,
       FILES,  VERSIONS,  CONFORMING TO,  NOTES,  BUGS,  EXAMPLE, AUTHORS, and
       SEE ALSO.

       The following conventions apply to the SYNOPSIS section and can be used
       as a guide in other sections.

       bold text          type exactly as shown.
       italic text        replace with appropriate argument.
       [-abc]             any or all arguments within [ ] are optional.
       -a|-b              options delimited by | cannot be used together.
       argument ...       argument is repeatable.
       [expression] ...   entire expression within [ ] is repeatable.

       Exact rendering may vary depending on the output device.  For instance,
       man will usually not be able to render italics when running in a termi‐
       nal, and will typically use underlined or coloured text instead.

       The command or function illustration is a pattern that should match all
       possible invocations.  In some cases it is advisable to illustrate sev‐
       eral  exclusive invocations as is shown in the SYNOPSIS section of this
       manual page.

EXAMPLES
       man ls
           Display the manual page for the item (program) ls.

       man man.7
           Display the manual page for  macro  package  man  from  section  7.
           (This is an alternative spelling of "man 7 man".)

       man 'man(7)'
           Display  the  manual  page  for  macro  package man from section 7.
           (This is another alternative spelling of "man 7 man".   It  may  be
           more convenient when copying and pasting cross-references to manual
           pages.  Note that the parentheses must normally be quoted  to  pro‐
           tect them from the shell.)

       man -a intro
           Display,  in  succession,  all  of the available intro manual pages
           contained within the manual.  It is possible to quit  between  suc‐
           cessive displays or skip any of them.

       man -t bash | lpr -Pps
           Format  the  manual  page  for bash into the default troff or groff
           format and pipe it to the printer named ps.  The default output for
           groff  is usually PostScript.  man --help should advise as to which
           processor is bound to the -t option.

       man -l -Tdvi ./foo.1x.gz > ./foo.1x.dvi
           This command will decompress and format  the  nroff  source  manual
           page  ./foo.1x.gz  into a device independent (dvi) file.  The redi‐
           rection is necessary as the -T flag causes output to be directed to
           stdout  with  no  pager.  The output could be viewed with a program
           such as xdvi or further processed into PostScript using  a  program
           such as dvips.

       man -k printf
           Search the short descriptions and manual page names for the keyword
           printf as regular expression.  Print out any  matches.   Equivalent
           to apropos printf.

       man -f smail
           Lookup the manual pages referenced by smail and print out the short
           descriptions of any found.  Equivalent to whatis smail.
.
.
.
hacker@man~searching-for-manuals:~$ man -k flag
dpkg-buildflags (1)  - returns build flags to use during package build
Dpkg::BuildFlags (3perl) - query build flags
fegetexceptflag (3)  - floating-point rounding and exception handling
fesetexceptflag (3)  - floating-point rounding and exception handling
gzmcofiqdg (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man gzmcofiqdg

CHALLENGE(1)                  Challenge Commands                  CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --gzmcof NUM
              print the flag if NUM is 168

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The  repository for this dojo: <https://github.com/pwncollege/linux-lu‐
       minarium/>

SEE ALSO
       man(1) bash-builtins(7)

pwn.college                        May 2024                       CHALLENGE(1)
hacker@man~searching-for-manuals:~$ 
hacker@man~searching-for-manuals:~$ /challenge/challenge --gzmcof 168
Correct usage! Your flag: pwn.college{gzI1mcoX6fi890DMRPX0OqPE2-K.dZTM4QDL1gDN1czW}
```


# Helpful Programs

In this challenge there was no direct manual, but using --help command gave details of the program.
I learnt that -p will give the key, and -g [key] will give the flag. Hence I invoked the program with those arguments.
``` bash
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v]
                                            [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give
                        you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 444
hacker@man~helpful-programs:~$ /challenge/challenge -g 444
Correct usage! Your flag: pwn.college{4HxeK-gM4bTlTThPhN4Oepb2c1G.ddjM4QDL1gDN1czW}
```


# Help for Builtins

In this challenge, challenge is a builtin shell command instead of a normal program, hence it does not have manual pages or help options. I used help challenge to get details and learnt that --secret with the right value will print the flag.
```bash
Connected!                                                                        
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune		display a fortune
      --version		display the version
      --secret VALUE	prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "w_odhRNM".
hacker@man~help-for-builtins:~$ challenge --secret w_odhRNM
Correct! Here is your flag!
pwn.college{w_odhRNMJ9MaddwuVTOnILCBJWN.dRTM5QDL1gDN1czW}
```




