# 🔐 Image Steganography using LSB Technique

## 📘 Overview
This project implements **Image Steganography** using the **Least Significant Bit (LSB)** method in **C programming**.  
It enables users to **embed a secret file** (such as `.txt`, `.c`, `.h`, `.sh`) inside a **24-bit `.bmp` image**, and later **decode** it safely — without any visible change to the image.

The system ensures:
- Proper file validation  
- Image capacity verification  
- Reliable decoding using a **magic string**  

---

## ⚙️ Features
- 🔐 Secure data hiding using LSB manipulation  
- 🖼️ Supports 24-bit BMP images  
- 📄 Handles multiple secret file types (`.txt`, `.c`, `.h`, `.sh`)  
- ✅ Validates file names, extensions, and storage capacity  
- 🧠 Modular C design for better readability and maintainability  
- 🔍 Magic string verification for accurate decoding  
- 💬 Step-by-step console output for execution transparency  

---

## 🧩 Project Structure
├── main.c # Entry point (CLI handling)
├── encode.c # Encoding implementation
├── encode.h # Encoding structures & prototypes
├── decode.c # Decoding implementation
├── decode.h # Decoding structures & prototypes
├── types.h # Common enums (Status, OperationType)
├── common.h # Shared macros (e.g., MAGIC_STRING)


---

## 🧠 Working Principle: LSB Encoding
A 24-bit BMP image uses **3 bytes per pixel (RGB)**.  
By modifying the **least significant bit (LSB)** of each byte, secret data can be embedded without affecting image appearance.

| Original Byte | Binary     | After Encoding ‘1’ |
|--------------|-----------|-------------------|
| 200          | 11001000  | 11001001          |

👉 The image remains visually unchanged while carrying hidden data.

---

## 🧮 Encoding Process
1. **Validate input files**  
2. **Open required files**  
3. **Check image capacity**  
4. **Copy BMP header**  
5. **Embed data sequentially**:
   - Magic string  
   - Secret file extension size  
   - Secret file extension  
   - Secret file size  
   - Secret file data  
6. **Copy remaining image data**  
7. **Generate output image**  

---

## 🧾 Decoding Process
1. **Validate and open encoded image**  
2. **Skip BMP header (54 bytes)**  
3. **Verify magic string**  
4. **Decode sequentially**:
   - Extension size  
   - Extension name  
   - File size  
   - File data  
5. **Reconstruct the original file**  

---

## 🧰 Data Structures

### `EncodeInfo` (from `encode.h`)
```c
typedef struct _EncodeInfo {
    char *src_image_fname;
    FILE *fptr_src_image;
    uint image_capacity;

    char *secret_fname;
    FILE *fptr_secret;
    char extn_secret_file[5];
    char secret_data[100000];
    long size_secret_file;

    char *stego_image_fname;
    FILE *fptr_stego_image;
} EncodeInfo;
DecodeInfo (from decode.h)
typedef struct _DecodeInfo {    char *stego_image_fname;    FILE *fptr_stego_image;    char *secret_fname;    FILE *fptr_secret;    long ext_size;    char extn_secret_file[5];    long size_secret_file;} DecodeInfo;

🧭 Command-Line Usage
🔐 Encoding
./stego -e <source.bmp> <secret.txt> [output_image.bmp]
Example:
./stego -e sample.bmp secret.txt encoded.bmp

🔓 Decoding
./stego -d <encoded_image.bmp> [output_name]
Example:
./stego -d encoded.bmp Decoded

💻 Sample Console Output
✅ Encoding
======================================== 🔐  Steganography using LSB Technique========================================🔒 Selected Encoding Operation-> Encode arguments validated successfully.======================================== 🔐 Starting Encoding Process========================================-> Step 1: Opened required files successfully.-> Step 2: Source image has sufficient capacity.-> Step 3: BMP header copied successfully.-> Step 4: Magic string encoded successfully.-> Step 5: Secret file extension size encoded successfully.-> Step 6: Secret file extension encoded successfully.-> Step 7: Secret file size encoded successfully.-> Step 8: Secret file data encoded successfully.-> Step 9: Remaining image data copied successfully.✅ Encoding completed successfully!📁 Output file generated: destination.bmp========================================

✅ Decoding
======================================== 🔐  Steganography using LSB Technique========================================🔓 Selected decoding operation.-> Decode arguments validated successfully.======================================== 🔓 Starting Decoding Process========================================-> Step 1: Secret file extension size decoded successfully.-> Step 2: Secret file extension decoded successfully.-> Step 3: Secret file size decoded successfully.-> Step 4: Secret file data decoded successfully.✅ Decoding completed successfully!📁 Output file generated: Decoded.txt========================================

🧱 Compilation
gcc main.c encode.c decode.c -o stego

🚀 Future Enhancements


🔐 Add password or encryption for secure encoding


🖼️ Support PNG/JPG formats


🖥️ Develop GUI (Qt/GTK)


📦 Enable batch processing


✔️ Add checksum for data integrity



👨‍💻 Author
Suraj Zure
📍 Bengaluru, Karnataka, India
💡 Aspiring Embedded Systems
