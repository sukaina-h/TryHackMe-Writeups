# 🔐 Cryptography Fundamentals: Principles & Algorithms

This repository contains my technical notes on the core pillars of cryptography. It covers the evolution from historical ciphers to modern symmetric and asymmetric standards, as well as the mathematical logic that powers secure communication.

---

## 🏗️ 1. Core Principles
Cryptography ensures that communication remains secure even in the presence of adversaries. It addresses three critical security requirements:
1. **Confidentiality:** Preventing unauthorized disclosure of data.
2. **Integrity:** Ensuring data has not been altered.
3. **Authenticity:** Verifying the identity of the sender.

### Key Terminology
| Term | Definition |
| :--- | :--- |
| **Plaintext** | The original, readable message. |
| **Ciphertext** | The encrypted, unreadable version of the message. |
| **Cipher** | The algorithm used to perform encryption and decryption. |
| **Key** | A secret bit string used by the cipher to transform the data. |

---

## 📜 2. Historical Ciphers
Early cryptography relied on simple substitution and transposition.

### Caesar Cipher
A substitution cipher where each letter in the plaintext is shifted by a fixed number of positions down the alphabet.
* **Mechanism:** If the key is 3, 'A' becomes 'D'.
* **Weakness:** With only 25 possible keys (rotations), it is highly vulnerable to **Brute Force** attacks.



---

## 🔑 3. Modern Encryption Standards

### Symmetric Encryption (Private Key)
Uses a **single secret key** for both encryption and decryption.
* **Pros:** Extremely fast and efficient for bulk data.
* **Cons:** Safe key distribution is a major challenge.
* **Standards:**
    * **AES (Advanced Encryption Standard):** The gold standard today. Uses 128, 192, or 256-bit keys.
    * **3DES:** An older method that applies the Data Encryption Standard (DES) three times. Now deprecated.



### Asymmetric Encryption (Public Key)
Uses a **Key Pair**: a **Public Key** (can be shared with anyone) and a **Private Key** (must be kept secret).
* **Mechanism:** Data encrypted with the Public Key can *only* be decrypted by the corresponding Private Key.
* **Pros:** Solves the key distribution problem.
* **Standards:**
    * **RSA:** Relies on the difficulty of factoring large prime numbers.
    * **ECC (Elliptic Curve Cryptography):** Offers the same security as RSA but with much smaller keys (e.g., 256-bit ECC is as strong as 3072-bit RSA).

---

## 🧮 4. Mathematical Building Blocks
Modern algorithms are built on two primary operations:

### XOR Operation ($\oplus$)
Exclusive OR compares bits. It returns `1` if the bits are different and `0` if they are the same.
* **Crucial Property:** XOR is its own inverse. 
* If $Plaintext \oplus Key = Ciphertext$, 
* then $Ciphertext \oplus Key = Plaintext$.

| A | B | A $\oplus$ B |
|:-:|:-:|:------------:|
| 0 | 0 | 0            |
| 0 | 1 | 1            |
| 1 | 0 | 1            |
| 1 | 1 | 0            |

### Modulo Operation ($\%$)
The modulo operator finds the **remainder** after division.
* **Example:** $23 \pmod 6 = 5$ (Because $23 = 6 \times 3 + 5$).
* **Significance:** It is a "one-way" function. You cannot easily reverse a modulo operation to find the original value, which is essential for algorithms like RSA.

---

## 🛡️ 5. Compliance & Practical Use
Cryptography is often mandated by law to protect sensitive information:
* **PCI DSS:** Standards for securing credit card transactions.
* **HIPAA/GDPR:** Regulations for protecting healthcare and personal data.
* **At Rest vs. In Motion:** Data must be encrypted while stored on a disk (at rest) and while traveling over a network (in motion/transit).

---
*Learning documented as part of a Cybersecurity journey.*
