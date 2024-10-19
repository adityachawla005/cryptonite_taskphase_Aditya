# Challenge 1-Learning from Documentation
This challenge guides us on how to use documentation to run certain programs.

## Challenge Description
The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line. This module will mostly dig into that concept, as a proxy for figuring out how to use the programs in general. Through the rest of the module, you'll go through various ways of asking the environment for help for the programs, but first, we'll dig into the concept of reading documentation.

The correct usage of programs depends, in a large part, in the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:

    Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

Given that knowledge, go get the flag!


## Solution

Invoking the /challenge/challenge with --giveflag argument.

 ```bash
Connected!
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{EoZopqIEMdFvujIxO8vgqO8aswg.dRjM5QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Digesting%20Documentation/assets/1.png)

<br>
<br>
<br>
<br>

# Challenge 2-Learning Complex usage
This challenge guides us on how to use documentation to run certain programs.

## Challenge Description
While using most commands is straightforward, the usage of some commands can get quite complex. For example, the arguments to commands like sed and awk, which we're definitely not getting into right now, are entire programs in an esoteric programming language! Somewhere on the spectrum between cd and awk are commands that take arguments to their arguments...

This sounds crazy, but you've already encountered this with the find challenge in Basic Commands. find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.

Here is this challenge's documentation for /challenge/challenge:

    Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the challenge!

Given that documentation, go get the flag!

## Solution

Invoking the /challenge/challenge with --printfile argument along with the path.

 ```bash
Connected!
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{AjBKklfv2ugieWVn5pRTA5jTxDx.dVjM5QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Digesting%20Documentation/assets/2.png)

<br>
<br>
<br>
<br>

# Challenge 3-Reading Manuals
This challenge requires the use of man command to read the manual of a specific program.

## Challenge Description
This challenge introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument. For example, let's say we wanted to learn about the yes command (yes, this is a real command):

```bash
hacker@dojo:~$ man yes

This will display the manual page for yes, which will look something like this:

YES(1)                           User Commands                          YES(1)

NAME
       yes - output a string repeatedly until killed

SYNOPSIS
       yes [STRING]...
       yes OPTION

DESCRIPTION
       Repeatedly output a line with all specified STRING(s), or 'y'.

       --help display this help and exit

       --version
              output version information and exit

AUTHOR
       Written by David MacKenzie.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report any translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
       GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
       This is free software: you are free  to  change  and  redistribute  it.
       There is NO WARRANTY, to the extent permitted by law.

SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/yes>
       or available locally via: info '(coreutils) yes invocation'

GNU coreutils 8.32               February 2022                          YES(1)

The important sections are:

NAME(1)                           CATEGORY                          NAME(1)

NAME
	This gives the name (and short description) of the command or
	concept discussed by the page.

SYNOPSIS
	This gives a short usage synopsis. These synopses have a standard
	format. Typically, each line is a different valid invocation of the
	command, and the lines can be read as:

	COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
	COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...

DESCRIPTION
	Details of the command or concept, with detailed descriptions
	of the various options.

SEE ALSO
	Other man pages or online resources that might be useful.

COLLECTION                        DATE                          NAME(1)
```
You can scroll around the manpage with your arrow keys and PgUp/PgDn. When you're done reading the manpage, you can hit q to quit.

Manpages are stored in a centralized database. If you're curious, this database lives in the /usr/share/man directory, but you never need to interact with it directly: you just query it using the man command. The arguments to the man command aren't file paths, but just the names of the entries themselves (e.g., you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage).

The challenge in this challenge has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challenge!

## Solution
Using man command with challenge to find the option.

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

       --szfqof NUM
              print the flag if NUM is 950

AUTHOR
       Written by Zardus.
hacker@man~reading-manuals:~$ /challenge/challenge --szfqof 950
Correct usage! Your flag: pwn.college{szfLOZ95GHq0o5AfjB-mOoDVzz1.dRTM4QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Digesting%20Documentation/assets/3.png)

<br>
<br>
<br>
<br>


# Challenge 4-Searching Manuals
This challenge requires the use of man command along with / to read the manual and search for srguments of a specific program.

## Challenge Description
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

Find the option that will give you the flag by reading the challenge man page.

## Solution

Using man command with challenge.

```bash
Connected!
hacker@man~searching-manuals:~$ man challenge
```

 ```bash
CHALLENGE(1)             Challenge Commands            CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right argument.

       --fortune
              read a fortune

       --version
              output version information and exit

       --kkmscvz
              A neat argument, but not the right one.

       --etaa A neat argument, but not the right one.

       --jbktj
              A neat argument, but not the right one.

       --ihgt A neat argument, but not the right one.
```

After using / to search for the word flagt and using n to scroll through searches:

```bash

       --famy This argument will give you the flag!!

hacker@man~searching-manuals:~$ /challenge/challenge --famy
Initializing...
Correct usage! Your flag: pwn.college{0xVPv0b1_5jyshHdOZNgsEUgfYP.dVTM4QDL1kzM2czW}



```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Digesting%20Documentation/assets/4.png)

<br>
<br>
<br>
<br>

# Challenge 5-Searching for manuals
This level required us to use man man command and man -k command to find the correct manual and get the flag.

## Challenge Description
This level is tricky: it hides the manpage for the challenge by randomizing its name. Luckily, all of the man pages are gathered in a searchable database, so you'll be able to search the man page database to find the hidden challenge man page! To figure out how to search for the right man page, read the man page manpage by doing: man man!

HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the man page is randomly named, you still actually use /challenge/challenge to get the flag!

## Solution

First using man man to view different manuals.

 ```bash
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


```
For finding challenge man page,using man -k challenge:

```bash
hacker@man~searching-for-manuals:~$ man -k challenge
ocjynkkbsi (1)       - print the flag!
```
Now viewing the man page for the keyword:

```bash
hacker@man~searching-for-manuals:~$ man ocjynkkbsi

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

       --ocjynk NUM
              print the flag if NUM is 840

AUTHOR
       Written by Zardus.
```
Printing the flag:
```bash
hacker@man~searching-for-manuals:~$ /challenge/challenge --ocjynk 840
Correct usage! Your flag: pwn.college{UASBIo8Gc-jyBU4nO0-kkb2Fsie.dZTM4QDL1kzM2czW}
hacker@man~searching-for-manuals:~$ 
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Digesting%20Documentation/assets/5.png)

<br>
<br>
<br>
<br>
