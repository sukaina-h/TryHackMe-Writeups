# 🔢 Hashing Basics: Data Integrity & Password Security

This repository documents my technical study of cryptographic hash functions. It covers the difference between hashing, encoding, and encryption, the mechanics of secure password storage, and practical techniques for integrity checking and hash cracking.

---

## 🏗️ 1. Fundamentals of Hash Functions
A **Hash Function** takes an input of arbitrary size and transforms it into a fixed-length string (a "digest").

### Key Properties:
* **One-Way:** It is computationally infeasible to reverse a hash to retrieve the plaintext.
* **Deterministic:** The same input will always produce the exact same hash.
* **Avalanche Effect:** A change of even a single bit in the input results in a radically different hash.
* **Collision Resistance:** It is difficult to find two different inputs that produce the same hash value.



### Common Algorithms
| Algorithm | Digest Size | Security Status |
| :--- | :--- | :--- |
| **MD5** | 128 bits (16 bytes) | **Insecure** (Collision vulnerabilities) |
| **SHA-1** | 160 bits (20 bytes) | **Insecure** |
| **SHA-256** | 256 bits (32 bytes) | **Secure** (Industry Standard) |
| **SHA-512** | 512 bits (64 bytes) | **Very Secure** |

---

## 🛡️ 2. Secure Password Storage
Storing passwords in plaintext is a critical security failure. Modern systems use salted hashes to protect user credentials.

### Protecting Against Rainbow Tables
**Rainbow Tables** are precomputed lookup tables of hashes. Attackers use them to "reverse" hashes instantly. We defeat them using **Salts**:
* **Salt:** A unique, random string added to the password before hashing.
* **Effect:** Even if two users have the same password, their hashes will be different, rendering precomputed tables useless.

### Secure Storage Workflow:
1.  Select a secure, slow algorithm (e.g., **Bcrypt**, **Scrypt**, or **Argon2**).
2.  Generate a unique salt for the user.
3.  Concatenate password + salt and hash the result.
4.  Store both the Salt and the Hash in the database.

---

## 🔎 3. Recognizing & Cracking Hashes
Identifying the hash type is the first step in offensive security.

### Linux Password Hashes (`/etc/shadow`)
Linux uses specific prefixes to identify the algorithm:
* `$1$`: MD5
* `$5$`: SHA-256
* `$6$`: SHA-512
* `$y$`: **yescrypt** (Modern default)
* `$2a$`: **Bcrypt**



### Cracking Tools
* **Hashcat:** Powerful GPU-based cracker. Uses "modes" (e.g., `-m 1000` for NTLM, `-m 3200` for Bcrypt).
* **John the Ripper:** Versatile CPU-based cracker.
* **Online Tools:** CrackStation and Hashes.com (Useful for unsalted, common hashes).

---

## 🛠️ 4. Practical Lab Achievements

### Hash Identification & Cracking
* **Bcrypt:** Cracked `$2a$06$...` to find password: `85208520`.
* **SHA-256:** Cracked `9eb7ee...` to find password: `halloween`.
* **SHA-512 (Unix):** Cracked `$6$GQXV...` to find password: `spaceman`.
* **MD5:** Cracked `b6b0d4...` to find password: `funforyou`.

### Integrity & Encoding
* **Integrity Check:** Verified the integrity of `libgcrypt-1.11.0.tar.bz2` using `sha256sum`.
* **Base64 Decoding:** Decoded `RU5jb2RlREVjb2RlCg==` to reveal the plaintext: `ENcodeDEcode`.

---

## 📉 5. Integrity & HMACs
Hashing ensures that files remain unchanged during transit.

### HMAC (Keyed-Hash Message Authentication Code)
HMAC provides both **Integrity** and **Authenticity** by combining a hash function with a secret key.
* **Formula:** $HMAC(K,M) = H((K \oplus opad) || H((K \oplus ipad) || M))$
* It proves that the message was not modified and that the sender possesses the secret key.



---

## 🔄 6. Hashing vs. Encoding vs. Encryption
| Feature | Hashing | Encoding | Encryption |
| :--- | :--- | :--- | :--- |
| **Purpose** | Integrity / Passwords | Compatibility | Confidentiality |
| **Reversible?** | **No** (One-Way) | **Yes** (Public) | **Yes** (Requires Key) |
| **Output** | Fixed Length | Variable Length | Variable Length |

---
*Learning documented as part of a Cybersecurity journey | Concepts via TryHackMe*
