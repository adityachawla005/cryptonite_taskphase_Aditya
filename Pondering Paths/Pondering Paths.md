# Challenge 1-The Root
This level required the use of invoking a pwn program under the root directory.

## Challenge Description
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!

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
<br>
<br>

# Challenge 2-Program and absolute Paths
This level required the use of invoking run program within challenge directory and the challenge directory is,in turn,in the root directory.

## Challenge Description
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge the directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give you the flag. Good luck!

## Solution

Writing the absolute path starting from root directory to challenge and invoking run program.


 ```bash
Connected!
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{8bE_Guw-65nXus-7qCFzXJSjM5E.dVDN1QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/2.png)

<br>
<br>
<br>
<br>

# Challenge 3-Position thy self
This level required navigating to a specific directory to invoke the /challenge/run program. 

## Challenge Description
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

```bash
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$ cd /some/new/directory
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

## Solution

Using cd to navigate to the specific path and then invoking the /challenge/run program.


 ```bash
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/aarch64-linux-gnu/include/gnu directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/aarch64-linux-gnu/include/gnu
hacker@paths~position-thy-self:/usr/aarch64-linux-gnu/include/gnu$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{kFBB5Zt9ZwFPazpn9tqa3YxQPVb.dZDN1QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/3.png)

<br>
<br>
<br>
<br>

# Challenge 4-Position elsewhere
This level required navigating to a specific directory to invoke the /challenge/run program. 

## Challenge Description
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

```bash
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$ cd /some/new/directory
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

## Solution

Using cd to navigate to the specific path and then invoking the /challenge/run program.


 ```bash
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /proc/67 directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /proc/67
hacker@paths~position-elsewhere:/proc/67$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{I5wcfMoMs9aaPzgIbhZPifsnznX.ddDN1QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/4.png)

<br>
<br>
<br>
<br>

# Challenge 5-Position yet elsewhere
This level required navigating to a specific directory to invoke the /challenge/run program. 

## Challenge Description
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

```bash
hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$ cd /some/new/directory
```

This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!

## Solution

Using cd to navigate to the specific path and then invoking the /challenge/run program.


 ```bash
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /etc directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /etc
hacker@paths~position-yet-elsewhere:/etc$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{EcKfy5VpjgpszaFNjJ1xJ6PB0_H.dhDN1QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/5.png)

<br>
<br>
<br>
<br>

# Challenge 6-implicit relative paths,from /
This challenge required the use of navigating to the root directory and making the use of relative path to invoke the run program.


## Challenge Description
Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.

However, the current working directory does matter for relative paths.


    A relative path is any path that does not start at root (i.e., it does not start with /).
    A relative path is interpreted relative to your current working directory (cwd).
    Your cwd is the directory that your prompt is currently located at.

This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

    If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
    If my cwd is /tmp, then a relative path to the file is a/b/my_file.
    If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.

Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊

## Solution

Using cd to navigate to the root directory  and then invoking the challenge/run program(absolute path).


 ```bash
hacker@paths~implicit-relative-paths-from-:~$ ls
COLLEGE               f       not-the-flag
Desktop               myflag  tmp
Intro_to_commands.md  new     zfLOZ95GHq0o5AfjB-mOoDVzz1.dRTM4QDL1kzM2czW}
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{A2t90JRESNPq0EN780jZtOzklnF.dlDN1QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/6.png)

<br>
<br>
<br>
<br>

# Challenge 6-implicit relative paths,from /
This challenge required the use of navigating to the root directory and making the use of relative path to invoke the run program.


## Challenge Description
Now you're familiar with the concept of referring to absolute paths and changing directories. If you put in absolute paths everywhere, then it really doesn't matter what directory you are in, as you likely found out in the previous three challenges.

However, the current working directory does matter for relative paths.


    A relative path is any path that does not start at root (i.e., it does not start with /).
    A relative path is interpreted relative to your current working directory (cwd).
    Your cwd is the directory that your prompt is currently located at.

This means how you specify a particular file, depends on where the terminal prompt is located.

Imagine we want to access some file located at /tmp/a/b/my_file.

    If my cwd is /, then a relative path to the file is tmp/a/b/my_file.
    If my cwd is /tmp, then a relative path to the file is a/b/my_file.
    If my cwd is /tmp/a/b/c, then a relative path to the file is ../my_file. The .. refers to the parent directory.

Let's try it here! You'll need to run /challenge/run using a relative path while having a current working directory of /. For this level, I'll give you a hint. Your relative path starts with the letter c 😊

## Solution

Using cd to navigate to the root directory  and then invoking the challenge/run program(absolute path).


 ```bash
hacker@paths~implicit-relative-paths-from-:~$ ls
COLLEGE               f       not-the-flag
Desktop               myflag  tmp
Intro_to_commands.md  new     zfLOZ95GHq0o5AfjB-mOoDVzz1.dRTM4QDL1kzM2czW}
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  opt   root  sbin  sys  usr
boot  dev        flag  lib   lib64  media   nix  proc  run   srv   tmp  var
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{A2t90JRESNPq0EN780jZtOzklnF.dlDN1QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/6.png)

<br>
<br>
<br>
<br>

# Challenge 7-explicit relative paths,from /
This challenge required the use of navigating to / directory and invoking run command inside challenge directory using a relative path while explicitly making the use of '.'.


## Challenge Description
Previously, your relative path was "naked": it directly specified the directory to descend into from the current directory. In this level, we're going to explore more explicit relative paths.

In most operating systems, including Linux, every directory has two implicit entries that you can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:

    /challenge
    /challenge/.
    /challenge/./././././././././
    /./././challenge/././

The following relative paths are also all identical to each other:

    challenge
    ./challenge
    ./././challenge
    challenge/.

Of course, if your current working directory is /, the above relative paths are equivalent to the above absolute paths.

This challenge will get you using . in your relative paths. Get ready!

## Solution
Navigate to / and then invoke the command using ./challenge/run.


 ```bash
Connected!                                                                        
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{I5iWSX0I06XEBwR-xcggQl8CgvW.dBTN1QDL1kzM2czW}
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/7.png)

<br>
<br>
<br>
<br>

# Challenge 8-implicit relative path
This challenge required the use of navigating to  challenge directory inside the root directory and invoking the run command using a relative path while explicitly making the use of '.'.


## Challenge Description
In this level, we'll practice refering to paths using . a bit more. This challenge will need you to run it from the /challenge directory. Here, things get slightly tricky.

Linux explicitly avoids automatically looking in the current directory when you provide a "naked" path. Consider the following:

```bash
hacker@dojo:~$ cd /challenge
hacker@dojo:/challenge$ run
```

This will not invoke /challenge/run. This is actually a safety measure: if Linux searched the current directory for programs every time you entered a naked path, you could accidentally execute programs in your current directory that happened to have the same names as core system utilities! As a result, the above commands will yield the following error:

```bash
bash: run: command not found
```

We'll explore the mechanisms behind this concept later, but in this challenge, will learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels. Give it a try now!

## Solution
Navigate to /challenge and then invoke the run command.


 ```bash
hacker@paths~implicit-relative-path:~$ cd /
hacker@paths~implicit-relative-path:/$ ./challenge
ssh-entrypoint: ./challenge: Is a directory
hacker@paths~implicit-relative-path:/$ cd ./challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{gw27MfcyN6MgolCe7SoaGmTm4rF.dFTN1QDL1kzM2czW}
```


<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/8.png)

<br>
<br>
<br>
<br>

# Challenge 9-home sweet home
In this challenge, we are required to invoke /challenge/run which will write a copy of the flag to any file.

1.Your argument must be an absolute path.
2.The path must be inside your home directory.
3.Before expansion, your argument must be three characters or less.

## Challenge Description
Every user has a home directory, typically under /home in the filesystem. In the dojo, you are the hacker user, and your home directory is /home/hacker. The home directory is typically where users store most of their personal files. As you make your way through pwn.college, this is where you'll store most of your solutions.

Typically, your shell session will start with your home directory as your current working directory. Consider the initial prompt:

hacker@dojo:~$

The ~ in this prompt is the current working directory, with ~ being shorthand for /home/hacker. Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Thus, whenever bash sees ~ provided as the start of an argument in a way consistent with a path, it will expand it to your home directory. Consider:

```bash
hacker@dojo:~$ echo LOOK: ~
LOOK: /home/hacker
hacker@dojo:~$ cd /
hacker@dojo:/$ cd ~
hacker@dojo:~$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~/asdf
hacker@dojo:~/asdf$ cd ~
hacker@dojo:~$ cd /home/hacker/asdf
hacker@dojo:~/asdf$
```

Note that the expansion of ~ is an absolute path, and only the leading ~ is expanded. This means, for example, that ~/~ will be expanded to /home/hacker/~ rather than /home/hacker/home/hacker.

Fun fact: cd will use your home directory as the default destination:

```bash
hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ cd
hacker@dojo:~$
```

Now it's your turn to play! In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

    Your argument must be an absolute path.
    The path must be inside your home directory.
    Before expansion, your argument must be three characters or less.

## Solution
Navigate to /challenge and then invoke the run command.


 ```bash
Connected!
hacker@paths~home-sweet-home:~$ cd /
hacker@paths~home-sweet-home:/$ ./challenge/run /home/hacker/n
The argument you provided must not have been longer than 3 characters (it's 
currently 14 characters long)!
hacker@paths~home-sweet-home:/$ ./challenge/run ~/n
Writing the file to /home/hacker/n!
... and reading it back to you:
pwn.college{8Se30_hY82YvdejiHGGXJe_VE4Z.dNzM4QDL1kzM2czW}
hacker@paths~home-sweet-home:/$
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Pondering%20Paths/assets/9.png)



