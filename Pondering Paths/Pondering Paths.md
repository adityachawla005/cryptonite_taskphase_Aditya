# The Root
This level required the use of invoking a pwn program under the root directory.

## Challenge Description
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!

In this case, the command was echo, and Hello and Hackers! were the two arguments to echo. Simple!

In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers. Try it now!

## Solution

Writing the absolute path starting from the root directory to involking pwn.

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
