# Chapter 2 Mathematics of Cryptography: Modular Arithmetric, Congruence, and Matrices

## 2.1 Integer arithmetic
- **set** as a background for modular arithmetic
- binary operation: two inputs & one ouput ```a (operation e.g. +, -, *) b = c```
- integer division : ```a = q * n + r```
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
- &equiv;	
    
