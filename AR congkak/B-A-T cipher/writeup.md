## Wala has crafted her own unique cipher and used it to send a secret message. On the surface, the letter appears ordinary, but there’s more to it than meets the eye. Can you decipher Wala’s hidden message and reveal the secret she’s concealed? The truth is there—if you can find it.

![image](https://github.com/user-attachments/assets/272b977d-ff64-4dea-9a8a-58243ee9b152)

The image presents a cryptic puzzle involving bats and encoded messages. The narrative ‎mentions that these bats are "masters of the night," flying silently through the darkness ‎while whispering secrets. The reference to "steganography" and "B-A-T cryptography" ‎suggests that hidden information is embedded in the image, which requires decryption.‎

### Step 1: Extracting Hidden Data Using Steganography

The first clue is the mention of "steganography," a technique used to hide data within an ‎image. To uncover any concealed files or messages within the image, the tool Steghide ‎can be used. Steghide allows us to extract hidden data if it exists within the image. And ‎this tool needs passphrase and it cannot be cracked, or brute forced.‎

### Step 2: Decoding the B-A-T Cryptography

The image mentions "B-A-T cryptography," which is a strong hint toward a custom ‎encoding system. The letters B, A, and T can be translated into a ternary (base-3) system:‎
`
  	B = 0‎, 
  	A = 1‎,
  	T = 2‎
`

This conversion allows us to decode the sequence of letters found at the bottom of the ‎image.‎

Sequence Given (Signature):‎ BBB ATB TBT BBA BBB TBA

* Step-by-Step Conversion:‎

    ![image](https://github.com/user-attachments/assets/f7f19604-aa54-4468-9df8-237d00b93583)

‎1.‎	BBB converts to 000 in base-3, which corresponds to the letter A (assuming A = ‎‎0).‎

‎2.‎	ATB converts to 102 in base-3, which corresponds to the letter P.‎

‎3.‎	TBT converts to 201 in base-3, which corresponds to the letter U.
‎


‎4.‎	BBA converts to 001 in base-3, which corresponds to the letter B.‎



‎5.‎	BBB converts to 000 in base-3, which corresponds to the letter A.‎

‎6.‎	TBA converts to 201 in base-3, which corresponds to the letter T.‎

Decoded Result:‎
After decoding, the sequence translates to the string "APUBAT"‎

### Step 3: Interpreting the Date as a Hint
The date displayed at the bottom of the image, 1030/03/03, also serves as a crucial hint. ‎The repeated presence of the number 3 may reinforce the idea of a base-3 (ternary) ‎system being central to the decryption process. This could suggest the importance of the ‎B-A-T cipher or even provide additional context for interpreting the passphrase.‎

### Step 4: Utilizing the Decoded Passphrase
With the passphrase "APUBAT" in hand, we can proceed to extract any hidden content ‎from the image using Steghide. This password is derived from the B-A-T cryptographic ‎sequence provided.‎

Command:‎
Use the decoded passphrase with Steghide:‎
``steghide extract -sf BAT_Cipher.jpg -p APUBAT``
  ![image](https://github.com/user-attachments/assets/8af64c78-2877-4364-affe-44759f4e0875)

  ![image](https://github.com/user-attachments/assets/2c341656-e317-406a-89d2-88d20e875718)

Each file has a password that I gave to participants when I sent them the questions:

`•	Number 15-->B-A-T cipher -->number_15.zip --> "Gent1ngH1lls_2024!" ‎`

`•	Number 16-->B-A-T cipher -->number_16.zip --> "KualaLumpur@Bukit88" ‎`

`•	Number 17-->B-A-T cipher -->number_17.zip -->"PeninsularT1gress#90" ‎`

`•	Number 18-->B-A-T cipher -->number_18.zip --> "PeranakanSp1ce2023!"` ‎

`•	Number 19-->B-A-T cipher -->number_19.zip --> "Monsoon_Seas0n!45" ‎`

`•	Number 20-->B-A-T cipher -->number_20.zip --> "Rafflesia#Bl00m2024!" ‎`

# After unzipping the file, the participant will see a QR code for the outfit they need to bring the next day!


