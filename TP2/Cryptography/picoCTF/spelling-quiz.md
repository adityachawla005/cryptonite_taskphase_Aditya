# Spelling quiz

**Flag:** `picoCTF{perhaps_the_dog_jumped_over_was_just_tired} `

Approach

- step 1<br>
We were given the python codeof the encryption scheme.
```
import random
import os

files = [
    os.path.join(path, file)
    for path, dirs, files in os.walk('.')
    for file in files
    if file.split('.')[-1] == 'txt'
]

alphabet = list('abcdefghijklmnopqrstuvwxyz')
random.shuffle(shuffled := alphabet[:])
dictionary = dict(zip(alphabet, shuffled))

for filename in files:
    text = open(filename, 'r').read()
    encrypted = ''.join([
        dictionary[c]
        if c in dictionary else c
        for c in text
    ])
    open(filename, 'w').write(encrypted)
```

- step 2<br>
From this we can observe that the challenge is using a substitution cipher with a random key at every execution.

- step 3<br>
So we open boxentriq cipher identifier to decoode the words given in flag and study guilde files using mono alphabetic substitution cipher.


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Cryptography/assets/spq.png)



What you learned through solving this challenge:
<br>
- In mono alphabetic substitution cipher,every letter is replaced by a corresponding encrypted letter.


Other incorrect methods you tried:
<br>
- Tried wiriting a script for frequency analysis of letters.


References
<br>
-none
