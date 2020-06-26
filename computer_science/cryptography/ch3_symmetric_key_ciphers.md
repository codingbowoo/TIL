# Traditional Symmetric-Key Ciphers

## Introduction
- **symmetric-key cipher**: **```Shared secret key```**, ```Encryption/Decryption algorithm```, ```Secure key-exchange channel```
- Kerckhoff's Principle: Always assume that the adversary know the enc/decryption algorithm -> **```the secrecy of the key```** matters
- Cryptanalysis
    - Ciphertext-only attack: brute-force(exhaustive-key-search) attack, statistical attack, pattern attack
    - Known-plaintext attack
    - Chosen-plaintext attack
    - Chosen-ciphertext attack

## Substitution Ciphers
**Replaces one symbol with another**
- Monoalphabetic Ciphers: the relationship is always one-to-one
    - Additive cipher, Shift cipher, Caesar cipher: ```C = (P+k) mod 26``` (**C**ipher,  **P**laintext, **k**ey)
    - Multiplicative ciphers: ```C = (P*k) mod 26```
        - plaintext and ciphertext are int in Z_26
        - the key is an int in Z_26*(multiplicative inverse가 있는 집합)
    - Affine ciphers: ```C = (P*k_1 + k_2) mod 26```
        - ```k_1``` is from Z_26*(multiplicative inverse가 있는 집합)
        - ```k_2``` is from Z_26
    - Monoalphabetic Substitution Cipher
        - ciphers above are vulnerable to brute-force attack; therefore create a mapping between each P and C
- Polyalphabetic Ciphers: relationship between a character in the P to C is one-to-many
    - Autokey Cipher: ```C_i = (P_i _ k_i) mod 26 ```
        - hides the single-letter frequency statistics of the P
        - ciphers vulnerable to a brute-force attack since the size of the key space is only 25
    - Vigenere Cipher: ```C_i = P_i + k_i```
        - depend only on the position of the character in P
        - vulnerable to the use Kasiski test(searches for repeated text segments) to find the key length & brute-force
    - Hill Cipher
    - One-Time Pad
    - Rotor Cipher

## Transposition Ciphers
- Keyless Transposition Ciphers
- Keyed Transposition Ciphers
- Combining Two Approaches

## Stream and Block Ciphers
- Stream Ciphers
- Block Ciphers
- Combination

