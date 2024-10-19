# Challenge 1-cat:not the pet,but the command!
This level required the use of reading the contents of flag file with cat command.

## Challenge Description
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:

cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:

```bash
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
```

Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!



## Solution

Using the command cat with flag to read its contents in the current directory.

 ```bash
Connected!
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{4VQhCrQjskrYC-bzBM0PyXwCOZs.dFzN1QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/1.png)

<br>
<br>
<br>
<br>

# Challenge 2-catting absolute paths
This level required the use of reading the contents of flag file with cat command and the file's absolute path.

## Challenge Description
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:

```bash
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...
```

In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.


## Solution

Using the command cat with absolute path /flag to read its contents.

 ```bash
Connected!
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{MetMmt7W_RBxzWKSQ8aCq42cCAn.dlTM5QDL1kzM2czW}
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/2.png)

<br>
<br>
<br>
<br>

# Challenge 3-more catting practice
This level required the use of reading the contents of flag file with cat command and the file's absolute path.

## Challenge Description
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must 

In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.


## Solution

 Using the command cat with absolute path to read its contents.

 ```bash
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/systemd/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/systemd/flag
pwn.college{U0b1cVSr7WAGywrVCyrdufGEVSy.dBjM5QDL1kzM2czW}
```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/3.png)

<br>
<br>
<br>
<br>

# Challenge 4-grepping for a needle in a haystack
This level required the use of grep command to find the flag in a file.

## Challenge Description
Sometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn on way here:

```bash
hacker@dojo:~$ grep SEARCH_STRING /path/to/file
```

Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. Grep it for the flag!

HINT: The flag always starts with the text pwn.college.

## Solution

Use grep command with the string to be searched along with the absolute path of the file to find the flag.

 ```bash
Connected!
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{QtOsrVPxIp17MiSoLSzwcRIE8kX.ddTM4QDL1kzM2czW}

```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/4.png)

<br>
<br>
<br>
<br>

# Challenge 5-listing files
This level required the use of ls command to list the files.

## Challenge Description
So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:

```bash
hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
```

In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.

## Solution

Use ls to find the renamed run command and then invoke it.

 ```bash
Connected!
onnected!
hacker@commands~listing-files:~$ ls /challenge
19507-renamed-run-19918  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/19507-renamed-run-19918
Yahaha, you found me! Here is your flag:
pwn.college{UJB1woCR1YvHBMsdqqO1r3TPKMW.dhjM4QDL1kzM2czW}

```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/5.png)

<br>
<br>
<br>
<br>


# Challenge 6-touching files
This level required the use of touch command to create files.

## Challenge Description
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:

```bash
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
```

It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!

## Solution

Use touch command to create two files in tmp directory.

 ```bash
Connected!
hacker@commands~touching-files:~$ cd /tmp
hacker@commands~touching-files:/tmp$ ls
bin  hsperfdata_root  tmp.G9qthVCks5
hacker@commands~touching-files:/tmp$ touch college
hacker@commands~touching-files:/tmp$ touch pwn
hacker@commands~touching-files:/tmp$ cd
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{kMOt7QVKqfTUrMag36Y3IzkEbDO.dBzM4QDL1kzM2czW}
```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/6.png)

<br>
<br>
<br>
<br>


# Challenge 7-removing files
This level required the use of rm command to remove a file.

## Challenge Description
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:

```bash
hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
```

Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!

## Solution

Delete the delete_me file using rm command then invoke the command /challenge/check.

 ```bash
Connected!
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{o92fTefLwrEpc40vTaDBDACzE-s.dZTOwUDL1kzM2czW}
```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/7.png)

<br>
<br>
<br>
<br>


# Challenge 8-hidden files
This level required the use of the -a flag along with ls command to view hidden files.

## Challenge Description

Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

```bash
hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
```

Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.

## Solution

Use ls -a to find the hidden flag file inside / directory.

 ```bash
Connected!
hacker@commands~hidden-files:~$ ls -a /
.           .flag-63465271714  challenge  home   lib64   mnt  proc  sbin  tmp
..          bin                dev        lib    libx32  nix  root  srv   usr
.dockerenv  boot               etc        lib32  media   opt  run   sys   var
hacker@commands~hidden-files:~$ cat /.flag-63465271714
pwn.college{8OIoGqhSEGdBb6HR4L4nr6CFCJi.dBTN4QDL1kzM2czW}
```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/8.png)

<br>
<br>
<br>
<br>


# Challenge 9-An epic Filesystem quest
This level required us to follow the hints and make the use of cd,ls and cat commands to find the flag.

## Challenge Description
With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:

```bash

hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
```

That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:

0.Your first clue is in /. Head on over there.
1.Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
2.cat that file to read the clue!
3.Depending on what the clue says, head on over to the next directory (or don't!).
4.Follow the clues to the flag!

Good luck!

## Solution
According to the clue first we changed directory to root.We used ls and cat to read the file BLUEPRINT.According to the clue we changed directories to /opt/linux/linux-5.4/drivers/media/usb/hackrf.Again using ls and cat to read the file EVIDENCE.Since we cant use cd to navigate to the directory given in the clue,we use ls and cat with the absolute path to read the contents of the file DOSSIER-TRAPPED.We had to change the directory to /usr/lib/python3/dist-packages/twisted/mail/__pycache__ as given in the clue.We make use of ls -a to view the hidden file .TRACE and cat to read it.Once again changing directories ,using ls -a to view the hidden file .WHISPER amd cat to read the file.We navigate to /usr/share/maxima-sage/5.42.2/share/contrib according to the clue and read the ALERT file using the ls and cat command.Further chaging the directory again to /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/constants/cgc/__pycache__ and view the GIST file using ls and cat command.Changing the directory again to /usr/lib/python3/dist-packages/hyperlink/__pycache__ according to the clue and using ls and cat to view NUGGET file.Now once again we make use of ls and cat along with absolute paths to view the TEASER-TRAPPED file and we find the flag.


 ```bash
 Connected!
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
BLUEPRINT  challenge  flag  lib32   media  opt   run   sys  var
bin        dev        home  lib64   mnt    proc  sbin  tmp
boot       etc        lib   libx32  nix    root  srv   usr
hacker@commands~an-epic-filesystem-quest:/$ cat BLUEPRINT
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/drivers/media/usb/hackrf
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/drivers/media/usb/hackrf
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/usb/hackrf$ ls
EVIDENCE  Kconfig  Makefile  hackrf.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/usb/hackrf$ cat EVIDENCE
Lucky listing!
The next clue is in: /usr/include/fflas-ffpack/paladin

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/usb/hackrf$ ls /usr/include/fflas-ffpack/paladin
DOSSIER-TRAPPED  fflas_plevel1.h     parallel.h           pfgemv.inl
blockcuts.inl    kaapi_routines.inl  pfgemm_variants.inl
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/usb/hackrf$ cat /usr/include/fflas-ffpack/paladin/DOSSIER-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/lib/python3/dist-packages/twisted/mail/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/usb/hackrf$ ^C
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/drivers/media/usb/hackrf$ cd /usr/lib/python3/dist-packages/twisted/mail/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/twisted/mail/__pycache__$ ls -a
.                        _except.cpython-38.pyc     protocols.cpython-38.pyc
..                       imap4.cpython-38.pyc       relay.cpython-38.pyc
.TRACE                   interfaces.cpython-38.pyc  smtp.cpython-38.pyc
__init__.cpython-38.pyc  pop3.cpython-38.pyc
_cred.cpython-38.pyc     pop3client.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/twisted/mail/__pycache__$ cat .TRACE
Congratulations, you found the clue!
The next clue is in: /usr/share/locale/ar/LC_MESSAGES

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/twisted/mail/__pycache__$ cd /usr/share/locale/ar/LC_MESSAGES
hacker@commands~an-epic-filesystem-quest:/usr/share/locale/ar/LC_MESSAGES$ ls -a
.         apt.mo         iso_3166-3.mo  iso_639-2.mo  iso_639_3.mo
..        iso_15924.mo   iso_3166.mo    iso_639-3.mo  libapt-pkg6.0.mo
.WHISPER  iso_3166-1.mo  iso_4217.mo    iso_639.mo    sphinx.mo
hacker@commands~an-epic-filesystem-quest:/usr/share/locale/ar/LC_MESSAGES$ cat .WHISPER
Yahaha, you found me!
The next clue is in: /usr/share/maxima-sage/5.42.2/share/contrib

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/locale/ar/LC_MESSAGES$ cd /usr/share/maxima-sage/5.42.2/share/contrib
hacker@commands~an-epic-filesystem-quest:/usr/share/maxima-sage/5.42.2/share/contrib$ ls
ALERT                     floatproperties.lisp  opsubst.lisp
Eulix                     format                prim
Grobner                   fresnel               quaternion.mac
README                    gentran               rand
Zeilberger                gf                    ratpow.lisp
alt-display               ggf.mac               rkf45
altsimp                   graph2d.lisp          rtest_augmented_lagrangian.mac
augmented_lagrangian.mac  impdiff.mac           rtest_engineering_format.mac
binsplit                  implicit_plot.lisp    rtest_ggf.mac
bitwise                   integration           rtest_wrstcse.mac
bode.mac                  levin                 sarag
boolsimp                  lindstedt.mac         simplifying.lisp
celine.mac                lll.lisp              smath
cgrind.lisp               log10.mac             state
chebformax.lisp           lurkmathml            stirling.mac
clebsch_gordan.mac        makeOrders.mac        symplectic_ode
clebsh-gordan.tex         maxima-odesolve       tex2ooo.lisp
colorterm.lisp            maxima-server.lisp    timeout.lisp
coma                      maximaMathML          tocl.lisp
devine.mac                mcclim                trigtools
diag.mac                  meijer_g.tex          unicodedata
diag_test.mac             meijer_gv2.mac        unit
diffequations             namespaces            unwind_protect.lisp
elliptic_curves           noninteractive        vector3d
engineering-format.lisp   odes                  wrstcse.dem
f90.lisp                  operatingsystem       wrstcse.mac
hacker@commands~an-epic-filesystem-quest:/usr/share/maxima-sage/5.42.2/share/contrib$ cat ALERT
Yahaha, you found me!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/constants/cgc/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/maxima-sage/5.42.2/share/contrib$ cd /opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/constants/cgc/__pycache__
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/constants/cgc/__pycache__$ ls
GIST                     i386.cpython-38.pyc       s390x.cpython-38.pyc
__init__.cpython-38.pyc  ia64.cpython-38.pyc       sparc.cpython-38.pyc
aarch64.cpython-38.pyc   mips.cpython-38.pyc       sparc64.cpython-38.pyc
alpha.cpython-38.pyc     powerpc.cpython-38.pyc    thumb.cpython-38.pyc
amd64.cpython-38.pyc     powerpc64.cpython-38.pyc
arm.cpython-38.pyc       s390.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/constants/cgc/__pycache__$ cat GIST
Tubular find!
The next clue is in: /usr/lib/python3/dist-packages/hyperlink/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/constants/cgc/__pycache__$ cd /usr/lib/python3/dist-packages/hyperlink/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/hyperlink/__pycache__$ ls
NUGGET  __init__.cpython-38.pyc  _url.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/hyperlink/__pycache__$ cat NUGGET
Yahaha, you found me!
The next clue is in: /usr/local/etc

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/hyperlink/__pycache__$ ls /usr/local/etc
TEASER-TRAPPED  jupyter
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/hyperlink/__pycache__$ cat /usr/local/etc/TEASER-TRAPPED
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{Q5a-bYwjjdPzcuuYO6hrXn_iAlD.dljM4QDL1kzM2czW}


```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/9.png)

<br>
<br>
<br>
<br>

# Challenge 10-making directories
This level required the use of making directories using mkdir command.

## Challenge Description
We can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:

```bash
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
```
Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!

Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!



## Solution

Using the mkdir command making a directory in /tmp and touch command to make a college file in it.

 ```bash
Connected!                                                                        
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ cd /tmp/pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{wcaFX1YIIcUPLx6viWOQ94q9fcG.dFzM4QDL1kzM2czW}
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/10.png)

<br>
<br>
<br>
<br>
