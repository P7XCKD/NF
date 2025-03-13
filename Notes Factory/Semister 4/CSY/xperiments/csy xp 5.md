**LSB Steganography**

**Aim:** Implement the Least Significant Bit (LSB) Steganography algorithm in Python.

**Theory:**

LSB Steganography is a technique for hiding information within a digital image by modifying the least significant bits of the image's pixel values. Since these bits contribute the least to the image's overall appearance, changes are generally imperceptible to the human eye.

**Algorithm:**

1.  **Read Image:** Load the cover image.
2.  **Convert Message:** Convert the secret message into a binary string.
3.  **Iterate Pixels:** Traverse the image pixels.
4.  **Embed Bits:** Replace the LSB of each pixel's color component with a bit from the message.
5.  **Save Image:** Save the steganographic image.
6.  **Extract Message:** Load the steganographic image, extract the LSBs, and convert back to the original message.

**Program (Python):**

```python
from PIL import Image

def encode_lsb(image_path, message, output_path):
    img = Image.open(image_path).convert('RGB')
    width, height = img.size
    binary_message = ''.join(format(ord(i), '08b') for i in message)
    data_index = 0

    if len(binary_message) > width * height * 3:
        raise ValueError("Message too large to fit in image.")

    pixels = list(img.getdata())
    encoded_pixels = []

    for pixel in pixels:
        r, g, b = pixel
        if data_index < len(binary_message):
            r = (r & ~1) | int(binary_message[data_index])
            data_index += 1
        if data_index < len(binary_message):
            g = (g & ~1) | int(binary_message[data_index])
            data_index += 1
        if data_index < len(binary_message):
            b = (b & ~1) | int(binary_message[data_index])
            data_index += 1
        encoded_pixels.append((r, g, b))

    encoded_img = Image.new('RGB', (width, height))
    encoded_img.putdata(encoded_pixels)
    encoded_img.save(output_path)

def decode_lsb(image_path):
    img = Image.open(image_path).convert('RGB')
    pixels = list(img.getdata())
    binary_message = ''

    for pixel in pixels:
        r, g, b = pixel
        binary_message += str(r & 1)
        binary_message += str(g & 1)
        binary_message += str(b & 1)

    decoded_message = ''
    for i in range(0, len(binary_message), 8):
        byte = binary_message[i:i + 8]
        if len(byte) == 8:
            decoded_message += chr(int(byte, 2))
        else:
            break
    return decoded_message.split('\0')[0]

# Example usage
image_path = "cover_image.png"
secret_message = "This is a secret message.\0" # null terminator added
output_path = "stego_image.png"

encode_lsb(image_path, secret_message, output_path)
extracted_message = decode_lsb(output_path)
print("Extracted Message:", extracted_message)
```
