## An old friend from my university sent me an envelope with a letter and a flight ticket. Can you find his location? 
Find the MD5 hash of the result and submit it. For example:‎
Input: "Jeddah 334400"
MD5 Hash: 1a308d7ad55d92367d56acce012e2ed4
Flag: BAT{1a308d7ad55d92367d56acce012e2ed4}

### Encrypted Message:

Prgth Beiwfm! Uje aaom mbc ozmg? I tu wadvoqgg rwi gw n bife hn Hvvtoqgg pqhu abhm hf fg teqrill hxzs. Jmnm ghuk jsfb gmiwimqcaiy Hiear ihgqez nhr tlrrl spv. Tfmmf gpr bife, emh'f prvl mo t uozix imtrug hb pnqm lofm Bnav Gmfad ibq Ilvu Zokmbt rhnb eidm hum bgl wara...


![image](https://github.com/user-attachments/assets/87f1bd8e-ff21-47f7-8582-8e06868b1903)

![image](https://github.com/user-attachments/assets/e8beee78-db73-4f73-bff9-b8223c8e6d71)


### Solution Steps:

1. **Identify the Cipher (using Cipher Identifier)**  
   The name **"Blaise De"** refers to **Blaise de Vigenère**, the creator of the Vigenère cipher.
   - **Key:** `INVITATION` (found in the title)

2. **Decrypt the Message**  
   Using the Vigenère cipher with the key `"INVITATION"`, the decrypted message reads:

   ![image](https://github.com/user-attachments/assets/b07a93a4-9758-4a78-96e0-1c29fe942884)

Hello Blaise! How have you been? I am inviting you to a game of Tingting with some of my friends here. Wear your best traditional Malay attire for added fun. After the game, let's head to a mamak nearby to have some Nasi Lemak and Ayam Goreng just like the old days...


4. **Find the Location**  
The hint `"m 1 | 2 | 2 o | 2"` reads as "mirror." Using the **Atbash cipher**, the location is:  
**Taman Tasik Titiwangsa, Titiwangsa, 53200 Kuala Lumpur, Wilayah Persekutuan Kuala Lumpur**


![image](https://github.com/user-attachments/assets/fc7d175d-965c-4b2e-b637-79a304bbfff2)

![image](https://github.com/user-attachments/assets/eedbdeb9-0283-49f4-8080-5c722e7f57c5)


5. **MD5 Hash of the Location**


![image](https://github.com/user-attachments/assets/c06ddecc-f6f9-41c5-8746-80ebe71048a9)

The MD5 hash of `"Taman Tasik Titiwangsa, Titiwangsa, 53200 Kuala Lumpur, Wilayah Persekutuan Kuala Lumpur"` is:  
`8e4406d8a3b91e1114605d546378e537`

### Final Flag:
`The flag is : BAT{8e4406d8a3b91e1114605d546378e537}‎`
