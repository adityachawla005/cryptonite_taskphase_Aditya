# Challenge 1-Listing Processes
This challenge required us to use ps command with -ef to list all processes.

## Challenge Description
First, we will learn to list running processes using the ps command. Depending on whom you ask, ps either stands for "process snapshot" or "process status", and it lists processes. By default, ps just lists the processes running in your terminal, which honestly isn't very useful:
```bash
hacker@dojo:~$ ps
    PID TTY          TIME CMD
    329 pts/0    00:00:00 bash
    349 pts/0    00:00:00 ps
hacker@dojo:~$
```
In the above example, we have the shell (bash) and the ps process itself, and that's all that's running on that specific terminal. We also see that each process has a numerical identifier (the Process ID, or PID), which is a number that uniquely identifies every running process in a Linux environment. We also see the terminal on which the commands are running (in this case, the designation pts/0), and the total amount of cpu time that the process has eaten up so far (since these processes are very undemanding, they have yet to eat up even 1 second!).

In the majority of cases, this is all that you'll see with a default ps. To make it useful, we need to pass a few arguments.

As ps is a very old utility, its usage is a bit of a mess. There are two ways to specify arguments.

"Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.

"BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.

These two methods, ps -ef and ps aux result in slightly different, but cross-recognizable output.

Let's try it in the dojo:
```bash
hacker@dojo:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
hacker         1       0  0 05:34 ?        00:00:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7       1  0 05:34 ?        00:00:00 /bin/sleep 6h
hacker       102       1  1 05:34 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server --auth=none -
hacker       138     102 11 05:34 ?        00:00:07 /usr/lib/code-server/lib/node /usr/lib/code-server/out/node/entr
hacker       287     138  0 05:34 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server/lib/vscode/ou
hacker       318     138  6 05:34 ?        00:00:03 /usr/lib/code-server/lib/node --dns-result-order=ipv4first /usr/
hacker       554     138  3 05:35 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server/lib/vscode/ou
hacker       571     554  0 05:35 pts/0    00:00:00 /usr/bin/bash --init-file /usr/lib/code-server/lib/vscode/out/vs
hacker       695     571  0 05:35 pts/0    00:00:00 ps -ef
hacker@dojo:~$
```
You can see here that there are processes running for the initialization of the challenge environment (docker-init), a timeout before the challenge is automatically terminated to preserve computing resources (sleep 6h to timeout after 6 hours), the VSCode environment (several code-server helper processes), the shell (bash), and my ps -ef command. It's basically the same thing with ps aux:
```bash
hacker@dojo:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
hacker         1  0.0  0.0   1128     4 ?        Ss   05:34   0:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7  0.0  0.0   2736   580 ?        S    05:34   0:00 /bin/sleep 6h
hacker       102  0.4  0.0 723944 64660 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       138  3.3  0.0 968792 106272 ?       Sl   05:34   0:07 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       287  0.0  0.0 717648 53136 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       318  3.3  0.0 977472 98256 ?        Sl   05:34   0:06 /usr/lib/code-server/lib/node --dns-result-order=
hacker       554  0.4  0.0 650560 55360 ?        Rl   05:35   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       571  0.0  0.0   4600  4032 pts/0    Ss   05:35   0:00 /usr/bin/bash --init-file /usr/lib/code-server/li
hacker      1172  0.0  0.0   5892  2924 pts/0    R+   05:38   0:00 ps aux
hacker@dojo:~$
```
There are many commonalities between ps -ef and ps aux: both display the user (USER column), the PID, the TTY, the start time of the process (STIME/START), the total utilized CPU time (TIME), and the command (CMD/COMMAND). ps -ef additionally outputs the Parent Process ID (PPID), which is the PID of the process that launched the one in question, while ps aux outputs the percentage of total system CPU and Memory that the process is utilizing. Plus, there's a bunch of other stuff we won't get into right now.

Anyways! Let's practice. In this level, I have once again renamed /challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory! But I also launched it, so can find it in the running process list, figure out the filename, and relaunch it directly for the flag! Good luck!

NOTE: Both ps -ef and ps aux truncate the command listing to the width of your terminal (which is why the examples above line up so nicely on the right side of the screen. If you can't read the whole path to the process, you might need to enlarge your terminal (or redirect the output somewhere to avoid this truncating behavior)!

## Solution
Using command ps -ef to list processes.

 ```bash
Connected!                                                                        
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 18:45 ?        00:00:00 /sbin/docker-init -- /nix/var/
root           7       1  0 18:45 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 18:45 ?        00:00:00 /challenge/19902-run-6573
root          72      68  0 18:45 ?        00:00:00 sleep 6h
hacker        73       0  0 18:45 pts/0    00:00:00 /run/dojo/bin/ssh-entrypoint
hacker        90      73  0 18:46 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/19902-run-6573
Yahaha, you found me! Here is your flag:
pwn.college{cGfHo6gM9-3N-nd5C_vB9g18C0c.dhzM4QDL1kzM2czW}
Now I will sleep for a while (so that you could find me with 'ps').

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-1.png)

<br>
<br>
<br>
<br>

# Challenge 2-Killing Processes
This challenge required the use of kill command to kill a process. 

## Challenge Description
You've launched processes, you've viewed processes, now you will learn to terminate processes! In Linux, this is done using the aggressively-named kill command. With default options (which is all we'll cover in this level), kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.

Let's say you had a pesky sleep process (sleep is a program that simply hangs out for the number of seconds specified on the commandline, in this case, 1337 seconds) that you launched in another terminal, like so:
```bash
hacker@dojo:~$ sleep 1337
```
How do we get rid of it? You use kill to terminate it by passing the process identifier (the PID from ps) as an argument, like so:
```bash
hacker@dojo:~$ ps -e | grep sleep
 342 pts/0    00:00:00 sleep
hacker@dojo:~$ kill 342
hacker@dojo:~$ ps -e | grep sleep
hacker@dojo:~$
```
Now, it's time to terminate your first process! In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission. Good luck.

## Solution
Using ps -ef and grep to find process PID and further use kill command to kill process.

 ```bash
Connected!                                                                        
hacker@processes~killing-processes:~$ ps -ef | grep dont
hacker        73      71  0 19:00 ?        00:00:00 /challenge/dont_run
hacker        93      75  0 19:00 pts/0    00:00:00 grep --color=auto dont
hacker@processes~killing-processes:~$ kill 74
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{ca6LODUmOKelxL8vq8CMWxpa5Uf.dJDN4QDL1kzM2czW}
hacker@processes~killing-processes:~$ 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-2.png)

<br>
<br>
<br>
<br>

# Challenge 3-Interrupting Processes
This challenge required the use of Ctrl+C to interrupt a process.

## Challenge Description
You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

Try it here! /challenge/run will refuse to give you the flag until you interrupt it. Good luck!

For the very interested, check out this article about terminals and "control codes" (such as Ctrl^C).

## Solution
Using Ctrl^C to interrupt the process.

 ```bash
Connected!                                                                        
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{IQAAnG2EkIFg_FcOjqUXrBBKqc4.dNDN4QDL1kzM2czW}
hacker@processes~interrupting-processes:~$ 
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-3.png)

<br>
<br>
<br>
<br>

# Challenge 4-Suspending Processes
This challenge required the use of Ctrl+Z to suspend a process.

## Challenge Description

You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z. In this level, we'll explore how this works and, in the next level, we'll figure out how to resume those suspended processes!

This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!

## Solution
Using Ctrl^Z to suspend the process and run /challenge/run again.

 ```bash
Connected!                                                                        
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 19:21 pts/0    00:00:00 bash /challenge/run
root          84      82  0 19:21 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root          82      65  0 19:21 pts/0    00:00:00 bash /challenge/run
root          89      65  0 19:21 pts/0    00:00:00 bash /challenge/run
root          91      89  0 19:21 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{856tKhK9QWsqLO5U36NwxJcZWTd.dVDN4QDL1kzM2czW}
hacker@processes~suspending-processes:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-4.png)

<br>
<br>
<br>
<br>

# Challenge 5-Resuming Processes
This challenge required the use of fg command to resume an ongoing process.

## Challenge Description
Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

Go try it out! This challenge's run needs you to suspend it, then resume it. Good luck!

## Solution
UsingCtrl+Z to suspend the program and then fg command to resume the /challenge/run process.

 ```bash
Connected!                                                                        
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{44qmMWjYPg3fj3PJqa1yUqAd6Zl.dZDN4QDL1kzM2czW}
Don't forget to press Enter to quit me!

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-5.png)

<br>
<br>
<br>
<br>

# Challenge 6-Backgrounding Processes
This challenge required the use of bg to resume a background process.

## Challenge Description
You've resumed processes in the foreground with the fg command. You can also resume processes in the background with the bg command! This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

This level's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background!

ARCANUM: If you're interested in some deeper details, check out how to view the differences between suspended and backgrounded properties! Allow me to demonstrate. First, let's suspend a sleep:
```bash
hacker@dojo:~$ sleep 1337
^Z
[1]+  Stopped                 sleep 1337
hacker@dojo:~$
```
The sleep process is now suspended in the background. We can see this with ps by enabling the stat column output with the -o option:
```bash
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 T    sleep 1337
hacker       782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
```
See that T? That means that the process is suspended due to our Ctrl-Z. The S in bash's STAT column means that bash is sleeping while waiting for input. the R in ps's column means that it's actively running, and the + means that it's in the foreground!

Watch what happens when we resume sleep in the background:
```bash
hacker@dojo:~$ bg
[1]+ sleep 1337 &
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 S    sleep 1337
hacker      1224 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$
```
Boom! The sleep now has an S. It's sleeping while, well, sleeping, but it's not suspended! It's also in the background and thus doesn't have the +.

## Solution
Using terminal first launch /challenge/run,suspend and bg command to resume the background porcess while creating another copy of the process.

 ```bash
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S+   bash /challenge/run
root          84 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root          82 S    bash /challenge/run
root          92 S    sleep 6h
root          93 S+   bash /challenge/run
root          95 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{sPFCPDwXVsG5q6UefKvVqaa-4c9.ddDN4QDL1kzM2czW}
hacker@processes~backgrounding-processes:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-8.png)

<br>
<br>
<br>
<br>


# Challenge 7-Foregrounding Processes
This challenge required the use of fg command to resume an ongoing process.

## Challenge Description
Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do? Well, you can foreground a backgrounded process with fg just like you foreground a suspended process! This level will walk you through that!

## Solution
Using /challenge/run to launch it,Ctrl+Z to suspend the program,bg to background it and then fg command to resume the /challenge/run process in the foreground.

 ```bash
  Connected!
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ 
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{E3QIYJu_2OkMDPur1oCviUq_Nf4.dhDN4QDL1kzM2czW}
hacker@processes~foregrounding-processes:~$ 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-7.png)

<br>
<br>
<br>
<br>

# Challenge 8-Starting Background Processes
This challenge required the use of & argument with the command to start a background process.

## Challenge Description
Of course, you don't have to suspend processes to background them: you can start the backgrounded right off the bat! It's easy; all you have to do is append a & to the command, like so:
```bash
hacker@dojo:~$ sleep 1337 &
[1] 1771
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker      1709 Ss   bash
hacker      1771 S    sleep 1337
hacker      1782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
```
Here, sleep is actively running in the background, not suspended. Now it's your turn to practice! Launch /challenge/run backgrounded for the flag!

## Solution
Using /challenge/run & to start a background process.
 ```bash
 Connected!
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 82
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{seGcbJ-JCKk_bbECTJo-Ql47vex.dlDN4QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-8.png)

<br>
<br>
<br>
<br>

# Challenge 9-Process Exit Codes
This challenge required the use of $? to get the exit code of a process.

## Challenge Description
Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates, This can be used by the shell, or the user of the shell (that's you!) to check if the process succeeded in its functionality (this determination, of course, depends on what the process is supposed to do in the first place).

You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value!):
```bash
hacker@dojo:~$ touch test-file
hacker@dojo:~$ echo $?
0
hacker@dojo:~$ touch /test-file
touch: cannot touch '/test-file': Permission denied
hacker@dojo:~$ echo $?
1
hacker@dojo:~$
```
As you can see, commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.

In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument. Good luck!

## Solution
Using /challenge/run and then $? to get the exit code to further invoke /challenge/submit-code with the exit code as an argument.

 ```bash
  Connected!
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
85
hacker@processes~process-exit-codes:~$ /challenge/submit-code 85
CORRECT! Here is your flag:
pwn.college{42pHNBC27B0gbiQxm5hybHGOJ6h.dljN4UDL1kzM2czW}
hacker@processes~process-exit-codes:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Processes%20and%20Jobs/assets/p-9.png)

<br>
<br>
<br>
<br>

