## I received an image from my friend Wala, the math genius ***= I used to play Chapteh with. It holds secrets beyond what the eyes can see or the ears can hear. Can you help me retrieve the hiDDen message?  





### Steps to Solve the Challenge

1. **Verify the File Type:**
   - First, verify the file type. We can see that it’s a JPG file.
   - Use `binwalk` to attempt to extract any additional files from the JPG image, but no extra files are found.
     
   ![image](https://github.com/user-attachments/assets/487bc29a-7b58-4133-88c2-34c942ddc8e6)
  

3. **Inspect the File’s Header and Footer:**
   - Use `hexdump` to inspect the header and footer of the image. A standard JPG file should start with `FF D8 FF E0` and end with `FF D9`.
   - During the string search of the image, we come across an `.mp4` file, suggesting that the JPG might contain an embedded file.
   - The description states *"it holds secrets beyond what the eyes can see or the ears can hear,"* indicating that this could be an audio file embedded within the image.
  
   ![image](https://github.com/user-attachments/assets/451b118e-3a71-4dac-bbb6-be66aee8dd7e)
 ![image](https://github.com/user-attachments/assets/9e8d39bf-4283-4e78-8dc8-2e33061d20bc)
  ![image](https://github.com/user-attachments/assets/d74454b3-ff9b-42ea-940a-f415da3a1fd0)


5. **Use DD to Extract the MP3 File:**
   - Since the embedded file is likely an audio file, we extract it using the `dd` command to copy raw data from the JPG file, starting from a specific byte.
   - The command to extract the hidden `.mp3` file is as follows:
     ```bash
     dd if=Chapteh.jpg bs=1 skip=181644 of=secret.mp3
     ```

     ![image](https://github.com/user-attachments/assets/11600335-ef87-4ac4-a82d-718e911c3dd0)

   - This command:
     - `if=Chapteh.jpg`: Specifies the input file (the image).
     - `bs=1`: Sets the block size to 1 byte.
     - `skip=181644`: Skips the first 181,644 bytes of the image file to access the embedded data.
     - `of=secret.mp3`: Specifies the output file where the extracted audio will be written.
     
6. **Play and Analyze the MP3 File:**
   - Playing the extracted `.mp3` file reveals familiar sounds of keyboard clicks associated with the **T9 cipher**. These sounds are known as **DTMF** (Dual-Tone Multi-Frequency) tones, often used in telephony systems.

  ![image](https://github.com/user-attachments/assets/ecc771f4-d5d7-4171-85b2-35859ed381b6)

   
7. **Extract the Encoded Number:**
   - The sound in the MP3 file encodes a series of numbers: `899999*222174433777*22200555`.
   - The description’s hint, *"math genius,"* suggests solving these numbers as part of an equation.

8. **Solve the Equation:**
   - When solved, the equation `899999*222174433777*22200555` results in the number:
     ```
     4439151230598394951353765
     ```
     ![image](https://github.com/user-attachments/assets/e737478c-9e06-494b-a5e1-cf8c6b6a54d9)


9. **Final Flag:**
   - After successfully extracting the content from the zip file and examining the results, the final flag is:
     ```
     BAT{F33t_0nly_N0_H4nds_Ch4pt3h}
     ```

     ![image](https://github.com/user-attachments/assets/4d3f6fe6-5acd-4250-8f5f-0cfe61cb4562)


### Hints from the Description:
- The phrase *"beyond what the eyes can see or the ears can hear"* hints at the presence of hidden data in a non-visual format, pointing towards an audio file (in this case, an embedded MP3).
- The mention of *"math genius"* implies that some numerical manipulation or equation solving will be required to unlock the hidden message.

