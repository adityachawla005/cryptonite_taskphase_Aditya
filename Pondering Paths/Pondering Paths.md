# Challenge 1-The Root
This level required the use of invoking a pwn program under the root directory.

## Challenge Description
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!

In this case, the command was echo, and Hello and Hackers! were the two arguments to echo. Simple!

In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers. Try it now!

## Solution

Writing the absolute path starting from the root directory to invoking pwn.

 ```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{QjppxbTA2-g-MtPPMXn1VdBzrc-.dhzN5QDL1kzM2czW}
hacker@paths~the-root:~$ 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/1.png)

<br>
<br>

# Challenge 2-Program and absolute Paths
This level required the use of invoking run program within challenge directory and th challenge directory is,in turn,in the root directory

## Challenge Description
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge the directory 

is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give you the 

flag. Good luck!

 ```bash
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{QjppxbTA2-g-MtPPMXn1VdBzrc-.dhzN5QDL1kzM2czW}
hacker@paths~the-root:~$ 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/2.png)
