# Scrambled RSA

**Flag:** `picoCTF{bad_1d3a5_3525501}`

Approach

- step 1<br>

In this challenge ,when we send a string of characters like 'pic' to the input stream and it shows the encrypted code in scrambled form(eg.first encrypted text for c then p then i).
So we write the script:

```
from pwn import *
import string

r = remote("mercury.picoctf.net", 61477)
r.recvuntil(b"flag: ")
flagre = r.recvline().decode()
r.recvlines(2)

def encrypt(data: str):
    r.sendlineafter(b"I will encrypt whatever you give me: ", data)
    r.recvuntil(b"Here you go: ")
    return r.recvline().decode().strip()

def get_unique_enc(prefix, char, seen):
    enc = encrypt(prefix + char)
    for seene in seen:
        enc = enc.replace(seene, "")
    return enc

known = "picoCTF{"
flag = ""
cipher_map = {}

for char in known:
    enc = get_unique_enc(flag, char, cipher_map)
    assert enc in flagre
    cipher_map[enc] = char
    flag += char
    flagre = enc_flag.replace(enc, "")

chars = "_}" + string.digits + string.ascii_letters

while not flag.endswith("}"):
    for char in chars:
        enc = get_unique_enc(flag, char, cipher_map)
        if enc not in flagre:
            continue
        cipher_map[enc] = char
        flag += char
        flagre = enc_flag.replace(enc, "")
        print(flag)
        break


```

- step 2<br>
How this script works:It starts with a known part of the flag (picoCTF{) and iteratively guesses the remaining characters. 
For each guess, it sends the partial flag to the server, receives the encrypted result, and checks if it matches the expected pattern. 
Checks character by character, the server's encryption is used to confirm each correct character.
The process continues until we get the flag.



![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Cryptography/assets/srsa.png)



What you learned through solving this challenge:
<br>
- We learn about encrypted scrambling and RSA encryption.


Other incorrect methods you tried:
<br>
- Tried sending plaintext to deduce the pattern.


References
<br>
-[Approach](https://ctftime.org/writeup/27362)

