## I downloaded a chess game and now I can't view any of my images. Can you help me restore them?
put your answer into the flag format: format: BAT{flag}

![image](https://github.com/user-attachments/assets/3d257104-978e-4001-9fac-be17e98d2443)

Upon unzipping the attached zip file, you will find five images with different file extensions. However, all of these images appear to be corrupted and cannot be opened. Additionally, there is an .exe file included, which is an executable that, when run on a machine, may have caused damage to the images. Given this scenario, our next step is to begin analyzing the .exe file to understand its impact and the extent of the harm it has caused to the images.

![image](https://github.com/user-attachments/assets/74ab8851-6e69-4781-aa6f-c2f02efc911d)

The simplest and most effective way to approach analyzing an .exe file is by using the strings command. This command allows us to extract and view readable text within the file, which can reveal important information, such as the type of script and the programming language used to create it. In this case, the strings command indicates that the executable is written in Python.

![image](https://github.com/user-attachments/assets/f86ce526-ae83-4f82-871d-a5762dbcae92)

To recover the source code from the .exe file, use the pyinstxtractor.py tool, which can be found at this GitHub repository. The command used is as follows: python3 /home/3BOOD/Documents/Challenge_new/Tools/pyinstxtractor/pyinstxtractor.py ChessPayload.exe

After executing this command, you will notice that a new folder has been created. Navigate into the ChessPayload.exe_extracted/ directory. Inside, you'll find numerous .pyc files, which are Python-compiled bytecode. This bytecode is an intermediate form that a Python compiler generates by translating source code into bytecode.

As a general rule, you should always prioritize decompiling the .pyc file that shares the same name as the executable. This file is most likely to contain the main logic of the original script.

![image](https://github.com/user-attachments/assets/63afc344-95b2-4bf4-b885-e030972ae640)

To view the source code, visit PyLingual and use the online decompiler. By uploading the .pyc file, you can easily decompile it and reveal the original Python source code.

![image](https://github.com/user-attachments/assets/dfeee268-6b1b-4cf3-9922-3b7a1f5c89dc)

After selecting the ChessPayload.pyc file, the decompiler will reveal the source code of the original .exe file.

![image](https://github.com/user-attachments/assets/c42bbe49-93b9-4e78-b16a-c2af3c20ca37)

![image](https://github.com/user-attachments/assets/97496436-d765-4600-b879-4b8a2528ec42)

Save the source code for further analysis. The code in question encrypts image files within a directory by modifying each byte of the image data. The encrypt_image function reads an image file, applies a simple encryption method (incrementing each byte value by 1 modulo 256), and then saves the altered file. The encrypt_all_images_in_directory function processes all image files in a specified directory, encrypts them using the encrypt_image function, and appends "_HACKED!!" to each filename. The main section of the code sets the directory path and executes the encryption process on all images within that directory.

![image](https://github.com/user-attachments/assets/6e2ed28c-92b2-4be4-8f3e-04640154947b)

We have written a simple script to decrypt image files that were encrypted by the previous script. The decrypt_image function reverses the encryption process by subtracting 1 from each byte value (modulo 256) and saves the decrypted image. The decrypt_all_images_in_directory function iterates through a directory, decrypting files with "_HACKED!!" in their names and renaming them with "_SOLVED!!". The main part of the code sets the directory path and executes the decryption process on all applicable images within that directory.

![image](https://github.com/user-attachments/assets/9020aac9-f153-4b09-bd4b-e177abd3fcf2)

After executing the Python script, you will find that all the images are now viewable.

![image](https://github.com/user-attachments/assets/ee048a61-1903-4b72-a7f8-30733aeca1ea)

![image](https://github.com/user-attachments/assets/bd394c36-fb7e-4b45-ae3f-59229c466467)

Next, use exiftool to extract the metadata from the images with the following command: exiftool * | grep Comment This will reveal 

### Final Flag:
The flag is:

`BAT{K3t1nt1ng_is_ch1ldr3n's_tr4d1t10n4l_g4m3}‎`
