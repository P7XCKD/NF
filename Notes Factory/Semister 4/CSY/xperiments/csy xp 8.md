Experiment 8: Steganography Tool Using Command Prompt and JPG File

Aim: To hide and extract a text message inside a JPG file using the steghide tool via the command prompt.

Theory: Steganography is the practice of concealing information within digital media such as images, audio, or videos. The steghide tool enables embedding and extracting hidden messages inside JPG images while keeping their visual integrity intact.

Steps to Hide a Message Using steghide
1. Open the command prompt and navigate to the directory containing your image and secret text file:
cd D:\B050

2. Embed the secret text file (secret.txt) inside the image (img.jpg):
steghide embed -cf img.jpg -ef secret.txt

3. Enter a passphrase when prompted. This passphrase is required for extraction.
4. If successful, the tool will confirm that the file has been embedded.

Steps to Extract the Hidden Message
1. Extract the hidden message from the image using the following command:
steghide extract -sf img.jpg -xf extracted.txt

2. Enter the passphrase when prompted.
3. If the passphrase is correct, the tool will extract the hidden message and save it in extracted.txt.

Example Output:
D:\B050>steghide extract -sf img.jpg -xf extracted.txt
Enter passphrase:
wrote extracted data to "extracted.txt".


Checking if an Image Contains Hidden Data

To check whether an image has hidden data, use:
steghide info img.jpg


Conclusion:
Using steghide, we successfully embedded and extracted secret data within a JPG image. 
