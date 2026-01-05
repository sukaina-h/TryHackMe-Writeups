# John the Ripper – Basics (TryHackMe)

## Overview

**John the Ripper** is a powerful and adaptable hash-cracking tool that combines high speed with support for many different hash types.  
The **Jumbo John** version is the most popular extended edition, adding more formats and advanced capabilities — this is the version I used.

John supports:
- Wordlist (dictionary) attacks
- Limited automatic hash-type detection (not always reliable)

---

## Basic Cryptography Concepts

Before moving into practical hash cracking, I reviewed some important cryptography terms.

### Hashes

A **hash** is a fixed-length representation of data generated from input of any length using a hashing algorithm such as:
- MD5
- SHA1
- SHA256

To generate a hash, the original data is passed through a hashing algorithm.

### What Makes Hashes Secure?

- Hashes are **one-way functions**
- Easy to compute: `input → hash`
- Extremely difficult to reverse: `hash → original input`

This is why hashes are commonly used to store passwords — although weak passwords can still be cracked.

---

## How Hashes Are Attacked

### Dictionary Attacks

If you know:
- The hashed password
- The hashing algorithm

You can:
1. Hash a large list of common passwords (a **wordlist**)
2. Compare generated hashes to the target hash
3. If a match is found, the password is cracked

This is the core idea behind dictionary attacks, which tools like John the Ripper automate and accelerate.

### Brute-Force Attacks

- Tries every possible character combination
- Slower than dictionary attacks
- Used when no wordlist match exists

---

## Tools Used

For the practical tasks, I used:
- **John the Ripper (Jumbo version)**
- **rockyou.txt** wordlist

---

## John the Ripper Basics

### Basic Syntax

``bash
john [options] [file_path]
#### Where:
- john → launches John the Ripper
- [options] → cracking options
- [file_path] → file containing the hash(es)

---

## Automatic Hash Cracking
- John can attempt to automatically detect the hash type and choose cracking rules.
- This can be useful, but it is not always reliable.
### Wordlist Mode Syntax
- *john --wordlist=[path_to_wordlist] [path_to_hash_file]*
- Example: *john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt*

---

## Identifying Hash Types
Because John’s auto-detection can fail, it’s often better to identify the hash manually using tools such as:
- hash-identifier
- hashes.com

Once identified, you can explicitly specify the hash format.

---

## Using --format
- Syntax: *john --format=[format] --wordlist=[path_to_wordlist] [path_to_hash_file]*
- Example (MD5): *john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt*

### Notes on Formats and raw-
- John must know the exact hash format
- raw- is used for standalone hash strings (not system password files)
#### Examples:
- raw-md5
- raw-sha1
  
- raw- is not always required, depending on how John interprets the input

---

## Cracking Windows Authentication Hashes

### NTLM / NTHash
- NTLM (NT Hash) is used by modern Windows systems
- User account information is stored in the SAM (Security Account Manager) database
- Hashes can be extracted using tools like:
  - mimikatz
  - NTDS.dit

### What Can You Do With a Hash?
1. Pass-the-Hash
    - Authenticate using the hash directly
    - No need to crack the password
2. Crack the Hash
    - Recover plaintext passwords
    - Useful if password policies are weak

---

## NTLM Cracking Syntax in John
- john --format=NT --wordlist=[path_to_wordlist] [path_to_hash_file]

---

## Practical Tasks Completed
- I worked through several cracking exercises and really enjoyed the hands-on aspect.

### Hash Cracking Questions
1. What type of hash is hash1.txt?
Identified using hash-identifier

2. What is the cracked value of hash1.txt?
Cracked using John the Ripper

3. What type of hash is hash2.txt?
Identified using a hash-identifier

4. What is the cracked value of hash2.txt?
Cracked using John the Ripper

5. What type of hash is hash3.txt?
Identified using a hash-identifier

6. What is the cracked value of hash3.txt?
Cracked using John the Ripper

7. What type of hash is hash4.txt?
Identified using a hash-identifier

8. What is the cracked value of hash4.txt?
Cracked using John the Ripper

---

## Windows Hash Cracking Task
1. What do we set --format to?
--format=NT
2. What is the cracked value of the password in ntlm.txt?
Cracked using John the Ripper with the NT format.

---

## Key Takeaways
- Always identify hash types before cracking
- Use --format when auto-detection fails
- Wordlist attacks are fast and effective for weak passwords
- NTLM hashes are common in Windows environments
- Hands-on practice greatly improves understanding
