# Not Just usbpcap 

**Flag:** ``

Approach

- step 1<br>
We can notice several uSB and Bluetooth traffic.
i tried extracting keyboard key presses.
The source was Google pixel buds A series.
Take a look at USB conversations, we can see that most of the traffic is related to device 9 and 10.there is USB HID protocol in the protocol hierarchy statistics,
 so these two device may be HID device.
and I found this source on HID devices.


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Forensics/assets/hie.png)

References

- ![Source on HID](https://www.usb.org/document-library/device-class-definition-hid-111)

<br>
<br>



