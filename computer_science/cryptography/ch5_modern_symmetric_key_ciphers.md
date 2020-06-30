# Introduction to Modern Symmetric-key Ciphers

**traditional ciphers: character-oriented**<br>
**modern ciphers: bit-oriented**

## Modern Block Ciphers
- encrypts an n-bit block of P/ decrypts an n-bit block of C using a ```k-bit key```
- designed as a **substitution cipher** since transposition makes the cipher vulnerable to brute-force attacks
- Block Ciphers as Permutation Groups
    - key should be long enough to choose every possible mapping from the input to output
    - Full Size key Ciphers: n! possible keys with ceil(log_2```n!```) bits
        - full-size key **substitution**(not a transposition!) block ciphers
        - transforming an n-bit int into a 2^n-bit string with **only a single 1 and ```2^n```-1 0's
    - Transposition: the key is ```ceil(log_2 n!)``` bits long
    - Substitution: the key is ```ceil(log_2 (2^n)!)``` bits long
- Components of a Modern Block cipher
    - transposition units (P-boxes; p for permutation): compression P-boxes, Expansion P-boxes
    - substitution units (S-boxes; m\*n substitution unit, m!=n): Linear vs Nonlinear S-boxes
    - Exclusive-OR: addition and subtraction operations in the GF(2^n) field 
    - Circular shift: shifting modulo n
    - Swap: special case of the circualr shift operation where ```k=n/2``` (self-invertible)
    - Split and Combine 
- Product Ciphers: complex cipher combining substitution, permutation and other components discussed in previous sections
    - **diffusion**: hide the relationship btwn the C and P (each symbol in C is dependent on some or all symbols in the P) 
    - **confusion**: hide the relationship btwn the C and the key (if a sisngle bit in the key is changed, most or all bits in the C will also be changed )
    <br>
    - Two Classes of Product Ciphers
        - Feistel ciphers (e.g. DES): self-invertible(mixer), invertible, and noninvertible.
        - non-Feistel ciphers (e.g. AES): only invertible components(key mixer)
- Attacks on Block Ciphers <FIND ALICES"S CIPHER KEY>
     - Differential Cryptanalysis: chosen-plaintext attacks
     - Linear Crytanalysis: known-olaintext attacks
     - Linear Approximation
     
     
    


## Modern Stream Ciphers
