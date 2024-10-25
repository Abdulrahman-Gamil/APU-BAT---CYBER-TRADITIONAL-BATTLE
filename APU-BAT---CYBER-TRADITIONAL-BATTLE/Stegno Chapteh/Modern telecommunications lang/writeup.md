## A friend, Wala, figured out that there is a strange text in this picture. Help me find it and unlock my zip file!!


### Steps to Solve the Challenge

1. **Extract Strings from the Image:**
   - Use the `strings` command to extract all printable strings from the `nothing.png` image file.
   - Command:
     ```bash
     strings nothing.png | tail
     ```

2. **Identify Morse Code:**
   - Among the extracted strings, find the line containing Morse code:
     ```bash
     { -.- ...-- ...-- .--. ..--.- - .... ...-- ..--.- -.-. .... ....- .--. - ...-- .... 
     ..--.- .---- -. ..--.- - .... ...-- ..--.- ....- .---- .-. }
     ```

![image](https://github.com/user-attachments/assets/a7f3ef81-15b8-4cef-b8ae-a93def9ccb9d)


3. **Decode Morse Code:**
   - Use CyberChef to decode the Morse code.
   - Output: 
     ```
     K33P_TH3_CH4PT3H_1N_TH3_41R
     ```

**The password is:** `K33P_TH3_CH4PT3H_1N_TH3_41R`

Unzip the secret message zip file and reveal the flag:

![image](https://github.com/user-attachments/assets/18191bc9-a274-4e7c-8548-0768d821a96f)

**Flag:** `BAT{U_n44d_2_K33p_Th3_Ch4pT3H_1N_tH3_41r}`
