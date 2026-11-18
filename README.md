# OpenSSL – Cryptographic Toolkit
### Visual Demonstration of Cryptographic Operations for Network Security

An interactive, animated educational web application demonstrating the core working flow of **OpenSSL (Open Secure Sockets Layer)** for Cryptography and Network Security (CNS) laboratory presentations.

🌐 **Live GitHub Pages URL**: [https://darshansnaikar.github.io/openSSL/](https://darshansnaikar.github.io/openSSL/)  
*(To activate, go to Repo Settings -> Pages -> Deploy from branch: `main`)*

---

## 🚀 Key Features & Modules

1. **Host-to-Host Secure Tunnel Visualization**:
   - Animated TLS 1.3 encrypted data channel with dynamic packets and security status.
2. **Complete 6-Stage OpenSSL Workflow**:
   - `User Input` ➔ `CLI Parser` ➔ `Command Processing` ➔ `Algorithm Selection` ➔ `Cryptographic Processing` ➔ `Final Output`.
3. **AES-256-CBC Encryption & Decryption (Confidentiality)**:
   - Interactive message encryption into salted ciphertext (`Salted__` container).
   - Password recovery and simulated `bad decrypt` padding error on wrong password.
4. **SHA-256 Hashing & The Avalanche Effect (Integrity)**:
   - Real-time in-browser hashing using native **Web Crypto API**.
   - 1-character tamper simulation demonstrating >50% bit flip across the 256-bit digest.
5. **RSA-2048 Asymmetric Key Generation**:
   - Mathematical prime selection ($p, q$), modulus $n = p \times q$, public exponent $e = 65537$, and private exponent $d$.
   - Distinct cards for `SECRET` Private Key and `SHAREABLE` Public Key.
6. **Digital Signatures & Verification (Authenticity & Non-Repudiation)**:
   - SHA-256 hashing + Private Key signing.
   - Public Key verification showing `VERIFIED OK` for authentic documents and `VERIFICATION FAILED` on tampered payloads.
7. **Interactive Windows Command Prompt Terminal Simulator**:
   - Simulated `cmd.exe` environment executing 8 standard OpenSSL CLI commands:
     - `openssl version`
     - `openssl dgst -sha256 message.txt`
     - `openssl enc -aes-256-cbc -salt -pbkdf2 -in message.txt -out encrypted.txt`
     - `openssl enc -aes-256-cbc -d -pbkdf2 -in encrypted.txt -out decrypted.txt`
     - `openssl genrsa -out private.pem 2048`
     - `openssl rsa -in private.pem -pubout -out public.pem`
     - `openssl dgst -sha256 -sign private.pem -out signature.bin message.txt`
     - `openssl dgst -sha256 -verify public.pem -signature signature.bin message.txt`
8. **Real-World Applications & The CIA Triad**:
   - HTTPS, SSH/SFTP, SSL/TLS Certificates, At-Rest Encryption, Code Signing, and CSPRNG Key Exchange.
   - Mapping AES ➔ Confidentiality, SHA-256 ➔ Integrity, RSA Signature ➔ Authenticity.

---

## 🛠️ How to Run Locally

### Option 1: Direct File Open
Double click `index.html` to open it in Google Chrome, Microsoft Edge, or Mozilla Firefox.

### Option 2: Local HTTP Server
Run with Python:
```bash
python -m http.server 8080
```
Then navigate to: `http://localhost:8080`

---

## 📚 Companion Guide
For complete lab viva questions, detailed mathematical breakdowns, and presentation talking points, see [CNS_Lab_OpenSSL_Demonstration_Guide.md](./CNS_Lab_OpenSSL_Demonstration_Guide.md).
