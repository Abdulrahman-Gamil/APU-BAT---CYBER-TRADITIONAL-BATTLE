## My geeky friend, who's super into his country, spends all day glued to YouTube. Somewhere, he's hidden some private keys, and these keys contain important notes and more keys, but only he knows where they are or what they mean. On top of that, there's also a secret message hidden somewhere, but no one has any idea where it could be.
Find the SHA-256 of my private keys and Find the MD5 hash of the actual secret message and submit it. For example:‎
Hello Jumper --> md5 = 1a308d7ad55d92367d56acce012e2ed4‎
passwords.txt --> SHA-256 = 3049a1f8327e0215ea924b9e4e04cd4b0ff1800c74a536d9b81d3d8ced9994d3
the flag : BAT{1a308d7ad55d92367d56acce012e2ed4_3049a1f8327e0215ea924b9e4e04cd4b0ff1800c74a536d9b81d3d8ced9994d3}‎


### Hints from the Description:
- **YouTube obsession** might suggest that the user’s YouTube habits will lead to useful clues (e.g., names, passwords).
- **Private keys** refer to files hidden in the process (possibly through steg tools or encryption).
- **Tingting** is a major clue for unlocking a password, particularly related to the YouTuber.

### Steps to Solve the Challenge:


1. **Unzip the Initial File:**
   - Players start by unzipping the provided zip file, which contains:
     - `someone.jpg`
     - `FFD8FFDB0084000101010101.zip`
  
2. **Open the Password-Protected Zip File:**
   - The file `FFD8FFDB0084000101010101.zip` is password protected.
   - The password is **tingting**, which can be found from the YouTuber in the image. (Youtuber Name: Tingting)

![image](https://github.com/user-attachments/assets/7f28b3ef-302f-44d8-8338-cb1ebadb85df)
![image](https://github.com/user-attachments/assets/464da44e-597b-4ff9-8d73-3046db3f8c44)

   - Command: `unzip -P tingting FFD8FFDB0084000101010101.zip`

![image](https://github.com/user-attachments/assets/cacbbf5c-9b83-41a6-b39c-b61f43dc0cd1)

3. **Extract Files from the Zip:**
   - After unzipping, players will find `flag.jpg`.

![image](https://github.com/user-attachments/assets/6df8b65c-eac2-4508-b3aa-32bf6160a57e)
![image](https://github.com/user-attachments/assets/834e32aa-b2bf-42b8-a6d1-bf07bee91b63)
![image](https://github.com/user-attachments/assets/312a3576-a116-4ed3-9bd3-f3d1e976e88d)

4. **Identify the Correct Header:**
   - The file name `FFD8FFDB0084000101010101` is the correct header for `flag.jpg`.
   - Players need to change the header of corrupted jpg to `FFD8FFDB0084000101010101`.

5. **Fix the Header of Corrupted Image:**
   - Use a hex editor to fix the header to `FFD8FFDB0084000101010101`.

![image](https://github.com/user-attachments/assets/a447371b-3699-4678-b5d7-4d6b9de385b6)

this is the image:

![image](https://github.com/user-attachments/assets/189c2ef7-e7ef-4fdf-94f7-f8329d46ae3f)

6. **Find the Binary Code in the Flag:**
   - Once the header is fixed, view `flag.jpg`.
   - Inside, there is hidden binary code that can be viewed by manipulating individual color channels (top right corner).
   - Use the `stegsolve` tool to view the binary code.

![image](https://github.com/user-attachments/assets/9c865e52-4424-4896-9d96-dcbf2c0ed820)

   - Binary Code: `1110110100100010111100101`

7. **Translate the Binary Code:**
   - The binary code translates to `31081957`, corresponding to Malaysia's Independence Day (31/08/1957).

![image](https://github.com/user-attachments/assets/dd5ad355-b0a0-4af8-910c-ec5a98302c2b)

8. **Use Steghide to Extract the Text File:**
   - Use **steghide** with the passphrase `independence` to extract the hidden text file from `flag.jpg`.
   - The extracted text file contains the key for decoding the message in `message.jpg`.

![image](https://github.com/user-attachments/assets/54208f9e-9c93-49b0-a30f-ba026aa2e564)

9. **Decode the Message in message.jpg:**
   - Use the key from the text file to decode the hidden message in `message.jpg`. (Use cipher identifier to decrypt the message)

![image](https://github.com/user-attachments/assets/29d9e654-88d0-4d1e-ae9a-967284d693e0)
![image](https://github.com/user-attachments/assets/22c96b86-3183-4ae5-9172-48b2b44bceae)

![image](https://github.com/user-attachments/assets/2c030b46-344d-45f9-89c5-93fb2d88a504)

‎MD5: `383198341101c3d319fc129507ddebd4‎`

10. **SHA-256 Hash of key.txt:**
   - The key.txt file contains encrypted content, but only the SHA-256 sum of the key is needed.
   - SHA-256 of key.txt:
     `‎97ee1dba08302cf7e3a86e86377b852eceb7c4b6e176aa0ad5c44174e412066a‎`

![image](https://github.com/user-attachments/assets/f78b033e-0ed7-400b-9a44-b3fc16f8e50a)
![image](https://github.com/user-attachments/assets/e6c82363-4fd5-4892-9760-1092f90a57ec)
![image](https://github.com/user-attachments/assets/f0837792-3f7b-410a-aaac-e7714f215a61)
![image](https://github.com/user-attachments/assets/cb1b0db3-9036-4940-b63b-6340193e2653)
![image](https://github.com/user-attachments/assets/68874601-807d-4f28-9992-8d3dd10349ae)

![image](https://github.com/user-attachments/assets/76190d6d-56a5-4ed5-bf10-fa9a4a1bd348)
### Final Flag:
`BAT{‎383198341101c3d319fc129507ddebd4‎_‎97ee1dba08302cf7e3a86e86377b852eceb7c4b6e176aa0ad5c44174e412066a‎}`


