# 🔐Image_Steganography_using_LSB_Technique

## 📌 Overview
This project implements **Image Steganography** using the C programming language.  
It enables secure communication by embedding a secret file within a BMP image without causing noticeable visual changes.

The system supports both:
- **Encoding**: Hiding secret data inside an image  
- **Decoding**: Extracting hidden data from the image  

---

## 🎯 Objectives
- To understand and implement **data hiding techniques**
- To apply **bit manipulation (LSB method)** in a real-world scenario
- To gain hands-on experience with **file handling in C**

---

## ⚙️ Features
- Encode secret text into BMP images  
- Decode hidden data from stego images  
- Maintains image quality (no visible distortion)  
- Command-line based execution  
- Lightweight and efficient implementation  

---

## 🧠 Working Principle

The project uses the **Least Significant Bit (LSB) technique**:

- Each byte of image data is modified at the least significant bit level  
- The change is minimal and not detectable by the human eye  
- Secret data is embedded bit-by-bit into the image  

---

## 📂 Project Structure
STEGNO_25040B/
│
├── main.c # Program entry point
├── encode.c # Encoding functionality
├── decode.c # Decoding functionality
├── encode.h # Header for encoding
├── decode.h # Header for decoding
├── common.h # Common utilities
├── types.h # Custom data types
│
├── input.bmp # Input image file
├── secret.txt # File to be hidden
├── output.bmp # Encoded image
├── decoded.txt # Extracted output
│
└── scripts.sh # Execution scripts (if any)

---

## 🚀 Compilation & Execution

### 🔧 Compile
```bash
gcc *.c -o stego
🔐 Encoding
./stego -e <input.bmp> <secret.txt> <output.bmp>
🔓 Decoding
./stego -d <output.bmp> <decoded.txt>

🧪 Example
Input Image: input.bmp
Secret File: secret.txt

After Encoding → output.bmp
After Decoding → decoded.txt


👨‍💻 Author
Suraj Zure
Final Year - Electronics & Telecommunication Engineering
Aspiring Embedded Systems & IoT Engineer
