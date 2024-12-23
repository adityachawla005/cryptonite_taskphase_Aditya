# vault-door-5

**Flag:** ` picoCTF{c0nv3rt1ng_fr0m_ba5e_64_84fd5095}`

Approach

- step 1<br>
We have been the given the script of the flag characters URL encoded using Java's inbuild URL encoder and further it is encoded using Base64 Encoding.

```
import java.net.URLDecoder;
import java.util.*;

class VaultDoor5 {
    public static void main(String args[]) {
        VaultDoor5 vaultDoor = new VaultDoor5();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1";
        return base64Encoded.equals(expected);
    }
}
```

- step 2<br>
The following script can be written to decode the characters of the flag.

```
import java.util.Base64;
import java.net.URLDecoder;

public class DecodePassword {
    public static void main(String[] args) throws Exception {
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTM4JTM0JTY2JTY0JTM1JTMwJTM5JTM1";
        
        byte[] base64Decoded = Base64.getDecoder().decode(expected);
        String urlEncoded = new String(base64Decoded);

        String password = URLDecoder.decode(urlEncoded, "UTF-8");
        
        System.out.println("Password: picoCTF{" + password + "}");
    }
}

```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/picoCTF/assets/door4.png)



What you learned through solving this challenge:
<br>
- I learned about Java's inbuilt libraries URL encoder and Base 64 Encoder.


Other incorrect methods you tried:
<br>
- none

References:
<br>
- [URL Encoder](https://stackoverflow.com/questions/10786042/java-url-encoding-of-query-string-parameters)

