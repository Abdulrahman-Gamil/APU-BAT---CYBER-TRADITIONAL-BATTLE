## I've hidden a confidential secret inside an image, but unfortunately, I forgot the password for my old Chapteh picture. Can you help me find the secret?


### Steps to Solve the Challenge

1. **Extract Metadata:**
   - Use Exiftool to extract the metadata from the image, which may contain hidden information. 
   - Upon inspecting the metadata, take note of the comment field that contains the string `S0_m4ny_c0l0rs`. This clue suggests that the image might contain hidden data.

![image](https://github.com/user-attachments/assets/ca47e125-6167-4031-a38d-f41925fc6c15)


2. **Use Steghide to Extract Hidden Data:**
   - Steghide is a tool that allows you to hide and extract data from images and other file formats.
   - By using Steghide on the image, you can extract any embedded files (e.g., a ZIP file) that may be hidden in the data layers of the image.


3. **Unzip the Extracted File:**
   - After extracting the ZIP file from the image, unzip it to reveal nested directories.
   - Use the `tree` command to list all files and notice that the directories are numbered sequentially from 1 to 9.

4. **Collect and Decode Folder Names:**
   - Each folder contains encoded folder names. Concatenate these folder names to form a Base64-encoded string.
   - Decode the Base64 string to reveal the final flag.

![image](https://github.com/user-attachments/assets/264dcf5f-312e-437e-a9c1-d8810941655b)

### Final Flag

After decoding, the flag is revealed as:

`BAT{F0cus_F33t_N_C0ntrol_Ch4pt3h}`
