## I’ve tampered with my note image to ensure no one can view it. I challenge you to uncover my secret note!

![image](https://github.com/user-attachments/assets/82dbd596-1618-4a09-979f-4190d070dd93)
![image](https://github.com/user-attachments/assets/76d10a26-d261-41a1-b411-409628462820)
Upon examining the hex editor to view the hexdump of the .png file, I ‎noticed that both the header and footer have been manipulated. The ‎highlighted bytes in yellow deviate from the standard .png file ‎structure.‎
PNG File Structure:‎
‎1.‎	PNG Signature (8 bytes): 

‎  89 50 4E 47 0D 0A 1A 0A‎

‎2.‎	IDHR Chunks:‎

	Length (4 bytes): 00 00 00 0D‎
	Chunk Type (4 bytes): 49 48 44 52‎
	Chunk Data (13 bytes)‎
	CRC (4 bytes)
 ‎
‎3.‎	Footer (IEND Chunk):‎

 ‎00 00 00 00 49 45 4E 44 AE 42 60 82‎
 
 00 00 00 00: Length of the chunk data, which is zero for ‎IEND.‎
 
 49 45 4E 44: Chunk type (ASCII for "IEND").‎

 AE 42 60 82: CRC for the IEND chunk type, a fixed value.`


![image](https://github.com/user-attachments/assets/231cccea-15cb-449b-9917-0de68f44a583)
![image](https://github.com/user-attachments/assets/15c548b0-c17f-46cc-8e37-7fa2c30fec75)

After editing the bytes we need to export the .png file to view it.

### Final Flag

`BAT{NeXt_gaMe_1s_tr4d1t10n4l_M4l4ys14n_g4m3_pl4y3d_w1th_s33ds_4nd_w00d3n}‎`
