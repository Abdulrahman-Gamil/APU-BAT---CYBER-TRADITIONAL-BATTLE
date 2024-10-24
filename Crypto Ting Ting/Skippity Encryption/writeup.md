## “OVARHVVBKV”‎ a very easy game. A game where you have to JUMP a lot and your opponent will be me, the ‎JUMPing Champion of skippity town. Now why ‎are you looking at me like that? What key are you talking about? I don’t know any key, over ‎here the only thing we do is JUMP.
Find the MD5 hash of the result and submit it. For example:
Hello Jumper --> md5 = 1a308d7ad55d92367d56acce012e2ed4
the flag : BAT{1a308d7ad55d92367d56acce012e2ed4}‎
‎
### Steps to Solve:

#### Step 1: Identify the Keyword
- **Hint:** The word "JUMP" is mentioned multiple times.
- **Key:** `JUMP`

#### Step 2: Identify the Cipher
![image](https://github.com/user-attachments/assets/7d8099bf-76b8-461f-b451-66b348e3b8b8)

- After using the cipher identifier tool, many possible ciphers were suggested. However, none of the suggested ciphers required a private key and didn’t provide any usable results.
- This led to the conclusion that the Playfair cipher must be used, as it requires a keyword, which is hinted at in the description.

#### Step 3: Apply the Playfair Cipher
- **Action:** Use the keyword "JUMP" to create a 5x5 matrix for the Playfair cipher.
- **Goal:** Decode the encrypted text `OVARHVVBKV`.
  
| J | U | M | P | A |
|---|---|---|---|---|
| B | C | D | E | F |
| G | H | I | K | L |
| N | O | Q | R | S |
| T | V | W | X | Y |

#### Step 4: Decode the Message
- **Decoded Message:** `HOPSCOTCHX`

#### Step 5: Generate MD5 Hash
- **Final Step:** Find the MD5 hash of the decoded message.

![image](https://github.com/user-attachments/assets/47a8663b-a518-4553-951e-fa040d8d338a)

### Final Flag:
`BAT{a7a13d17fbc3bc356f152984821323bd}`
