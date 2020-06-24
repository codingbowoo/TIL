# Chapter 2 Mathematics of Cryptography: Modular Arithmetric, Congruence, and Matrices

## 2.1 Integer arithmetic
- **set** as a background for modular arithmetic
- Binary Operation: two inputs & one ouput ```a (operation e.g. +, -, *) b = c```
- Integer Division : ```a = q * n + r```
    - a: dividend
    - n: divisor (must be a positive number)
    - q: quotient
    - r: remainder (must be a nonnegative number)
- Divisibility: if r = 0, ```n|a```
    - Greatest Common Divisor(GCD)
    - Euclidean Algorithm
        - gcd(a, 0) = a
        - gcd(a, b) = gcd(b,r) where r is the remainder of dividing a by b
        - gcd(a, b) = 1 : a and b are **relatively prime**
    - Extended Euclidean Algorithm
        - ```s*a + t*b = gcd(a, b)```의  ```s```, ```t```를 구하고 ```gcd(a, b)```값도 구한다.
    - Linear Diophantine Equation
        - linear diophantine equation of **two variable** ```ax + by = c```
        - let d = gcd(a, b). if d|c, infinite number of solutions
            - particular solution:
                1. reduce the equation by dividing both sides by d
                2. solve s and t (extended euclidean algorithm)
                3. ```x_0 = (c/d)s```, ```y_0 = (c/d)t```
            - general solution: ```x = x_0 + k(b/d)``` and ```y = y_0 - k(a/d)``` (k is an integer)
        - else, no solution
    

## 2.2 Modular arithmetic
- Modulo Operator: ```mod```, Integer Division ```a = q * n + r``` 중 ```n```: modulus(positive), ```r```: residue(nonnegative)
- Set of Residue: the set of least residues modulo n, ```Z_n = {0, 1, 2, 3, ..., (n-1)}```(size: n)
- Congruence (**&equiv;**), **congruent** modulo n: have the same residue for the modulus n
    - Residue Classes: ```[a]```, ```[a]_n``` : the set of integers congruent modulo n
    - Circular Notation: a &equiv; 2 (mod n)
- Operation in Z_n
    - Property 1: (a + b) mod n = [(a mod n) + (b mod n)] mod n
    - Property 2: (a - b) mod n = [(a mod n) - (b mod n)] mod n
    - Property 3: (a * b) mod n = [(a mod n) * (b mod n)] mod n
        - 10^n mod x = (10 mod x)^n 
        - an integer divided by 3 is the same as the remainder of the sum of its decimal digits
- Inverses
    - Additive Inverse: **a + b &equiv; 0 (mod n)**, each integer has an additive inverse
        - The sum of an integer and its additive inverse is congruent to 0 modulo n.
    - Multiplicative Inverse: **a * b &equiv; 1 (mod n)**, an integer may or may not have a multiplicative inverse
        - The product of the integer and its multiplicative inverse is congruent to 1 modulo n.
        - the multiplicative inverse of ```b``` in ```Z_n``` can be found using the extended Euclidean algorithm
            - when ```n``` and ```b``` are given and **gcd(n, b) &equiv; 1**
            - ```(s * n) + (t * b) = 1```, t is the inverse of b
- Addition and Multiplication Tables 이라는 것이 있다. addition table의 0은 additive inverse를 보여주고 multiplication table의 1은 multiplicative inverse를 보여준다.
= Different Sets for Addition and Multiplication
    - ```Z_n```(additive inverse needed) and ```Z_p```(multiplicative inverses are needed)
    - ```Z_p``` and ```Z_p*```(prime number only)
    
## 2.3 Matrices
- Matrix Equality, Addition, Subtraction, Multiplication
- **Determinant**: ```det(A)``` where A is a square matrix of size m * m
    - Multiplicative inverse exists only if the det(A) has a multiplicative inverse in the corresponding set
- Residue Matrices: matrices where all elements are in ```Z_n```
    - Multiplicative inverse exists if gcd(det(A), n) = 1.
    - Scalar Multiplication 가능, Congruence A &equiv; B if a_ij &equiv; b_ij for all i's and j's

## 2.4 Linear Congruence
- Single-Variable Linear Equations
    - **ax &equiv; b (mod n)** : if ```d|b```, there are d solutions. if not, there's no solution.
        1. Reduce the equation by dividing both sides including the modulus. 
        2. Multiply both sides of the reduced equation by inverse of a to find the particular solution
        3. The general solutions are ```x = x_0 + (n/d)k``` for k = 0, 1, 2, ..., (d-1).
- Set of Linear Equations
    1. Equations
    2. Interpretation
    3. Solution
