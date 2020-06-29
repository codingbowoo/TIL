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
    - Hill Cipher : ```C_m = P_1*k_1m + ... + P_i*k_im + ...+ P_m*k_mm``` (```m```: size of the block )
        - plaintext divided into equal-size blocks
        - Each clock is encrytped one at a time
        - multiplicative inverse for the key matrix needed
        - frequency analysis disabled, known-plaintext attack available if the value ```m``` and plaintext/cipher text pairs are known.
    - One-Time Pad
        - "perfect secrecy can be achieved if each plaintext symbol is encrypted with a key randomly chosen from a key domain"
        - key length = plaintext length
        - key chosen in complete random

## Transposition Ciphers
**changes the location of the symbols/ reorders symbols** <br>
**vulnerable to several ciphertext-only attacks**(e.g. statistical attack(frequency), brute-force attack)
- Keyless Transposition Ciphers
    - written into a table 1) column by column and transmitted row by row 2) row by row and transmitted column by column
- Keyed Transposition Ciphers
    - permutation is done on the whold plaintxt to create the whole ciphertext
    - key used for encryption and decryption (matrices can be used as a representation of the key)
- Combining Two Approaches
    - Double transposition cipher(e.g. (Plaintext) -> write row by row -> permute columns -> read col by col -> (Middle-text) -> write row by row -> permute columns -> read column by column -> ciphertext)

## Stream and Block Ciphers
**Two categoris of the traditional symmetric ciphers: stream ciphers and block ciphers**
- Stream Ciphers: encryption and decryption are done one symbol at a time 
    - P(plaintext), C(ciphertext), K(key stream)
    - key stream might diverse: 1) predetermined 2) depend on P/C/previous key values
    - additive ciphers(monoalphabetic), monoalphabetic substitution ciphers, vigenere ciphers(polyalphabetic) 
- Block Ciphers: a group of P symbols of size m are encrypted together creating a grounp of ciphertext of the same size
    - a single key is used to encrypt the whole block
    - Hill ciphers 
- Combination: "blocks of plaintext are encrypted individually but using a stream of keys to encrypt the whole message block by block"

