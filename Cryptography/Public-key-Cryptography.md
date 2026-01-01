# Public Key Cryptography: Asymmetric Encryption & PKI

This repository documents my technical study of Asymmetric Cryptography. It covers the transition from shared secrets to key-pair infrastructure, the mathematical logic of RSA and Diffie-Hellman, and the practical implementation of SSH and GPG.

---

## 🏦 1. The Core Concept: Key Exchange
Asymmetric encryption solves the "Key Exchange Problem." Unlike symmetric encryption, where the same key must be shared secretly, asymmetric encryption allows two parties to agree on a secret over an insecure channel.

### The Lock & Key Analogy
Imagine you want to send a secret to a friend:
1. **Public Key (The Lock):** Your friend sends you an open, indestructible lock. Anyone can see it, but only your friend has the key.
2. **Encryption:** You put your message in a box and snap the lock shut.
3. **Private Key (The Key):** Your friend receives the box and uses their private key to open it.



---

## 🔢 2. RSA (Rivest-Shamir-Adleman)
RSA is based on the mathematical difficulty of factoring the product of two large prime numbers.

### Key Variables & Calculations:
* **$p, q$**: Large prime numbers.
* **$n$**: The modulus ($n = p \times q$).
* **$\phi(n)$**: Euler’s Totient ($\phi(n) = (p-1) \times (q-1)$).
* **Public Key ($e, n$)**: Shared for encryption.
* **Private Key ($d, n$)**: Kept secret for decryption.


**Lab Practice:**
* For $p = 4391$ and $q = 6659$:
  * **$n$** = $29,239,669$
  * **$\phi(n)$** = $29,228,620$

---

## 🤝 3. Diffie-Hellman (DH) Key Exchange
Diffie-Hellman allows two parties to establish a **shared secret** over an untrusted network without prior communication.

### The Process:
1. Parties agree on a prime $p$ and a generator $g$.
2. Alice chooses private $a$; calculates public $A = g^a \pmod p$.
3. Bob chooses private $b$; calculates public $B = g^b \pmod p$.
4. They exchange $A$ and $B$.
5. **Shared Secret:** $Key = B^a \pmod p$ (calculated by Alice) and $Key = A^b \pmod p$ (calculated by Bob). Both reach the same result.



---

## 4. SSH (Secure Shell)
SSH uses asymmetric keys to provide secure remote access. 

### Key Algorithms
* **RSA**: Standard legacy algorithm.
* **ED25519**: Modern Edwards-curve Digital Signature Algorithm (Fast and Secure).
* **ECDSA**: Uses Elliptic Curves for smaller key sizes.

---

## 5. Digital Signatures
A digital signature is used to verify the **authenticity** and **integrity** of a message. It ensures that the sender is who they claim to be and that the content has not been altered.

### How it Works:
1. **Signing:** The sender creates a hash of the message and encrypts it with their **Private Key**.
2. **Verification:** The receiver decrypts the signature using the sender's **Public Key** and compares the resulting hash with a fresh hash of the received message.



---

## 6. Certificates & TLS
Certificates are used to verify the identity of web servers. They prevent Man-in-the-Middle (MITM) attacks by establishing a "Chain of Trust."

* **Proof of Identity:** A remote web server uses a **Certificate** to prove itself to the client.
* **Certificate Authorities (CA):** Trusted entities that sign and issue certificates.
* **Let's Encrypt:** A free, automated, and open Certificate Authority used to obtain TLS certificates for modern websites.

---

## 7. PGP & GPG (Pretty Good Privacy)
**PGP** (Pretty Good Privacy) is a methodology for encrypting and signing data. **GPG** (GnuPG) is the open-source implementation of the OpenPGP standard.

### Core Functions:
* **Confidentiality:** Encrypting files so only the recipient with the private key can read them.
* **Integrity:** Signing files to ensure they haven't been tampered with.
* **Key Management:** Generating, importing, and exporting public/private key pairs.

### Common GPG Key Algorithms:
* **RSA:** Widely used for both signing and encryption.
* **DSA:** Specifically designed for digital signatures.
* **ECC (Elliptic Curve):** Modern standard (e.g., Curve 25519) for high security with small keys.

---

## 4. Practical Lab Workflow
Below are the commands and steps used to handle encrypted files and keys in a Linux environment.

### Generating a Key
When generating a key with `gpg --full-gen-key`, we define:
* **The Purpose:** (Sign only, or Sign and Encrypt).
* **The Algorithm:** (e.g., ECC Curve 25519 or RSA).
* **Expiry Date:** How long the key remains valid.
* **User ID:** Name and email address associated with the key.

### Decrypting Evidence
During the lab, I performed the following steps to recover a secret message:

1. **Import the Private Key:**
   ```bash
   gpg --import ~/Public-Crypto-Basics/Task-7/tryhackme.key

1. **Decrpt the Private message:**
   ```bash
   gpg --decrypt ~/Public-Crypto-Basics/Task-7/message.gpg

### Essential CLI Commands
```bash
# Generate a key pair
ssh-keygen -t ed25519

# Inspect a private key's algorithm
ssh-keygen -l -f ~/path/to/key

# Login using a specific key
ssh -i private_key_file user@target_ip

# Generate a key pair
ssh-keygen -t ed25519

# Inspect a private key's algorithm
ssh-keygen -l -f ~/path/to/key

# Login using a specific key
ssh -i private_key_file user@target_ip
