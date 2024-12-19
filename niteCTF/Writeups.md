# Mumbo-Dumbo

**Flag:** `nite{quICklY_grab_the_codE5_sgOqkA}`

# About
In this challenge, a cryptographic mechanism guarded the "Key," which was protected by a complex Proof-of-Work (PoW) system. The Keeper, as described, relentlessly enforced the PoW verification process. My goal was to bypass this defense by solving the challenge and uncovering the secret.

# Approach

- step 1<br>
The challenge gives us a python file implementing a PoW system using cryptographic and mathematical operations.
1.Modular square roots using Sloth functions.
2.Base64 encoding/decoding to handle large numbers.
3.Reverse verification logic via modular squaring.

We solve the challenge first:

```bash
ncat --ssl mumbo-dumbo.chals.nitectf2024.live 1337
== proof-of-work: enabled ==
Please solve the proof-of-work challenge first:

python3 pow.py solve s.ACcQ.AAAWkREI491AwrxolvsuRA3d

Solution: s.AAAwBKzUDVeVZV6T548pijZy/mdB+YG+HGe1EmsMw4CZpUdB/qgiMa21SGDaqrczxtc+dNRUUd9fD10NkHKEeW1Kj/JjF6h/SwLOxvvKx/Il/OY9YCPoHYDsNbgjmslagj9F8qEYpIhRljxKrbfdQOqpuI1NKR3lwlG9CtYygJMtvPbIVWrxYeQLerTfOHLtFSDMm/Bw96ZrvMyw3ePLXwwq
```

- step 2<br>
We have to engage the AI(keeper) in a conversation to get the flag.


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/niteCTF/assets/end.png)

<br>
<br>
<br>


# RSAabc

**Flag:** `nite{C@TCHME!FY0UCAN}`

# About
The task was to break the encryption and retrieve the hidden flag.

The provided files for the challenge were:

    cipher.py: A Python script implementing the encryption.
    out.txt: A file containing the encrypted message.

# Approach

- step 1<br>
the algorithm performed differently based on whether the ascii of character in flag.txt is prime or not.

##if was not prime
reversed and written in out.txt
rsa was implemented on its ascii and its ct and n values were written

##if prime
converted to greek
rsa was done on it
googly function was done

3 different files to handle the greek output,cipher and modulus.txt.


- step 2<br>
Removed these english letters these were the letters which are not prime also remove indices of these not prime vlaues from ct and n values also note the indices.

```python
import json

# Read the greek.txt file and identify English letters
with open('greek.txt', 'r') as f:
    greek_text = f.read()

# Initialize an empty list to store indices of English letters
english_indices = []

# Loop through the greek text and find English letters
for index, char in enumerate(greek_text):
    if char.isalpha() and not char.isascii():  # Only English letters
        english_indices.append(index)

# Write the indices of English letters to index.txt
with open('index.txt', 'w') as f:
    for index in english_indices:
        f.write(str(index) + '\n')

# Read the cipher.txt and modulus.txt (JSON arrays)
with open('cipher.txt', 'r') as f:
    cipher_numbers = json.load(f)

with open('modulus.txt', 'r') as f:
    modulus_numbers = json.load(f)

# Remove elements in cipher_numbers and modulus_numbers at the indices in index.txt
for idx in sorted(english_indices, reverse=True):  # Remove from the end to avoid index shifting
    if idx < len(cipher_numbers):
        del cipher_numbers[idx]
    if idx < len(modulus_numbers):
        del modulus_numbers[idx]

# Write the updated arrays back to cipher.txt and modulus.txt
with open('cipher.txt', 'w') as f:
    json.dump(cipher_numbers, f)

with open('modulus.txt', 'w') as f:
    json.dump(modulus_numbers, f)

print("Process complete!")
```
- step 3<br>
Performed reverse operation on them and got half the flag.

- step 4<br>
I have the greek letters of prime characters convert them to english.

```python
# Define the original Greek-to-English mapping
language = {
    'A': 'Α', 'a': 'α',
    'B': 'Β', 'b': 'β',
    'C': 'Σ', 'c': 'σ',
    'D': 'Δ', 'd': 'δ',
    'E': 'Ε', 'e': 'ε',
    'F': 'Φ', 'f': 'φ',
    'G': 'Γ', 'g': 'γ',
    'H': 'Η', 'h': 'η',
    'I': 'Ι', 'i': 'ι',
    'J': 'Ξ', 'j': 'ξ',
    'K': 'Κ', 'k': 'κ',
    'L': 'Λ', 'l': 'λ',
    'M': 'Μ', 'm': 'μ',
    'N': 'Ν', 'n': 'ν',
    'O': 'Ο', 'o': 'ο',
    'P': 'Π', 'p': 'π',
    'Q': 'Θ', 'q': 'θ',
    'R': 'Ρ', 'r': 'ρ',
    'S': 'Σ', 's': 'ς',  
    'T': 'Τ', 't': 'τ',
    'U': 'Υ', 'u': 'υ',
    'V': 'Ω', 'v': 'ω',
    'W': 'Ψ', 'w': 'ψ',
    'X': 'Χ', 'x': 'χ',
    'Y': 'Υ', 'y': 'υ',
    'Z': 'Ζ', 'z': 'ζ'
}

# Reverse the dictionary to map Greek letters back to English
reverse_language = {v: k for k, v in language.items()}

# Open the Greek text file and read its contents
with open("greek.txt", "r", encoding="utf-8") as greek_file:
    greek_text = greek_file.read()

# Convert Greek text back to English
english_text = ''.join([reverse_language.get(char, char) for char in greek_text])

# Write the English text to a new file
with open("english.txt", "w", encoding="utf-8") as english_file:
    english_file.write(english_text)

print("Conversion complete! Check 'english.txt' for the result.")
```
```python
import json

# Load the ciphertext from the cipher.txt file
with open("updated_cipher.txt", "r") as cipher_file:
    cipher_content = cipher_file.read()

# Load the ciphertext list (which should be a JSON array)
try:
    ciphertext_list = json.loads(cipher_content)
except json.JSONDecodeError as e:
    print(f"Error loading JSON: {e}")

# Load the corresponding English characters from english.txt
with open("english.txt", "r") as eng_file:
    eng_content = eng_file.read().strip()

# Check that the lengths match
if len(ciphertext_list) != len(eng_content):
    print("Error: The number of ciphertext entries does not match the number of English characters!")
else:
    # Create a reverse mapping for the googly function
    def reverse_googly(number, position):
        mask = 1 << position
        return number ^ mask

    # Recover the original ciphertext and characters
    recovered_message = []

    for i in range(len(ciphertext_list)):
        # Get the ciphertext number and the corresponding English character
        cipher_text = ciphertext_list[i]  # Get each ciphertext number from the list
        eng = eng_content[i]  # Get the corresponding English character from the string

        # Ensure the character is valid before proceeding
        if len(eng) == 1:  # Only process valid single characters
            # Calculate the original ciphertext before the googly function was applied
            # Determine the bit length and the corresponding position from the character
            original_ciphertext = reverse_googly(cipher_text, cipher_text.bit_length() - ord(eng))

            # Now, handle upper or lower case based on the original character
            if eng.isupper():
                original_char = chr(65 + original_ciphertext % 26)  # Uppercase letter
            else:  # Lowercase letter
                original_char = chr(97 + original_ciphertext % 26)

            recovered_message.append(original_char)  # Append the recovered original character

    # Join the recovered characters to form the message
    recovered_text = ''.join(recovered_message)
    print("Recovered Message: ", recovered_text)
```
- step 5<br>
Now we have to reverse the googly function.

- step 6<br>
I have the final ciphertext and the lan values these are enough to reverse the xor

- step 7<br>
Now we perform reverse RSA to get the message.

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/niteCTF/assets/algo.png)

<br>
<br>
<br>


# freakada 3301

**Flag:** `nite{4_wannabe_1ntern3t_myst3ry}`

# About
This was an Miscellaneous OSINT challenge centered arount ci- you know what I mean.

# Approach

- step 1<br>
We were given an image.After extracting metadata we get the following encrypted text.

```
ZIT HQZI OL GWLEXKTR, WXZ ZIT ZKXZI SOTL OF ZIT LIQRGVL. LTTA ZIT HQZZTKFL. QDGFU ZIT EIQGL, Q WTQEGF QVQOZL: izzhl://woz.sn/yktqatlztof0. GFSN ZIT VGKZIN VOSS LTT ZIT XFLTTF. ZIT PGXKFTN IQL PXLZ WTUXF
```
Deciphering the monoalphabetic substitution cipher, we get a link HTTPS://BIT.LY/FREAKESTEIN0, which leads us to a proton drive page and gives us a ducky.jpg image.


- step 2<br>
By hexdumping the ducky image we get a github link.

- step 3<br>
In this  profiile, there lies a repo Salvation-in-Decay.
In there, lie 3 files, one README which seems to contain the second part of the flag1sk3vr3d_qw5yvvc}. The other two files Code of decay and Whispers of the forgotten which contained some alien language.
Coincidentially, to our surprise, this thing was actually called ALIEN LANGUAGE! The texts in the fiie translated to WE WERE HERE and SOMEHOW FORGOTTEN.  It turns out, it was hinting us towards checking the history of the commits. As there were 6 commits in the the repo, we checked them out to find two things.

- step 4<br>
In the commits we found 
1.A poem
2.A list of colon separated numbers.
We tried matching the numbers as the line:word:character number and we get a link to a discord server.
discord.gg/AHj7R2Qd

- step 5<br>
The discord had a voice channel playing "Thick of it"(from the screen-)
Moving on, we found a freaky bot named freakada. We started talking to it, gave it all sorts of stuff, to receive Incorrect. But freakada was aking for its prime, so we tried 3301 and voila it gave us another task.

- step 6<br>
multiply 3 certain primes, `3301 * x * y`.
Where, `x` and `y` are integral part of the original image.
Obviously x and y where the number representing image size of the freakada image. So we did the math and put in 745520947.

- step 7<br>
13.34508015959565, 74.79629600750295 - these coordinates led us to the infamously famous FREAKY BACKSHOTS CLIFF. The reviews had images with a QR code which led us to a voice message.

We drew out the spectrogram of the audio to get the first part of the flag.
nite{4_wannabe_

- step 8<br>
We tried Vignere cipher. It came to us suddenly to type freakey as the key cuz it sounded smart and possible. We did so and voila. The second part of the flag was 1ntern3t_myst3ry}.


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/niteCTF/assets/spectro.png)

<br>
<br>
<br>


# La-Casa-De-Papel

**Flag:** `nite{El_Pr0f3_0f_Prec1s10n_Pl4ns}`

# About
We were provided with an access to the web server and the python code the challenge is based on.
I look into the code and its just a use of Base64 encoding and decoding.

# Approach

- step 1<br>
Accessing the function practice_convo(secret), we can see that it encodes your message into hash and then into Base64.

- step 2<br>
Taking a look at the function fool_alice(secret), we can see that we have to type in Bob as an input to Your name: and to Enter your HMAC: , we have to enter the decoded Base64 of Bob. This gives us the key for the vault G0t_Th3_G0ld_B3rl1nale.
Then we enter the vault key into crack_the_vault(), and boom there is our flag right in front of us.

<br>
<br>
<br>

# Beyond A Display

**Flag:** `nite{Hyundai,Shankar_Ehsaan_Loy,KTPO}`

# About
In this OSINT challenge,we were given a google street image of a metro station.


# Approach

- step 1<br>
We try to find a metro station painted red.We track it to Belvedere Towers in Gurgaon.

- step 2<br>
The description says I saw a shopping complex in the vicinity. If you move a bit forward in the map, you'll see the DLF Cyberhub shopping complex.

- step 3<br>
Hundai's first 4D billboard for Hyundai Spotlight event featuring the band Shankar Ehsaan Loy.The venue is KTPO.


<br>
<br>
<br>

# Glitch Please

**Flag:** `nite{4_R34L_0DD84LL}`

# About
In this challenge,we have to detect the suspicious players using an Ai outliers model.

# Approach

- step 1<br>
Initially, I created a basic AI model to identify outliers by analyzing numerical features such as:
1.ItemsCollected
2.ConnectionPing
3.PlayerScore
Other performance metrics like K/D Ratio and Efficiency

- step 2<br>
I filtered the dataset to identify rows where the pixel array had 65,536 elements.

```python
import pandas as pd
import ast
from tqdm import tqdm

# Load the dataset
file_name = "datasetALLALONE.csv"
df = pd.read_csv(file_name)

# Initialize a list to store rows
players_data = []

# Check ProfilePic size
for index, row in tqdm(df.iterrows(), total=df.shape[0], desc="Processing Profile Pics"):
    try:
        profile_pic_array = ast.literal_eval(row['ProfilePic (256x256)'])
        if len(profile_pic_array) == 256 * 256:
            players_data.append(row)
    except Exception as e:
        print(f"Error at index {index}: {e}")

# Convert to DataFrame
players_df = pd.DataFrame(players_data)
players_df.to_csv("flattened_players_65536.csv", index=False)
print("Filtered players saved to flattened_players_65536.csv")
```
- step 3<br>
With the filtered players’ pixel arrays, I generated images using Python libraries like PIL (Python Imaging Library) and NumPy and made its picture.

- step 4<br>
To sort the images based on player scores for better visualization.


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/niteCTF/assets/c.png)

<br>
<br>
<br>

# Farewell Firewall

**Flag:** ``

# About
It alludes to concepts of anomaly detection using DBSCAN, balance, and interplay of opposing forces.

# Approach

- step 1<br>
The story begins with "visualizing the exact locations of counterpart villages, mapping their positions with precision."
This correlates to clustering the latitude and longitude coordinates using DBSCAN.
DBSCAN identifies dense regions of data points (villages) and flags anomalies (outliers) as isolated, hidden from the main clusters.
These outliers represent "hidden villages" or tampered entries in the dataset.

By mapping outliers, we reveal points where manipulation occurred—this sets the stage for uncovering the hidden information.

```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import DBSCAN
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('Network_Log.csv')

# Extract the latitude and longitude columns
coordinates = df[['latitude_coord', 'longitude_coord']]

# Optional: Standardize the data (important for DBSCAN)
scaler = StandardScaler()
coordinates_scaled = scaler.fit_transform(coordinates)

# Apply DBSCAN
dbscan = DBSCAN(eps=0.1, min_samples=6)  # You can adjust eps and min_samples based on your data
df['outlier'] = dbscan.fit_predict(coordinates_scaled)

# 'outlier' column: -1 means an outlier, other values indicate cluster labels
outliers = df[df['outlier'] == -1]

# Save outliers to a new CSV file
outliers.to_csv('outliers.csv', index=False)

# Print outliers
print(f"Number of outliers: {len(outliers)}")
print(outliers)

# Plot the results
plt.scatter(df['latitude_coord'], df['longitude_coord'], c=df['outlier'], cmap='coolwarm', marker='o')
plt.title('Outlier Detection using DBSCAN')
plt.xlabel('Latitude')
plt.ylabel('Longitude')
plt.show()

```

- step 2<br>
The use of the XOR operation symbolizes the "interplay of opposing forces" where two binary or numerical values interact to produce a new result.This is the yin part.

- step 3<br>
XOR produces a numeric result, which, when converted to its ASCII representation, unveils readable characters.

step 4<br>
Sorting by user id.
I tried to filter this data out by removing ascii out of range and removed the special charactars so got the flag wrong


<br>
<br>
<br>

# You are T detective

**Flag:** `nite{n0n_std_b4ud_r4t3s_ftw}`


# Approach

- step 1<br>
Open the file: Load the provided signal file in a logic analyzer software, such as Sigrok.

- step 2<br>
Identify the smallest bit: Carefully examine the signal to locate the smallest bit, which corresponds to the narrowest pulse in the data stream.

- step 3<br>
Measure the time duration: Find the exact time taken by that smallest bit. Most logic analyzers will allow you to zoom in and measure this duration accurately.

- step 4<br>
Calculate the custom baud rate: Take the reciprocal of the measured time (1/time). This result will give you the custom baud rate used in the signal.


<br>
<br>
<br>


# BackTrack

**Flag:** `nite{17:00_20February}`

# About
Kenji is a nice guy who lives in Tokyo. He is in a dilemma. In 2017, he was late to an important meeting and is now facing repercussions. To defend himself, he needs to prove that it was not his fault. His evidence? The train he boarded that day, traveling between Omotesandō and Suitengumae, was delayed. However, his boss is not providing the specific details of the accusation. Kenji vividly remembers one key fact: the train was around 61 minutes late.

# Approach

- step 1<br>
We can find out the line  between these two stations.

- step 2<br>
 We see a tab called Delay Certificate, and navigate to the Hanzomon line. 
To got back to 2017 we can use WayBack Machine Archive as the question name suggests BackTrack.

- step 3<br>
we go to each snapshot and search for 61, we can find it in the snapshot of March 26th, 2017.
We find the entry of 20th February.


<br>
<br>
<br>

