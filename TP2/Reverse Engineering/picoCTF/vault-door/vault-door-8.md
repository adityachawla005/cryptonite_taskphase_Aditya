# vault-door-8

**Flag:** `picoCTF{s0m3_m0r3_b1t_sh1fTiNg_89eb3994e}`

Approach

- step 1<br>
We are given the following code.
The scrambling involves switching bits at different positions using bit shifting and masking.
The checkPassword method is used to compare the scrambled password to a predefined array.
If the scrambled password matches the expected array, access is granted.
```

import java.util.*;

class VaultDoor8 {

    public static void main(String args[]) {
        Scanner b = new Scanner(System.in); 
        System.out.print("Enter vault password: ");
        String c = b.next(); 
        String f = c.substring(8, c.length() - 1); 
        VaultDoor8 a = new VaultDoor8(); 
        if (a.checkPassword(f)) {
            System.out.println("Access granted.");
        } else {
            System.out.println("Access denied!"); 
        }
    }

    public char[] scramble(String password) {
        char[] a = password.toCharArray();
        for (int b = 0; b < a.length; b++) {
            char c = a[b];
            c = switchBits(c, 1, 2);
            c = switchBits(c, 0, 3);
            c = switchBits(c, 5, 6);
            c = switchBits(c, 4, 7);
            c = switchBits(c, 0, 1);
            c = switchBits(c, 3, 4);
            c = switchBits(c, 2, 5);
            c = switchBits(c, 6, 7);
            a[b] = c;
        }
        return a;
    }

    public char switchBits(char c, int p1, int p2) {
        char mask1 = (char)(1 << p1);
        char mask2 = (char)(1 << p2);
        char bit1 = (char)(c & mask1);
        char bit2 = (char)(c & mask2);
        char rest = (char)(c & ~(mask1 | mask2));
        char shift = (char)(p2 - p1);
        char result = (char)((bit1 << shift) | (bit2 >> shift) | rest);
        return result;
    }

    public boolean checkPassword(String password) {
        char[] scrambled = scramble(password);
        char[] expected = {
            0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4, 
            0xF0, 0x77, 0xA4, 0xD0, 0xC5, 0x77, 0xF4, 0x86, 
            0xD0, 0xA5, 0x45, 0x96, 0x27, 0xB5, 0x77, 0xC2, 
            0xD2, 0x95, 0xA4, 0xF0, 0xD2, 0xD2, 0xC1, 0x95
        };
        return Arrays.equals(scrambled, expected);
    }
}



```

- step 1<br>
The following script can be written to decode the characters of the flag.

```
import java.util.*;


class Solution{
 public static void main(String args[]) {
    char[] expected = {
        0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4, 
        0xF0, 0x77, 0xA4, 0xD0, 0xC5, 0x77, 0xF4, 0x86, 
        0xD0, 0xA5, 0x45, 0x96, 0x27, 0xB5, 0x77, 0xC2, 
        0xD2, 0x95, 0xA4, 0xF0, 0xD2, 0xD2, 0xC1, 0x95
    };
  System.out.println("picoCTF{"+String.valueOf(unscramble(String.valueOf(expecte
 }
 static public char[] unscramble(String input) {
  char[] a = input.toCharArray();
  for (int b = 0; b < a.length; b++) {
   char c = a[b];
   c = switchBits(c, 6, 7);
   c = switchBits(c, 2, 5);
   c = switchBits(c, 3, 4);
   c = switchBits(c, 0, 1);
   c = switchBits(c, 4, 7);
   c = switchBits(c, 5, 6);
   c = switchBits(c, 0, 3);
   c = switchBits(c, 1, 2);
   a[b] = c;
  }
  return a;
 }
 
 static public char switchBits(char c, int p1, int p2) {
  char mask1 = (char)(1 << p1);
  char mask2 = (char)(1 << p2);
  char bit1 = (char)(c & mask1);
  char bit2 = (char)(c & mask2);
  char rest = (char)(c & ~(mask1 | mask2));
  char shift = (char)(p2 - p1);
  char result = (char)((bit1 << shift) | (bit2 >> shift) | rest);
  return result;
 }
}


```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/picoCTF/assets/door8.png)



What you learned through solving this challenge:
<br>
- I learnt about bitmasking and swapping bits.


Other incorrect methods you tried:
<br>
- none

References:
<br>
- [Bit-Masking](https://stackoverflow.com/questions/57280464/bit-mask-in-swapping-bits-algorithm)
