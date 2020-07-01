# Mathematics of Cryptography

    prime numbers, primality test algorithms, factorization algorithms, 
    Chinese remainder theorem, quadratic congruence, modular exponentiation and logarithm
    
    
## Primes
- **prime**, **composite**, **coprime(relatively prime)**
- cardinality
- checking primality
- Euler's Phi-Function: finds the numver of integers that are smaller than n and relatively prime to n
- Fermat's Little Therem: If p is prime and a is an integer, 1) a^(p-1) &equiv; 1 (mod p) 2) a^p &equiv; a (mod p)
- Euler's Therorem: Fermat's little theorem w/o the condition taht a and n should be coprime
- Generating Primes: mersenne primes, fermat primes

## Primality Testing
- Deterministic Algorithms
    - Divisibility Algorithm
- Probabilistic Algorithms
    - Fermat Test
    - Square Root Test
    - Miller-Rabin Test : ```n-1 = m * 2^k```, finding a strong pseudoprime
    
## Factorization
**security of several public-key cryptosystems**
- Greatest Common Divisor
- Least Common Multiplier
- Trial Division Method
- Fermat MethodPollard rho Method

## Chinese Remainder Theorem
**solve a set of songruent equations with one variable but different moduli(relatively prime)**
- solution
    1. Find common modulus M = m1 * m2 * ... * mk 
    2. Find M1 = M/m1, M2 = M/m2, ..., Mk = M/mk
    3. Dinf the multiplicative inverse of M1, ..., Mk using the corresponding moduli
    4. The solution: ```x = (a1*M1*inv(M1) + a2*M2*inv(M2) + ... + ak*Mk*inv(Mk)) mod M```
    
## Quadratic Congruence
**x^2 &equiv; a (mod n)**
- ```a```: quadratic residue(QR) if the equation has two solutions
- ```a```: quadratic nonresidue(QNR) if the equation has no solutions

<br>

- Euler's Criterion: **a^((p-1)/2) &equiv; 1 (mod p)** -> QR, **a^((p-1)/2) &equiv; -1 (mod p)** -> QNR
- Quadratic Congruence Modulo a Composite
- complexity: **solving a quadratic congruence modulo a composite is as hard as factorization of the modulus**

## Exponentiation and Logarithm
