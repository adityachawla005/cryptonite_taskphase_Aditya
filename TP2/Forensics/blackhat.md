# Not Supported

**Flag:** `BHflagY{d22a3eed050c23c0880cc912368905c9d2527a41c328f81ef115b9464b800f7425333edb71d57b440b94dc766a2d49611d46968477b09dfa1f246585d87d7b5a}`

Approach

- step 1<br>
We are searching for notepad process:-
python3 vol.py -f memdump.mem windows.pslist.PsList


- step 2<br>
We make an out directory and dump the PID Notepad proces 6028 using memmap

python3 vol.py -c config.json -f memdump.mem -o out windows.memmap.Memmap --pid 6028 --dump
Then we use string stool to find the flag which is of format BHflagY{}


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Forensics/assets/note.png)


What you learned through solving this challenge:
<br>
- About volatility,pslist and psinfo process finding.



<br>
<br>


# usb100

**Flag:** `BHflagy{1d3cbfa0e052b1729a00950e9fc0f61a3f393bc97c0c74c8ecab1b58cd0f95c32e4c970bdfa6e23371d50680ca0c37f61f7206974d20d5cbb2f00151f4735dde}`

Approach

- step 1<br>
We have to recover usb traffic from send.pcap.I found an article on how data could be recovered from URB_BULK_OUT packets.

- step 1<br>
Now we have to sort the packets according to length.Some of them were images except one binary file which I executed using wine and got the flag.

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Forensics/assets/size.png)
<br>
![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Forensics/assets/bin.png)


References
<br>
- ![Usb pcap](https://shankaraman.wordpress.com/tag/extract-files-from-pcap-usb-protocol/)

<br>
<br>


