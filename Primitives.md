1. **Coprime (Relatively Prime)**: Two integers are considered coprime if they share no common factors other than 1. In cryptographic applications, coprime numbers are often used in generating public and private keys for asymmetric encryption schemes like RSA.

   Mathematically, two integers $a$ and $b$ are coprime if their greatest common divisor (GCD) is 1:
   $$\gcd(a, b) = 1$$

   For example, 15 and 28 are coprime because their only common divisor is 1.

2. **XOR (Exclusive OR)**: XOR is a binary operation that outputs true (1) only when the number of true inputs is odd. In cryptography, XOR is commonly used for encrypting and decrypting data, as well as for generating cryptographic hash functions and key derivation.

   The XOR operation is denoted by the symbol $\oplus$, and it can be represented as follows:
   $$A \oplus B = (A \land \lnot B) \lor (\lnot A \land B)$$

   For example, if we XOR two binary numbers $1010_2$ and $1100_2$, the result would be $0110_2$.

3. **Modulus Operation**: In modular arithmetic, the modulus operation calculates the remainder when one integer is divided by another. In cryptography, the modulus operation is fundamental in asymmetric encryption algorithms like RSA, where large prime numbers are used to generate keys.

   Mathematically, the modulus operation is represented using the symbol $\%$, and it is defined as:
   $$a \mod n = r$$

   This means that when $a$ is divided by $n$, the remainder $r$ is the result.

   For example, $17 \mod 5 = 2$ because when 17 is divided by 5, the remainder is 2.

These mathematical concepts form the basis of many cryptographic algorithms and are crucial for ensuring the security and integrity of encrypted data.
