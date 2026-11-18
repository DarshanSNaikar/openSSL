# OpenSSL Cryptographic Toolkit — CNS Laboratory Demonstration Manual

**Course**: Cryptography & Network Security (CNS) Laboratory  
**Demonstration Web Application**: [openssl_cns_lab_demonstration.html](file:///d:/Major%20Project/Capstone-Project-Explainable-allele-Pathogenicty-classification-with-contextual-insights/openssl_cns_lab_demonstration.html)  
**Artifact Link**: [openssl_cns_lab_demonstration.html](file:///C:/Users/DARSHAN/.gemini/antigravity/brain/043c61d6-873c-4864-9802-f81e69e22bac/openssl_cns_lab_demonstration.html)

---

## 1. Laboratory Objectives
1. Understand the architecture, command-line interface, and execution pipeline of **OpenSSL**.
2. Visually demonstrate **Symmetric Encryption (AES-256-CBC)** and observe key-dependent decryption and padding failure on invalid keys.
3. Understand **Cryptographic Hash Functions (SHA-256)**, prove pre-image resistance (one-way property), and demonstrate the **Avalanche Effect**.
4. Generate **Asymmetric RSA-2048 Keypairs**, inspect the mathematical primes ($p, q$), modulus ($n$), public exponent ($e$), and private exponent ($d$).
5. Demonstrate **Digital Signatures** for authenticity and non-repudiation, and prove how any message tampering triggers verification failure.
6. Master actual **OpenSSL CLI commands** in a Windows Command Prompt environment.
7. Map all operations to the **CIA Triad** (Confidentiality, Integrity, Availability / Authenticity).

---

## 2. OpenSSL Execution Pipeline Flowchart

```
USER INPUT (File / Data + Options)
       ↓
OPENSSL COMMAND-LINE INTERFACE (CLI Parser & Validation)
       ↓
COMMAND PROCESSING (EVP High-Level Subsystem Initialization)
       ↓
ALGORITHM SELECTION (EVP_CIPHER / EVP_MD: AES, RSA, SHA-256)
       ↓
CRYPTOGRAPHIC PROCESSING (Hardware Acceleration via AES-NI / AVX)
       ↓
FINAL OUTPUT (Ciphertext / 64-char Hash / PEM Key Containers)
```

---

## 3. Core OpenSSL Commands Demonstrated

| # | Cryptographic Operation | OpenSSL Terminal Command | Security Goal |
|---|-------------------------|--------------------------|---------------|
| 1 | Check Toolkit Version | `openssl version` | System Audit |
| 2 | Compute SHA-256 Digest | `openssl dgst -sha256 message.txt` | **Integrity** |
| 3 | Encrypt with AES-256-CBC | `openssl enc -aes-256-cbc -salt -pbkdf2 -in message.txt -out encrypted.txt` | **Confidentiality** |
| 4 | Decrypt with AES-256-CBC | `openssl enc -aes-256-cbc -d -pbkdf2 -in encrypted.txt -out decrypted.txt` | **Confidentiality** |
| 5 | Generate RSA-2048 Private Key | `openssl genrsa -out private.pem 2048` | Key Generation |
| 6 | Extract RSA Public Key | `openssl rsa -in private.pem -pubout -out public.pem` | Asymmetric Setup |
| 7 | Generate Digital Signature | `openssl dgst -sha256 -sign private.pem -out signature.bin message.txt` | **Authenticity** |
| 8 | Verify Digital Signature | `openssl dgst -sha256 -verify public.pem -signature signature.bin message.txt` | **Non-Repudiation** |

---

## 4. Viva / Faculty Presentation Talking Points

### Q1: Why does OpenSSL use `-salt` and `-pbkdf2` in AES encryption?
> **Answer**: A passphrase provided by a human does not have 256 bits of entropy. OpenSSL uses **PBKDF2** (Password-Based Key Derivation Function 2) to hash the passphrase alongside a cryptographically random 8-byte salt across tens of thousands of rounds. The salt ensures that identical passwords yield different ciphertexts, preventing rainbow table attacks.

### Q2: What is the Avalanche Effect in SHA-256?
> **Answer**: The avalanche effect is a desirable property of cryptographic hash functions where a minimal change in the input (such as flipping a single bit or changing a comma to a period) results in a radical, uncorrelated change in the output digest (>50% of the bits flip).

### Q3: Why can't a SHA-256 hash be decrypted?
> **Answer**: Hashing is a **one-way function (pre-image resistant)**. It condenses an arbitrary-length message into a fixed 256-bit space. Because an infinite number of messages could map to the same 256-bit space (pigeonhole principle), and mathematical compression operations (e.g. bitwise XOR, shifts, modulo additions) discard information, no inverse key or reverse formula exists.

### Q4: What is the relationship between the RSA Private Key and Public Key?
> **Answer**: 
> 1. Two large primes $p$ and $q$ are chosen.
> 2. The modulus $n = p \times q$ is computed (e.g., 2048 bits long).
> 3. Euler's totient is calculated: $\phi(n) = (p-1)(q-1)$.
> 4. The public exponent $e$ (typically $65537$) is chosen such that $\gcd(e, \phi(n)) = 1$.
> 5. The private exponent $d$ is derived as the modular multiplicative inverse: $d \equiv e^{-1} \pmod{\phi(n)}$.
> 
> The **Public Key** contains $(n, e)$ and can be distributed openly.  
> The **Private Key** contains $(n, d, p, q)$ and must remain strictly confidential.

### Q5: How does a Digital Signature prove both Integrity and Authenticity?
> **Answer**: 
> 1. **Authenticity**: Only the sender holds the unique private key that generated the signature.
> 2. **Integrity**: If an attacker alters the message in transit, the recomputed SHA-256 hash at the receiver will fail to match the hash decrypted using the sender's public key, throwing an immediate verification error.

---

## 5. How to Run the Website for the Demonstration

1. Double-click the file [openssl_cns_lab_demonstration.html](file:///d:/Major%20Project/Capstone-Project-Explainable-allele-Pathogenicty-classification-with-contextual-insights/openssl_cns_lab_demonstration.html) in your file manager, or open it in any modern browser (Chrome, Edge, Firefox).
2. Click **"▶ Start Guided Demo"** in the top control bar to take the faculty member through the step-by-step automated tour, or manually click on any module to run live experiments:
   - Test live AES encryption and wrong password error.
   - Click **"⚡ Change 1 Character (Avalanche Demo)"** to demonstrate SHA-256 bit changes.
   - Click **"⚡ Compute & Generate New RSA Key Pair"** to inspect PEM cards.
   - Click **"⚠️ Tamper Transmitted Message & Re-Verify"** to show signature validation failure.
   - Click command buttons in the **Windows Command Prompt** terminal simulator.
