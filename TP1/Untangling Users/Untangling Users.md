# Challenge 1-Becoming root with su
This challenge required the use of providing the password to su for becoming root and getting the flag.

## Challenge Description
In the previous level, you used the /challenge/getroot program to become the root user. Becoming root is a fairly common action that Linux users take, and your typical Linux installation obviously does not have /challenge/getroot. Instead, there are two utilities used for this purposes: su and sudo.

In this challenge, we will cover the older one, su (the switch user command). This is not typically used to elevate to root access anymore, but it is an elegant utility from a more civilized time, and we'll cover it first.

su is a setuid binary:
```bash
hacker@dojo:~$ ls -l /usr/bin/su
-rwsr-xr-x 1 root root 232416 Dec 1 11:45 /usr/bin/su
hacker@dojo:~$
```
Because it has the SUID bit set, su runs as root. Running as root, it can start a root shell! Of course, su is discerning: before allowing the user to elevate privileges to root, it checks to make sure that the user knows the root password:
```bash
hacker@dojo:~$ su
Password: 
su: Authentication failure
hacker@dojo:~$
```
This check against the root password is what obsoletes su. Modern systems very rarely have root passwords, and different mechanisms (that we will learn later) are used to grant administrative access.

But THIS challenge (and only this challenge) does have a root password. That password is hack-the-planet, and you must provide it to su to become root! Go do that, and read the flag!

## Solution

Give the password to su to become root and then cat /flag to read the file.

 ```bash
Connected!
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# ls
COLLEGE               myflag
Desktop               n
Intro_to_commands.md  new
PWN                   not-the-flag
command               tee
command.txt           the-flag
f                     tmp
grep                  zfLOZ95GHq0o5AfjB-mOoDVzz1.dRTM4QDL1kzM2czW}
instructions
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{0VI4WC8EJudP5fQrI93fmytx8Yp.dVTN0UDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Untangling%20Users/assets/u-1.png)

<br>
<br>
<br>
<br>

# Challenge 2-Other users with su
This challenge required the use of providing the password to su for some user and getting the flag.

## Challenge Description
With no arguments, su will start a root shell (after authenticating with root's password). However, you can also give a username as an argument to switch to that user instead of root. For example:
```bash
hacker@dojo:~$ su some-user
Password:
some-user@dojo:~$
```
Awesome! In this level, you must switch to the zardus user and then run /challenge/run. Zardus' password is dont-hack-me. Good luck!

## Solution

Give the password to su to become Zardus and then cat /flag to read the file.

 ```bash
Connected!
shacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{gSaQCqO0185-tZ73VwDXr5hqGyM.dZTN0UDL1kzM2czW}
zardus@users~other-users-with-su:/home/hacker$ 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Untangling%20Users/assets/u-2.png)

<br>
<br>
<br>
<br>

# Challenge 3-Cracking passwords
This challenge required the use of cracking the password using John the Ripper and then becoming zardus by giving the password to get the flag.

## Challenge Description
When you enter a password for su, it compares it against the stored password for that user. These passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords, these were moved to /etc/shadow. Here is the example /etc/shadow from the previous level:

root:$6$s74oZg/4.RnUvwo2$hRmCHZ9rxX56BbjnXcxa0MdOsW2moiW8qcAl/Aoc7NEuXl2DmJXPi3gLp7hmyloQvRhjXJ.wjqJ7PprVKLDtg/:19921:0:99999:7:::<br>
daemon:*:19873:0:99999:7::: <br>
bin:*:19873:0:99999:7:::<br>
sys:*:19873:0:99999:7:::<br>
sync:*:19873:0:99999:7:::<br>
games:*:19873:0:99999:7:::<br>
man:*:19873:0:99999:7:::<br>
lp:*:19873:0:99999:7:::<br>
mail:*:19873:0:99999:7:::<br>
news:*:19873:0:99999:7:::<br>
uucp:*:19873:0:99999:7:::<br>
proxy:*:19873:0:99999:7:::<br>
www-data:*:19873:0:99999:7:::<br>
backup:*:19873:0:99999:7:::<br>
list:*:19873:0:99999:7:::<br>
irc:*:19873:0:99999:7:::<br>
gnats:*:19873:0:99999:7:::<br>
nobody:*:19873:0:99999:7:::<br>
_apt:*:19873:0:99999:7:::<br>
systemd-timesync:*:19901:0:99999:7:::<br>
systemd-network:*:19901:0:99999:7:::<br>
systemd-resolve:*:19901:0:99999:7:::<br>
mysql:!:19901:0:99999:7:::<br>
messagebus:*:19901:0:99999:7:::<br>
sshd:*:19901:0:99999:7:::<br>
hacker::19916:0:99999:7:::<br>
zardus:$6$bEFkpM0w/6J0n979$47ksu/JE5QK6hSeB7mmuvJyY05wVypMhMMnEPTIddNUb5R9KXgNTYRTm75VOu1oRLGLbAql3ylkVa5ExuPov1.:19921:0:99999:7:::

Separated by :s, the first field of each line is the username and the second is the password. A value of * or ! functionally means that password login for the account is disabled, a blank field means that there is no password (a not-uncommon misconfiguration that allows password-less su in some configurations), and the long string such as Zardus' $6$bEFkpM0w/6J0n979$47ksu/JE5QK6hSeB7mmuvJyY05wVypMhMMnEPTIddNUb5R9KXgNTYRTm75VOu1oRLGLbAql3ylkVa5ExuPov1. is the result of one-way-encrypting (hashing) Zardus' password from the last level (in this case, dont-hack-me). Other fields in this file have other meanings, and you can read more about them here.

When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value. If the result matches, su grants you access to the user!

But what if you don't know the password? If you have the hashed value of the password, you can crack it! Even though /etc/shadow is, by default, only readable by root, leaks can happen! For example, backups are often stored, unencrypted and insufficiently protected, on file servers, and this has led to countless data disclosures.

If a hacker gets their hands on a leaked /etc/shadow, they can start cracking passwords and wreaking havoc. The cracking can be done via the famous John the Ripper, as so:
```bash
hacker@dojo:~$ john ./my-leaked-shadow-file
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Will run 32 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
password1337      (zardus)
1g 0:00:00:22 3/3 0.04528g/s 10509p/s 10509c/s 10509C/s lykys..lank
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@dojo:~$
```
Here, John the Ripper cracked Zardus' leaked password hash to find the real value of password1337. Poor Zardus!

This level simulates this story, giving you a leak of /etc/shadow (in /challenge/shadow-leak). Crack it (this could take a few minutes), su to zardus, and run /challenge/run to get the flag!

## Solution

Run the John the Ripper command along with /challenge/shadow-leak to get the password for zardus.Give the command su zardus and put the password to invoke the /challenge/run program to get the flag.

 ```bash
Connected!
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04798g/s 279.4p/s 279.4c/s 279.4C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su
WARNING: you are invoking 'su' without specifying a user. This will default to 
the 'root' user, which is not achievable in this challenge.
Password: 
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{oC3_js5qVGm5Qz-nQkZlLMlwK0R.ddTN0UDL1kzM2czW}
zardus@users~cracking-passwords:/home/hacker$ 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Untangling%20Users/assets/u-3.png)

<br>
<br>
<br>
<br>


# Challenge 4-Using sudo
This challenge required us to invoke sudo command to run a process with root access. 

## Challenge Description
In the olden days, a typical Linux system had a root password that administrators would use to su to root (after logging into their account with their normal account password). But root passwords are a pain to maintain, they (or their hashes!) can leak, and they don't lend themselves well to larger environments (e.g., fleets of servers). To address this, in recent decades, the world has moved from administration via su to administration via sudo (superuser do).

Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root:
```bash
hacker@dojo:~$ whoami
hacker
hacker@dojo:~$ sudo whoami
root
hacker@dojo:~$
```
Or, more relevant to getting flags:
```bash
hacker@dojo:~$ grep hacker /etc/shadow
grep: /etc/shadow: Permission denied
hacker@dojo:~$ sudo grep hacker /etc/shadow
hacker:$6$Xro.e7qB3Q2Jl2sA$j6xffIgWn9xIxWUeFzvwPf.nOH2NTWNJCU5XVkPuONjIC7jL467SR4bXjpVJx4b/bkbl7kyhNquWtkNlulFoy.:19921:0:99999:7:::
hacker@dojo:~$
```
Also unlike su, rather than authenticating via password, sudo relies on policies that it checks to determine the user's authorization run things as root. These policies are defined in /etc/sudoers, and though it's mostly out of scale for our purposes, there are plenty of resources for learning about this!

So, the world has moved to sudo and has (for the purposes of system administration) left su behind. In fact, even pwn.college's Practice Mode works by giving you sudo access to elevate privileges!

In this level, we will give you sudo access, and you will use it to read the flag. Nice and easy!

NOTE: After this level, we will enable Practice Mode! When you launch a challenge in Practice Mode (by clicking the Practice button instead of the Start button), the resulting container will give you full sudo access to allow you to introspect and debug to your heart's content, but of course with a placeholder flag.

## Solution
```bash

Connected!
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{kxV-I_lG1LC7E3OjVFz30kKppnO.dhTN0UDL1kzM2czW}
```



<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Untangling%20Users/assets/u-4.png)

<br>
<br>
<br>
<br>
