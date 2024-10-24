## I attempted password cracking but was unsuccessful. Your task is to retrieve the password for the file and explore it!!
submit the flag using the flag format
Format : BAT{flag}

![image](https://github.com/user-attachments/assets/aecf7805-8cfd-48f0-9421-bed22fa5d21d)

I used the website LostMyPass to recover the password for a locked ‎‎.rar file. After following the steps on the site, I successfully retrieved ‎the password, which turned out to be "pookie".‎

![image](https://github.com/user-attachments/assets/342e2bb6-4680-4fed-92ec-e628104b784d)

I entered the command rar x FLAGS.rar, which extracts all files and ‎folders contained within the FLAGS.rar archive. The x option stands ‎for "extract with full paths," ensuring that the original directory ‎structure is preserved. After the extraction, I used the tree command ‎to visually display the directory structure of the extracted files and ‎folders.‎
![image](https://github.com/user-attachments/assets/7520ad7b-65a4-4c34-8f77-970d9dd8cb0c)

I examined the hexdump and observed that all three .txt files contain ‎base64 encoded text.‎


![image](https://github.com/user-attachments/assets/02f844ef-2e96-44c6-a38f-12466f810acd)

I decoded all the base64-encoded strings to uncover any hidden ‎messages. The decoded content from the files revealed the following:‎

•	The first file states: “it’s not how it looks.”‎

•	The second file appears to be a UTF-8 ‎encoded sequence: ‎‎\x48\x30\x70\x73\x63\x30\x74\x63\x68\x5f\x31\x73\x5f\x74\x33\‎x6e\x67\x74\x33\x6e\x67\x5f\x31\x73\x5f\x74\x31\x6e\x67\x74\x‎31\x6e\x67.‎

•	The third file says: “you’re close!!”‎

I find the UTF-8 sequence to be suspicious and plan to further ‎investigate its significance.
‎
![image](https://github.com/user-attachments/assets/0233fa54-740b-4920-a792-347c9f32e003)

To decrypt the UTF-8 encoded sequence, you can use the command:‎
echo -e ‎‎"\x48\x30\x70\x73\x63\x30\x74\x63\x68\x5f\x31\x73\x5f\x74\x33\x6e\x‎67\x74\x33\x6e\x67\x5f\x31\x73\x5f\x74\x31\x6e\x67\x74\x31\x6e\x67"‎
Here's a breakdown of the command:‎

•	echo is a command used to display a line of text or a string.‎

•	The -e option enables interpretation of backslash escapes (like ‎‎\x for hexadecimal values).‎

•	The string inside quotes contains hexadecimal representations ‎of ASCII characters, each prefixed with \x.‎

When you run this command, it converts the hexadecimal values into ‎their corresponding ASCII characters and outputs the decoded text.‎
Running the command will produce the following decrypted text:‎
H0psc0tch_1s_t3ngt3ng_1s_t1ngt1ng


### Final Flag

After decrypting the text, the flag is revealed as:
`BAT{ H0psc0tch_1s_t3ngt3ng_1s_t1ngt1ng}‎`

