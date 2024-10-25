## my friend Rijndael send me this old photo of me playing teng-teng, i believe it's more than a photo, help me to find it out!! 


### Steps to Solve the Challenge

1. **Extract Metadata:**
   - The image contains metadata, specifically a `Comment` field that holds encrypted text. To view the comment metadata, run the following command:
     ```bash
     exiftool teng-teng.png | grep Comment
     ```
     ![image](https://github.com/user-attachments/assets/4bff8945-795e-44f6-bb08-78e8c5c3d2bc)

2. **Extract Embedded Files:**
   - The image also contains files embedded within it. To extract these files, use `binwalk`:
     ```bash
     binwalk -e teng-teng.png
     ```
   - After extraction, view the directory structure by running:
     ```bash
     tree
     ```

![image](https://github.com/user-attachments/assets/9b21366e-65f1-4c88-b195-51d2b78e20f9)

3. **Find the Key and IV:**
   - Inside the extracted directory, you'll find a strange file named `"my notes.txt"`. Opening this file reveals a hint: "AESia," which points to the use of the AES encryption algorithm. AES requires both a **key** and an **initialization vector (IV)** to decrypt the text found in the metadata.
   - Upon further inspection of the file:
     - **The key** is located on **line 274**.
     - **The IV** is located on **line 450**.

![image](https://github.com/user-attachments/assets/24228cba-860f-4dfa-a877-a243833602a7)
![image](https://github.com/user-attachments/assets/3d2d9531-f58b-497b-8944-983161323ea4)
![image](https://github.com/user-attachments/assets/d0dc0c27-67fd-451e-b4a7-845f8c1c9a56)

4. **Decrypt the Text:**
   - Once you've gathered the key and IV, use the **CyberChef** tool to decrypt the encrypted text from the image's `Comment` field.

![image](https://github.com/user-attachments/assets/4d7bd9a3-c31a-4d38-8b81-67f311f02f08)

### Final Flag

After decrypting the text, the flag is revealed as:

`BAT{Teng_teng_1s_pl4yfround_g4m3}`

### Hints from the Description

- The friend’s name "Rijndael" is a direct reference to **AES (Advanced Encryption Standard)**, which is also known as the **Rijndael cipher**. This hints early on that the challenge will involve AES encryption.
- The hint "AESia" in the extracted files confirms the use of the AES encryption algorithm, guiding the solver to search for the key and IV necessary for decryption.

