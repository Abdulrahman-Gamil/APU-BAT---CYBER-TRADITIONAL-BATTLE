### The APU servers have been compromised, resulting in all files being locked with an unknown encryption method. One of our students Wala was tasked with investigating the attack to find a way to recover the critical data. During the investigation, Wala discovered that while most files were encrypted, one Java code file remained intact. Additionally, Wala managed to capture memory dump data, leading to the discovery of a mysterious file that couldn't be opened. At this point, your mission is to delve deeper into the investigation. Your objectives are to understand the significance of the unencrypted Java file and to uncover the contents of the mysterious file that initially appeared inaccessible and find out the output the code.

![image](https://github.com/user-attachments/assets/6df571e3-e8eb-4ce0-81de-2b89ffc9c2ca)

The challenge given two file a java file and .hprof file is a ‎binary format file that contains heap dump information for a ‎Java process. It is typically generated when a Java application ‎crashes or when the jmap utility is used to capture the heap ‎state of a running Java application. This file captures the ‎memory state of the Java application at a specific point in ‎time, including details like object references, class ‎information, and the amount of memory used by different ‎objects.‎

Usage:‎
	‎-‎ Memory Analysis.‎
	‎- Debugging.‎

![image](https://github.com/user-attachments/assets/53376410-a49f-47d3-a0bf-5555383eb002)

This Java code is a decryption utility that decrypts an ‎encrypted string using the AES (Advanced Encryption ‎Standard) algorithm in CBC (Cipher Block Chaining) mode ‎with PKCS5 padding. Let’s break down each part of the code ‎to understand how it works‏.‏

## ‎1‎‏. ‏main Method
```
public static void main(String[] args) throws InterruptedException {
    String encryptedSecret = "fc3f4a4110356538528a3e29e60750d95135fd78919550401e38afa407b...";

    try {
        String decryptedPassword = decrypt(encryptedSecret, Key, ivHex);
        
        // Output the results
        System.out.println("...........................................................................................................");
        System.out.println("Decrypted Password: " + decryptedPassword);
    } catch (Exception e) {
        System.out.println("Decryption failed: " + e.getMessage());
    }

    Thread.sleep(5000);
}
```

- encryptedSecret: This string contains the encrypted data that ‎needs to be decrypted‏.‏

- decrypt method: This method is called to perform the ‎decryption. It takes three parameters: the encrypted data, the ‎secret key (Key), and the initialization vector (ivHex)‎‏.‏

- try-catch block: If the decryption is successful, the decrypted ‎password is printed. If there is an exception during ‎decryption, an error message is printed‏.‏

- Thread.sleep(5000): This line pauses the execution of the ‎program for 5 seconds‏.‏


## 2 .decrypt Method

```
public static String decrypt(String encryptedHex, String hexKey, String ivHex) throws Exception {
    byte[] keyBytes = hexStringToByteArray(hexKey);
    byte[] ivBytes = hexStringToByteArray(ivHex);

    Cipher cipher = Cipher.getInstance("AES/CBC/PKCS5Padding");
    SecretKeySpec keySpec = new SecretKeySpec(keyBytes, "AES");
    IvParameterSpec ivSpec = new IvParameterSpec(ivBytes);
    cipher.init(Cipher.DECRYPT_MODE, keySpec, ivSpec);

    byte[] encryptedBytes = hexStringToByteArray(encryptedHex);
    byte[] decryptedBytes = cipher.doFinal(encryptedBytes);

    return new String(decryptedBytes);
}

```
  
  - hexStringToByteArray: Converts the hexadecimal string ‎‎(hexKey and ivHex) into a byte array‎‏.‏
  - Cipher cipher = ‎Cipher.getInstance("AES/CBC/PKCS5Padding");: Creates a ‎Cipher instance that uses the AES algorithm in CBC mode ‎with PKCS5 padding‏.‏
  -  SecretKeySpec keySpec: The secret key is created from the ‎provided key bytes‏.‏
  -  IvParameterSpec ivSpec: The initialization vector (IV) is ‎created from the provided IV bytes‏.‏
  -  cipher.init(Cipher.DECRYPT_MODE, keySpec, ivSpec);: ‎Initializes the Cipher in decryption mode with the key and IV‏.‏
  -  cipher.doFinal: Performs the actual decryption operation on ‎the encrypted bytes‏.‏

## ‎3‎‏. ‏hexStringToByteArray Method

```
public static byte[] hexStringToByteArray(String s) {
    int len = s.length();
    byte[] data = new byte[len / 2];
    for (int i = 0; i < len; i += 2) {
        // Convert each pair of hex characters to a byte
        data[i / 2] = (byte) ((Character.digit(s.charAt(i), 16) << 4) + 
                             Character.digit(s.charAt(i + 1), 16));
    }
    return data; 
}

```

  - Purpose: Converts a hexadecimal string to a byte array‏.‏
  - Character.digit(s.charAt(i), 16): Converts each character from ‎the hexadecimal string to its corresponding integer value‏.‏

Key Points‏:‏

  - Encryption Algorithm: The code uses AES with CBC mode ‎and PKCS5 padding for encryption and decryption‏.‏
  - Initialization Vector (IV): IV is crucial in CBC mode as it ‎adds randomness to the encryption process. Without the ‎correct IV, decryption will fail‏.‏
  - Secret Key: The secret key is also necessary for both ‎encryption and decryption‏.‏
  
Final Note‏:‏
In order to decrypt the string (flag) using the AES algorithm, ‎both the Initialization Vector (IV) and the Private Key are ‎required. The IV ensures that the encryption process is secure ‎by adding randomness, and the private key is used to unlock ‎the encrypted data


![image](https://github.com/user-attachments/assets/3e3d6b8f-e599-430b-b03f-44768bdec147)

How to Open a .hprof File:‎

You can open and analyze a .hprof file using VisualVM, a tool ‎that provides a visual interface for monitoring and ‎troubleshooting Java applications. After downloading and ‎installing VisualVM, you can load the .hprof file to explore ‎the heap dump and identify any potential issues with your ‎Java application.‎
By analyzing the .hprof file, it may be possible to discover ‎sensitive information such as the Initialization Vector (IV) ‎and the private key, if they were stored in memory at the time ‎the heap dump was taken. This can be crucial for decrypting ‎data encrypted with the AES algorithm, as both the IV and the ‎private key are necessary for successful decryption.‎


a summary of the heap dump in VisualVM:‎

	‎•‎	Heap Size: Shows the total memory size used.‎
	‎•‎	Instances: Number of objects in memory.‎
	‎•‎	Classes: Number of unique classes.‎
	‎•‎	Environment: Details like system architecture, Java ‎version, etc.‎
	‎•‎	Classes by Number of Instances: Lists the classes ‎with the most instances, like byte[] and String.‎

This summary helps identify what is consuming memory, ‎which can be used to locate sensitive data like the IV ‎and private key.‎


![image](https://github.com/user-attachments/assets/42e507d4-6269-4f21-af8c-3a0858ec50fc)

![image](https://github.com/user-attachments/assets/e390ddcd-ce18-49f2-9d5c-7591b2823c61)

In the “Instances by Size” section of VisualVM, the entry ‎char[]#12 appears, which could be significant. This aligns ‎with the earlier analysis of the code where the flag is expected ‎to be printed after a sequence of dots (.................). This ‎char[]#12 instance might contain the actual flag or related ‎data, potentially hidden after these dots. By examining this ‎specific instance, you may uncover the flag or sensitive ‎information within like: ‎

![image](https://github.com/user-attachments/assets/22e6540b-cea2-4e1b-b735-8086db8a2dd0)

The correct and full URL, based on the preview, should likely ‎be:‎

https://drive.google.com/drive/folders/10duyyM...EJ5GvWiYWPR1abnDko2YbgkI2T?usp=sharing

This URL points to a Google Drive folder, but the middle ‎portion (...) seems to be obfuscated or incomplete. You might ‎need to investigate or reconstruct the missing part to access ‎the content correctly.‎


![image](https://github.com/user-attachments/assets/a812ef5a-9e56-4afc-9ec8-a0ba8b5f8f6e)


![image](https://github.com/user-attachments/assets/7112fd8e-0f65-41ed-83de-52a7819a2ce0)


We still haven’t found what we are looking for, to locate the ‎IV and KEY, you can navigate to the Decryption.main class ‎under the threats category. By examining the local variables ‎in this class, you can preview and retrieve the IV, KEY, and ‎the encrypted string needed for decryption. This will provide ‎the necessary information to successfully decrypt the string ‎using the AES algorithm.‎


![image](https://github.com/user-attachments/assets/19107e92-44e7-43bc-b692-1d0ab883b690)


![image](https://github.com/user-attachments/assets/7548ad10-04a3-40b0-9497-494d9010c298)


Now, by editing the Java code to incorporate the retrieved IV ‎and key, the decryption process will display the same ‎Google Drive link.‎

`drive.google.com/drive/folders/10duyyMEJ5GvWiYWPR1abnDko2YbgkI2T?usp=sharing‏ `



![image](https://github.com/user-attachments/assets/68555077-92ec-4ab8-ba5f-269912a8ff38)


After accessing the Google Drive link, you'll find a ZIP file ‎available for download. Once downloaded, you can begin ‎investigating the contents of the ZIP file to ‎continue your analysis.‎


![image](https://github.com/user-attachments/assets/5efaac03-ae26-4a17-a1f9-e024b03d0d87)


![image](https://github.com/user-attachments/assets/d49a219a-36be-4100-8714-7dfe46cefe8e)

The ZIP file is password-protected, and I attempted to crack it ‎using the zip2john tool. However, the attempt was ‎unsuccessful, and no useful output was generated. This ‎suggests that the password might be strong or complex, ‎requiring alternative methods or further analysis to ‎unlock the contents.‎


![image](https://github.com/user-attachments/assets/e99a767d-9cc1-431a-a7fe-990f38434cb7)

After attempting to crack the ZIP file with no success, you ‎decided to try the IV and KEY found in the heap dump ‎‎(.hprof) file. Using the IV, the ZIP file was successfully ‎extracted, allowing you to access its contents.‎


![image](https://github.com/user-attachments/assets/b3c0f7db-6e92-4a33-9655-837573bdc7b5)

By using the tree command, you can view the entire directory ‎structure. In this case, you noticed that three .txt files were ‎located deep within the the_flag directory. To extract and view ‎the contents of all these .txt files at once, you can use the ‎following command:‎



![image](https://github.com/user-attachments/assets/36ce2ef0-4aeb-4319-a085-73307ced8f95)

![image](https://github.com/user-attachments/assets/4d35890e-e41e-4919-9e62-3f35ba9d8d37)

![image](https://github.com/user-attachments/assets/cece1db6-4c62-4e69-98b8-8bd3754c0219)

Given the large number of subdirectories, it’s possible that the ‎directory structure itself might represent a cipher or some ‎form of encoded information. Each subdirectory could ‎potentially correspond to a letter, number, or symbol in ‎a coded message.‎

`‎8, 20, 20, 16, 19, 4, 18, 9, 22, 5, 7, 15, 15, 7, 12, 5, 3, 15, 13, ‎‎4, 18, 9, 22, 5, 6, 15, 12, 4, 5, 18, 19, `1`, Cap; 17, Cap; 2, ‎Cap; 19, Cap; 24, Cap; 13, Cap; 6, Cap; 2, Cap; 13, 14, Cap; ‎‎12, 20, _, 16, `8`, 11, 26, 15, 13, Cap; 26, Cap; 21, 5, `9`, ‎Cap; 13, Cap; 5, Cap; 19, 5, Cap; 25, 24, Cap; 25, `3`, `3`, 8, ‎‎?, 21, 19, 16, =, 19, 8, 1, 18, 9, 14, 7‎`


Decoding Instructions:‎

‎- Cap: Indicates that the letter should be capitalized.‎

‎- ‘number’: Represents a number that remains unchanged in ‎the sequence.‎

‎- Symbols (? _ =): These are symbols that should remain ‎unchanged in the sequence.‎


This sequence of numbers and instructions decodes into a ‎specific message where letters correspond to their positions in ‎the alphabet, some are capitalized, and specific symbols ‎remain unchanged. ‎


After deleting  the Cap and the numbers in `` and the symbols ‎and try to decrypt it : ‎




![image](https://github.com/user-attachments/assets/13e9c4d5-db89-4909-ad06-416a70b871d5)



So by using the A1Z26 and take in mind the above ‎instructions we will be able to extract the message which is ‎another google drive link : ‎

`https://drive.google.com/drive/folders/1QBSXMFBMnLt_p8kzomZUe9MESeYxY33h?usp=sharing`




![image](https://github.com/user-attachments/assets/fc0bac00-2f38-4380-8e03-13e7814563f3)

Each file has a password that I gave to participants when I sent them the questions

`Number 1-->Dummy Data-->number_1.zip --> "MyJ4l1lKuala2024!"` ‎

`Number 2-->Dummy Data-->number_2.zip --> "Langkawi_MySunset88" ‎`

`Number 3-->Dummy Data-->number_3.zip --> "Petron45@TwinTower" `
‎
`Number 4-->Dummy Data-->number_4.zip -->"SabahJungle#2023" ‎`

`Number 5-->Dummy Data-->number_5.zip --> "BatuCavesR1vers&" `
‎
`Number 6-->Dummy Data-->number_6.zip -->"Penang@Heritage123" ‎`

`Number 7-->Dummy Data-->number_7.zip --> "KL_Skyl1ne!2024" ‎`

# After unzipping the file, the participant will see a QR code for the outfit they need to bring the next day!



