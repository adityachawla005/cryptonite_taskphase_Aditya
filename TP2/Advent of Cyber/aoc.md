# Day 5	

**Flag:** `THM{Brut3f0rc1n6_mY_w4y}
THM{m4y0r_m4lw4r3_b4ckd00rs}`

Approach

- step 1<br>
We can use Burp Suite to change the XML data in the request:
Right-click on the wishlist.php request in the HTTP history tab and select Send to Repeater.
In the Repeater tab, we can change the XML data in the request to the payload :


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Advent%20of%Cyber/xml.png) 

- step 2<br>
We can see the flag at 15th wish by giving entity as www/var/html/wish_15.txt.
Also,We look at the http://<IP>/CHANGELOG file to see the flag. The contents of the file are:

```
commit 3f786850e387550fdab836ed7e6dc881de23001b (HEAD -> master, origin/master, origin/HEAD)
Author: Mayor Malware - Wareville <mayor@wareville.org>
Date:   Wed Dec 4 21:24:22 2024 +0200

    Fixed the wishlist.php page THM{m4y0r_m4lw4r3_b4ckd00rs}

commit 89e6c98d92887913cadf06b2adb97f26cde4849b (tag: v1.0.0)
Author: Software - Wareville <software@wareville.org>
Date:   Thu Dec 4 14:45:18 2024 +0200

    Almost done with the wishlists page, needs to handle XML parsing

commit 2b66fd261ee5c6cfc8de7fa466bab600bcfe4f69
Author: Software - Wareville <software@wareville.org>
Date:   Tue Dec 2 15:20:57 2024 +0200

    Finally done with the landing page and initial CSS

commit e983f374794de9c64e3d1c1de1d490c0756eeeff
Author: Software - Wareville <software@wareville.org>
Date:   Tue Dec 2 15:19:33 2024 +0200

    Initial commit 

```
What you learned through solving this challenge:
<br>
- XXE Injection using BurpSuite

<br>
<br>

# Day 23

**Flag:** `the flag was : THM{do_not_GET_CAUGHT}`

Approach

- step 1<br>
We can use Burp Suite to change the XML data in the request:
Right-click on the wishlist.php request in the HTTP history tab and select Send to Repeater.
In the Repeater tab, we can change the XML data in the request to the payload :


- step 2<br>
We are given a hash and a hash-id.py program for the hash.It is SHA-256.
We can crack the password using jack the ripper.

john --format=raw-sha256 --wordlist=wordlist.txt hash.txt

The password comes out to be M4y0rM41w4r3


<br>
- John the Ripper

<br>
<br>
