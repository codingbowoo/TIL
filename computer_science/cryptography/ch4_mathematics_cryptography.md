# Mathematics of Cryptography

## Algebraic Structures
### Groups (Z_n or Z_n*)
** Set of elements with a binary operation that satisfies four properties.

**Properties of a group**
- Closure
- Associativity
- Commutativity
- Existence of identity
- Existence of inverse

<br>Terms
- finite group
- order of a group ```|G|``` a number of elements in the group
- subgroups
    - cyclic subgroups: a^n = a * a * a * ... * a
 - Lagrange's Theorem: If H is a subgroup os G then ```|H|``` | ```|G|```
 - Order of an element: the order of the cyclic group it generates

### Rings (Z)
```R = <{...}, o1, o2> ``` : o1, o2 are operations <br>
**Distribution of o2 over o1**
- o1: Closure, Associativity, Commutativity, Existence of identity and inverse
- o2: Flosure, Associativity, Commutativity

### Fields(Z_p)
```F = <{...}, o1, o2> ``` <br>
**Distribution of o2 over o1**
- o1: Closure, Associativity, Commutativity, Existence of identity and inverse
- o2: Closure, Associativity, Commutativity, Existence of identity and inverse
- **The identity element of the first operation o1 has no inverse w.r.t. the second operation o2.**
- Finite Fields: A Galois field GF(p^n) is a finie field with p^n elements
 
 
##  GF(2^n) Fields
**n-bit words** and **two operations** that satisfies the properties defined for a field
- repsentation of an ```n-bit word``` by a polynomial, a polynomial of degree n-1
    - irreducible polynomial(modulus), reducible polynomial
    - additive/multiplicative identity and inverse(gained with extended Euclidean algorithm)
- Generator : {0, 1, g, g^2, ..., g^N}, where N=(2^n)-2



