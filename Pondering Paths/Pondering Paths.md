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
This level required navigating to a specific directory to invoke the /challenge/run program. 

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


