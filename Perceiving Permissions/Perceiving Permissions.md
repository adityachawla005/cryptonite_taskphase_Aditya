# Challenge 1-Changing File Ownership
This challenge required us to change ownership of /flag to hacker using chown.

## Challenge Description

First things first: file ownership. Every file in Linux is owned by a user on the system. Most often, in your day-to-day life, that user is the user you log in as every day.

On a shared system (such as in a computer lab), there might be many people with different user accounts, all with their own files in their own home directories. But even on a non-shared system (such as your personal PC), Linux still has many "service" user accounts for different tasks.

The two most important user accounts are:

    Your user account! On pwn.college, this is the hacker user, regardless of what your username is.
    root. This is the administrative account and, in most security situations, the ultimate prize. If you take over the root user, you've almost certainly achieved your hacking objective!

So what? Well, it turns out that the way that we prevent you from just doing cat /flag is by having /flag owned by the root user, configure its permissions so that no other user can read it (you will learn how to do that later), and configure the actual challenge to run as the root user (you will learn how to do this later as well). The result is that when you do cat /flag, you get:

```bash
hacker@dojo:~$ ls -l /flag
-r-------- 1 root root 53 Jul  4 04:47 /flag
hacker@dojo:~$ cat /flag
cat: /flag: Permission denied
hacker@dojo:~$
```

Here, you can see that the flag is owned by the root user (the first root in that line) and the root group (the second root in that line). When we try to read it as the hacker user, we are denied. However, if we were root (a hacker's dream!), we would have no problem reading this file:
```bash
root@dojo:~# cat /flag
pwn.college{demo_flag}
root@dojo:~#
```
Interestingly, we can change the ownership of files! This is done via the chown (change owner) command:

chown [username] [file]

Typically, chown can only be invoked by the root user. Let's pretend that we're root again (that never gets old!), and watch a typical use of chown:
```bash
root@dojo:~# mkdir pwn_directory
root@dojo:~# touch college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root root    0 May 22 13:42 college_file
drwxr-xr-x 2 root root 4096 May 22 13:42 pwn_directory
root@dojo:~# chown hacker college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 hacker root    0 May 22 13:42 college_file
drwxr-xr-x 2 root   root 4096 May 22 13:42 pwn_directory
root@dojo:~#
```
college_file's owner has been changed to the hacker user, and how hacker can do with it whatever root had been able to do with it! If this was the /flag file, that means that the hacker user would be able to read it!

In this level, we will practice changing the owner of the /flag file to the hacker user, and then the flag. For this challenge only, I made it so that you can use chown to your heart's content as the hacker user (again, typically, this requires you to be root). Use this power wisely and chown away!

## Solution
Changing the /flag permission to hacker user and get the flag.

 ```bash
Connected!
hacker@permissions~changing-file-ownership:~$ ls -l /flag
-r-------- 1 root root 58 Oct 19 20:30 /flag
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ ls -l /flag
-r-------- 1 hacker root 58 Oct 19 20:30 /flag
hacker@permissions~changing-file-ownership:~$ cat flag
cat: flag: No such file or directory
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{kickxmzhlFnq4uZptgGZYIV130W.dFTM2QDL1kzM2czW}
hacker@permissions~changing-file-ownership:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-1.png)

<br>
<br>
<br>
<br>

# Challenge 2-Groups and Files
This challenge required us to change group of /flag file using chgroup command.

## Challenge Description
Sharing is caring, and sharing is built into Linux's design. Files have both an owning user and group. A group can have multiple users in it, and a user can be a member of multiple groups.

You can check what groups you are part of with the id command:
```bash
hacker@dojo:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@dojo:~$
```
Here, the hacker user is only in the hacker group. The most common use-case for groups is to control access to different system resources. For example, "Practice Mode" in pwn.college grants you root access to allow better debugging and so on. This is handled by giving you an extra group when you launch in practice mode:
```bash
hacker@dojo:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker),27(sudo)
hacker@dojo:~$
```
A typical main user of a typical Linux desktop has a lot of groups. For example, this is Zardus' desktop:
```bash
zardus@yourcomputer:~$ id
uid=1000(zardus) gid=1000(zardus) groups=1000(zardus),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),106(netdev),114(bluetooth),117(lpadmin),120(scanner),995(docker)
zardus@yourcomputer:~$
```
All these groups give Zardus the ability to read CDs and floppy disks (who does that anymore?), administer the system, play music, draw to the video monitor, use bluetooth, and so on. Often, this access control happens via group ownership on the filesystem! For example, graphical output can be done via the special /dev/fb0 file:
```bash
zardus@yourcomputer:~$ ls -l /dev/fb0
crw-rw---- 1 root video 29, 0 Jun 30 23:42 /dev/fb0
zardus@yourcomputer:~$
```
This file is a special device file (type c means it is a "character device"), and interacting with it results in changes to the display output (rather than changes to disk storage, as for a normal file!). Zardus' user account on his machine can interact with it because the the file has a group ownership of video, and Zardus is a member of the video group.

No such luck for the /flag file in the dojo, though! Consider the following:
```bash
hacker@dojo:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@dojo:~$ ls -l /flag
-r--r----- 1 root root 53 Jul  4 04:47 /flag
hacker@dojo:~$ cat /flag
cat: /flag: Permission denied
hacker@dojo:~$
```
Here, the flag file is owned by the root user and the root group, and the hacker user is neither the root user nor a member of the root group, so the file cannot be accessed. Luckily, group ownership can be changed with the chgrp (change group) command! Unless you have write access to the file and membership in the new group, this typically requires root access, so let's check it out as root:
```bash
root@dojo:~# mkdir pwn_directory
root@dojo:~# touch college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root root    0 May 22 13:42 college_file
drwxr-xr-x 2 root root 4096 May 22 13:42 pwn_directory
root@dojo:~# chgrp hacker college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root hacker    0 May 22 13:42 college_file
drwxr-xr-x 2 root root   4096 May 22 13:42 pwn_directory
root@dojo:~#
```
In this level, I have made the flag readable by whatever group owns it, but this group is currently root. Luckily, I have also made it possible for you to invoke chgrp as the hacker user! Change the group ownership of the flag file, and read the flag!

## Solution
Changing the /flag group to hacker group and get the flag.

 ```bash
Connected!
hacker@permissions~groups-and-files:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~groups-and-files:~$ ls -l flag
ls: cannot access 'flag': No such file or directory
hacker@permissions~groups-and-files:~$ ls -l /flag
-r--r----- 1 root root 58 Oct 19 20:43 /flag
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{g5CJkttIDzeKPhYJOF-dYuKcvrD.dFzNyUDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-2.png)

<br>
<br>
<br>
<br>


# Challenge 3-Changing Permissions
This challenge required us to change group of /flag to hacker using id and chgrp.

## Challenge Description

In the previous levels, you may have noticed that your hacker user is a member of the hacker group, and that zardus is a member of the zardus group. There is a convention in Linux that every user has their own group, but this does not have to be the case. For example, many computer labs will put all of their users into a single, shared users group.

The point is, you've used hacker for the group before, but in this level, that is not going to work. I'll still allow you to use chgrp, but I have randomized the name of the group that your user is in. You will need to use the id command to figure that name out, then chgrp to victory!

## Solution
Changing the /flag permission to hacker user and get the flag.

 ```bash
Connected!
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp91) groups=1000(grp91)
hacker@permissions~fun-with-groups-names:~$ ^C
hacker@permissions~fun-with-groups-names:~$ chgrp grp91 /flag
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{kPys8tPF2dsMbIfQ6bitPdBn6aZ.dJzNyUDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-3.png)

<br>
<br>
<br>
<br>

# Challenge 4-Changing Permissions
This challenge required us to use chmod to change file permissions for the /flag file.

## Challenge Description

So now we're well-versed in ownership. Let's talk about the other side of the coin: file permissions. Recall our example:

```bash
hacker@dojo:~$ mkdir pwn_directory
hacker@dojo:~$ touch college_file
hacker@dojo:~$ ls -l
total 4
-rw-r--r-- 1 hacker hacker    0 May 22 13:42 college_file
drwxr-xr-x 2 hacker hacker 4096 May 22 13:42 pwn_directory
hacker@dojo:~$
```
As a reminder, the first character there is the file type. The next nine characters are the actual access permissions of the file or directory, split into 3 characters denoting permissions for the owning user (now you understand this!), 3 characters denoting the permissions for the owning group (now you understand this as well!), and 3 characters denoting the permissions that all other access (e.g., by other users and other groups) has to the file.

Each character of the three represent permission for a different type:

r - user/group/other can read the file (or list the directory)
w - user/group/other can modify the files (or create/delete files in the directory)
x - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
- - nothing 

For college_file above, the rw-r--r-- permissions entry decodes to:

    r: the user that owns the file (user hacker) can read it
    w: the user that owns the file (user hacker) can write to it
    -: the user that owns the file (user hacker) cannot execute it
    r: users in the group that owns the file (group hacker) can read it
    -: users in the group that owns the file (group hacker) cannot write to it
    -: users in the group that owns the file (group hacker) cannot execute it
    r: all other users can read it
    -: all other users cannot write to it
    -: all other users cannot execute it

Now, let's look at the default permissions of /flag:
```bash
hacker@dojo:~$ ls -l /flag
-r-------- 1 root root 53 Jul  4 04:47 /flag
hacker@dojo:~$
```
Here, there is only one bit set: the read permission for the owning user (in this case, root). Members of the owning group (the root group) and all other users have no access to the file.

You might be wondering how the chgrp levels worked, if there is no group access to the file. Well, for those levels, I set the permissions differently:
```bash
hacker@dojo:~$ ls -l /flag
-r--r----- 1 root root 53 Jul  4 04:47 /flag
hacker@dojo:~$
```
The group had access! That is why chgrping the file enabled you to read the file.

Anyways! Like ownership, file permissions can also be changed. This is done with the chmod (change mode) command. The basic usage for chmod is:

chmod [OPTIONS] MODE FILE

You can specify the MODE in two ways: as a modification of the existing permissions mode, or as a completely new mode to overwrite the old one.

In this level, we will cover the former: modifying an existing mode. chmod allows you to tweak permissions with the mode format of WHO+/-WHAT, where WHO is user/group/other and WHAT is read/write/execute. For example, to add read access for the owning user, you would specify a mode of u+r. write and execute access for the group and the other (or all the modes) are specified the same way. More examples:

    u+r, as above, adds read access to the user's permissions
    g+wx adds write and execute access to the group's permissions
    o-w removes write access for other users
    a-rwx removes all permissions for the user, group, and world

So:
```bash
root@dojo:~# mkdir pwn_directory
root@dojo:~# touch college_file
root@dojo:~# ls -l
total 4
-rw-r--r-- 1 root root    0 May 22 13:42 college_file
drwxr-xr-x 2 root root 4096 May 22 13:42 pwn_directory
root@dojo:~# chmod go-rwx *
root@dojo:~# ls -l
total 4
-rw------- 1 hacker root    0 May 22 13:42 college_file
drwx------ 2 root   root 4096 May 22 13:42 pwn_directory
root@dojo:~#
```
In this challenge, you must change the permissions of the /flag file to read it! Typically, you need to have write access to the file in order to change its permissions, but I have made the chmod command all-powerful for this level, and you can chmod anything you want even though you are the hacker user. This is an ultimate power. The /flag file is owned by root, and you can't change that, but you can make it readable. Go and solve this!


## Solution
Using chmod +r to change permission of group and other of /flag file to -r.

```bash
Connected!
hacker@permissions~changing-permissions:~$ ls -l /flag
-r-------- 1 root root 58 Oct 19 21:11 /flag
hacker@permissions~changing-permissions:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~changing-permissions:~$ chmod +r /flag
hacker@permissions~changing-permissions:~$ id
uid=1000(hacker) gid=1000(hacker) groups=1000(hacker)
hacker@permissions~changing-permissions:~$ ls -l /flag
-r--r--r-- 1 root root 58 Oct 19 21:11 /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{IL_LvJk7Yx3LJw0Tqp1prwr0mL2.dNzNyUDL1kzM2czW}
hacker@permissions~changing-permissions:~$ 
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-4.png)

<br>
<br>
<br>
<br>

# Challenge 5-Executable Files
This challenge required us to use chmod to change file permissions to make /challenge/flag file executable.


## Challenge Description
So far, you have mostly been dealing with read permissions. This makes sense, because you have been making the /flag file readable to read it. In this level, we will explore execute permissions.

When you invoke a program, such as /challenge/run, Linux will only actually execute it if you have execute-access to the program file. Consider:
```bash
hacker@dojo:~$ ls -l /challenge/run
-rwxr-xr-x 1 root root    0 May 22 13:42 /challenge/run
hacker@dojo:~$ /challenge/run
Successfully ran the challenge!
hacker@dojo:~$
```
In this case, /challenge/run runs because it is executable by the hacker user. Because the file is owned by the root user and root group, this requires that the execute bit is set on the other permissions). If we remove these permissions, the execution will fail!
```bash
hacker@dojo:~$ chmod o-x /challenge/run
hacker@dojo:~$ ls -l /challenge/run
-rwxr-xr-- 1 root root    0 May 22 13:42 /challenge/run
hacker@dojo:~$ /challenge/run
bash: /challenge/run: Permission denied
hacker@dojo:~$
```
In this challenge, the /challenge/run program will give you the flag, but you must first make it executable! Remember your chmod, and get /challenge/run to tell you the flag!


## Solution
Using chmod+x to change permission of /challenge/flag file to make it executable.

```bash
Connected!
hacker@permissions~executable-files:~$ /challenge/run
ssh-entrypoint: /challenge/run: Permission denied
hacker@permissions~executable-files:~$ ls -l /challenge/run
-r--r--r-- 1 hacker hacker 32 Jul  4 06:37 /challenge/run
hacker@permissions~executable-files:~$ chmod +x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{MP-f3V3stzgjEszwirPWmAuUNPk.dJTM2QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-5.png)

<br>
<br>
<br>
<br>


# Challenge 6-Permission tweaking Practice
This challenge required us to use chmod to change file permissions for /challenge/flag file.


## Challenge Description
You think you can chmod? Let's practice!

This challenge will ask you to change the permissions of the /challenge/pwn file in specific ways a few times in a row. If you get the permissions wrong, the game will reset and you can try again. If you get the permissions right eight times in a row, the challenge will let you chmod /flag to make it readable for yourself :-) Launch /challenge/run to get started!

## Solution

```bash
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g-r,o-r /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rw-------
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rw----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+rw /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": rw-rw----
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw-rw---x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ ^C
hacker@permissions~permission-tweaking-practice:~$ chmod o+x /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": rw-rw---x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rw-rw-r-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+r /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": rw-rw-r-x
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--r--r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-w,g-w /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": r--r--r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r--r-----
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o-rx /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": r--r-----
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--rwx---
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+wx /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": r--rwx---
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": ----wx---
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u-r,g-r /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod +r /flag
hacker@permissions~permission-tweaking-practice:~$ cat flag
cat: flag: No such file or directory
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{UjAtMDCl-HlTuDM8_Me4rsoVs04.dBTM2QDL1kzM2czW}
hacker@permissions~permission-tweaking-practice:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-6.png)

<br>
<br>
<br>
<br>

# Challenge 7-Permissions Setting Practice
This challenge required us to use '=' symbol to set permissions overwriting the old permissions..

## Challenge Description

FIn addition to adding and removing permissions, as in the previous level, chmod can also simply set permissions altogether, overwriting the old ones. This is done by using = instead of - or +. For example:

    u=rw sets read and write permissions for the user, and wipes the execute permission
    o=x sets only executable permissions for the world, wiping read and write
    a=rwx sets read, write, and executable permissions for the user, group, and world!

But what if you want to change user permissions in a different way as group permissions? Say, you want to set rw for the owning user, but only r for the owning group? You can achieve this by chaining multiple modes to chmod with ,!

    chmod u=rw,g=r /challenge/pwn will set the user permissions to read and write, and the group permissions to read-only
    chmod a=r,u=rw /challenge/pwn will set the user permissions to read and write, and the group and world permissions to read-only

Additionally, you can zero out permissions with -:

    chmod u=rw,g=r,o=- /challenge/pwn will set the user permissions to read and write, the group permissions to read-only, and the world permissions to nothing at all

Keep in mind, that -, appearing after = is in a different context than if it appeared directly after the u, g, or o (in which case, it would cause specific bits to be removed, not everything).

This level extends the previous level by requesting more radical permission changes, which you will need = and ,-chaining to achieve. Good luck!

## Solution
Setting the permissions using the = sign.

 ```bash
Connected!                                                                        
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 0 (of 8)!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxr-x--x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=rx,o=x /challenge/pwn
You set the correct permissions!
Round 1 (of 8)!

Current permissions of "/challenge/pwn": rwxr-x--x
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r----x--x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,g=x /challenge/pwn
You set the correct permissions!
Round 2 (of 8)!

Current permissions of "/challenge/pwn": r----x--x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -----x-wx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=-,o=wx /challenge/pwn
You set the correct permissions!
Round 3 (of 8)!

Current permissions of "/challenge/pwn": -----x-wx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wxrw--wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=rw /challenge/pwn
You set the correct permissions!
Round 4 (of 8)!

Current permissions of "/challenge/pwn": -wxrw--wx
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": rwx-w--w-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=w,o=w /challenge/pwn
You set the correct permissions!
Round 5 (of 8)!

Current permissions of "/challenge/pwn": rwx-w--w-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w--wxrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=wx,o=rw /challenge/pwn
You set the correct permissions!
Round 6 (of 8)!

Current permissions of "/challenge/pwn": -w--wxrw-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
* the group does have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwx-w--wx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g=w,o=wx /challenge/pwn
You set the correct permissions!
Round 7 (of 8)!

Current permissions of "/challenge/pwn": rwx-w--wx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": r-x-w--wx
* the user does have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod +r /flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{UUN8_VeT24IqG-WlUGEmZ-Wlxfx.dNTM5QDL1kzM2czW}
hacker@permissions~permissions-setting-practice:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-7.png)

<br>
<br>
<br>
<br>


# Challenge 9-The SUID Bit
This challenge required us to change permissions to make the file executable with SUIT bit.

## Challenge Description
There are many cases in which non-root users need elevated access to do certain system tasks. The system admin can't be there to give them the password every time a user wanted to do a task that only root/sudoers can do. The "Set User ID" (SUID) permissions bit allows the user to run a program as the owner of that program's file.

This is actually the exact mechanism used to let the challenge programs you run read the flag or, outside of pwn.college, to enable system administration tools such as su, sudo, and so on. The permission of a file with SUID list look like this:
```bash
hacker@dojo:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/sudo
hacker@dojo:~$
```
The s part in place of the executable bit means that the program is executable with SUID. It means that, regardless of what user runs the program (as long as they have executable permissions), the program will execute as the owner user (in this case, the root user).

As the owner of a file, you can set a file's SUID bit by using chmod:

chmod u+s [program]

But be careful! Giving the SUID bit to an executable owned by root can give attackers a possible attack vector to become root. You will learn more about this in the Program Misuse module.

Now, we are going to let you add the SUID bit to the /challenge/getroot program in order to spawn a root shell for you to cat the flag yourself!

## Solution
Changing the /challenge/getroot permissions using chmod u+s.

 ```bash
Connected!                                                                        
hacker@permissions~the-suid-bit:~$ ls -l /challenge/getroot
-rwxr-xr-x 1 root root 155 Jul 12 10:30 /challenge/getroot
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root! 
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{Mca5rEdwOIjHtOM3McljMDxAgJX.dNTM2QDL1kzM2czW}
root@permissions~the-suid-bit:~# 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/o-8.png)

<br>
<br>
<br>
<br>
