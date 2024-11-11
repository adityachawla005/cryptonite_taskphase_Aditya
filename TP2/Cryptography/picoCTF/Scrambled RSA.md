# Scrambled RSA

**Flag:** `picoCTF{bad_1d3a5_3525501} `

Approach

- step 1<br>
We make use of an oracle based decryption system.So we write a python script to interact with the server.

```
from pwn import *
import string

remote_service = remote("mercury.picoctf.net", 61477)

remote_service.recvuntil(b"flag: ")
encrypted_flag = remote_service.recvline().decode()

remote_service.recvline()
remote_service.recvline()

def get_encrypted_data(input_str: str):
    remote_service.sendlineafter(b"I will encrypt whatever you give me: ", input_str)
    remote_service.recvuntil(b"Here you go: ")
    return remote_service.recvline().decode().strip()

def get_cipher_representation(prefix: str, character: str, seen_data: dict):
    encrypted = get_encrypted_data(prefix + character)
    for prev_encrypted in seen_data.keys():
        encrypted = encrypted.replace(prev_encrypted, "")
    return encrypted

known_prefix = "picoCTF{"
current_flag = ""
cipher_dict = {}

for character in known_prefix:
    encrypted_version = get_cipher_representation(current_flag, character, cipher_dict)
    assert encrypted_version in encrypted_flag
    cipher_dict[encrypted_version] = character
    current_flag += character
    encrypted_flag = encrypted_flag.replace(encrypted_version, "")

possible_characters = "_}" + string.digits + string.ascii_lowercase + string.ascii_uppercase

while not current_flag.endswith("}"):
    for character in possible_characters:
        encrypted_version = get_cipher_representation(current_flag, character, cipher_dict)
        if encrypted_version not in encrypted_flag:
            continue
        cipher_dict[encrypted_version] = character
        current_flag += character
        encrypted_flag = encrypted_flag.replace(encrypted_version, "")
        print(current_flag)
        break

```

- step 2<br>
How this script works:It starts with a known part of the flag (picoCTF{) and iteratively guesses the remaining characters. 
For each guess, it sends the partial flag to the server, receives the encrypted result, and checks if it matches the expected pattern. 
By gradually building the flag character by character, it uses the server's encryption as a clue to confirm each correct character.
 The process continues until the entire flag is reconstructed.



![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Cryptography/assets/srsa.png)



What you learned through solving this challenge:
<br>
- In this challenge ,we send a string of characters like 'pic' to the input stream and it shows the encrypted code in scrambled form(eg.first encrypted text for c then p then i).


Other incorrect methods you tried:
<br>
- Tried sending plaintext 'picoCTF'to deduce the pattern.


References
<br>
-[Approach](https://ctftime.org/writeup/27362)

