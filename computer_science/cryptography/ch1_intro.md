# Introduction

## Security Goals
- **Confidentiality** (Protecting confidential informtaion)
    - Snooping, Traffic analysis
- **Integrity** (Information to be changed constantly, change only made by authorized entities & mechanisms)
    - Modification, Masquerading, Replaying, Repudiation(sender of receiver later deny that she has sent/received the message)
- **Availability** (Information should be available to authorized entities)
    - Denial of service
    
## Services and Mechanisms
### Security Services
- Data confidentiality
- Data Integrity: Anti-change, Anti-replay
- Authentication: Peer entity, Data origin
- Nonrepudation: Proof of origin, Proof of delivery
- Access control

### Security Mechanisms
- Encipherment: hiding/covering data (confidentiality: cryptography/steganography)
- Data integrity: a short checkvalue created from the data itself
- Digital signature: the sendes/receiver can electronically sign/verify the signature
- Authentication exchange: two entities exchange messages for identification
- Traffic padding: insert some fake data to invalidate traffic analysis
- Routing control
- Notarization: set third party control center
- Access control: passwords, PINs

## Techniques
### Cryptography
- "secret writing"
- Encryption/Decryption: conceal the contents of a message by enciphering
- Symmetric encipherment: single secret key
- Asymmetric encipherment: one public key & one private key
- Hashing: from variable-length to fixed-length message

### Steganography
- "covered writing"
- "conceling the message itself by covering it with something else"
