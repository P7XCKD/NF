### To hide a message in an image
```bash
steghide embed -cf cover.jpg -ef secret.txt -p yourpassphrase
```
### To extract a message in an image
```bash
steghide extract -sf cover.jpg -p yourpassphrase
```

### to check info of file

```bash
steghide info cover.jpg
```
### Flags explained:

-cf : Cover File (image/audio to hide data in)

-ef : Embed File (file to be hidden)

-sf : Stego File (optional output file with hidden data)

-p  : Passphrase for encryption/decryption




***

![image](.attachments/2e5b032656b29e5fe1a715a435125f3e600f01f7.png) 