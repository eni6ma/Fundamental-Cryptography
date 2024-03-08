# Standard Cryptographic Primitives

## 1. **Coprime (Relatively Prime)**:

Two integers are considered coprime if they share no common factors other than 1. In cryptographic applications, coprime numbers are often used in generating public and private keys for asymmetric encryption schemes like RSA.

   Mathematically, two integers $a$ and $b$ are coprime if their greatest common divisor (GCD) is 1:
   $$\gcd(a, b) = 1$$

   For example, 15 and 28 are coprime because their only common divisor is 1.

## 2. **XOR (Exclusive OR)**: 

XOR is a binary operation that outputs true (1) only when the number of true inputs is odd. In cryptography, XOR is commonly used for encrypting and decrypting data, as well as for generating cryptographic hash functions and key derivation.

   The XOR operation is denoted by the symbol $\oplus$, and it can be represented as follows:
   $$A \oplus B = (A \land \lnot B) \lor (\lnot A \land B)$$

   For example, if we XOR two binary numbers $1010_2$ and $1100_2$, the result would be $0110_2$.

## 3. **Modulus Operation**: 

In modular arithmetic, the modulus operation calculates the remainder when one integer is divided by another. In cryptography, the modulus operation is fundamental in asymmetric encryption algorithms like RSA, where large prime numbers are used to generate keys.

   Mathematically, the modulus operation is represented using the symbol $\%$, and it is defined as:
   $a \mod n = r$

   This means that when $a$ is divided by $n$, the remainder $r$ is the result.

   For example, $17 \mod 5 = 2$ because when 17 is divided by 5, the remainder is 2.

These mathematical concepts form the basis of many cryptographic algorithms and are crucial for ensuring the security and integrity of encrypted data.

This is illustration of how Coprime (Relatively Prime), XOR (Exclusive OR), and the Modulus Operation can be used in a generic cryptography algorithm:


## Math Notation Key
Here's the key of functions and variables used in the cryptography algorithm, presented as a LaTeX table for GitHub Markdown:


| Symbol            | Description                                       |
|-------------------|---------------------------------------------------|
| $p, q$            | Large prime numbers                               |
| $n$               | Modulus computed by multiplying $p$ and $q$      |
| $e$               | Public exponent                                   |
| $d$               | Private exponent                                  |
| $M$               | Plaintext message                                 |
| $C$               | Ciphertext                                        |
| $H$               | Cryptographic hash                               |
| $S$               | Signature                                         |
| $K$               | One-time pad                                      |
| $r$               | Random number                                     |
| $v$               | Pseudorandom value                                |
| $M'$              | Received plaintext message                        |
| $S'$              | Received signature                                |
| $H'$              | Hash computed from the received message           |


This table provides a clear reference for the symbols used in the cryptography algorithm described earlier. Each symbol is accompanied by a brief description of its role in the algorithm.

## Generic Cryptography Algorithm

1. **Key Generation**:
   - Generate two large prime numbers, $p$ and $q$, that are coprime to each other.
   - Calculate the modulus $n$ by multiplying $p$ and $q$: $n = p \times q$.
   - Choose a public exponent $e$ that is coprime to $(p-1)(q-1)$.
   - Compute the private exponent $d$ such that $d \times e \equiv 1 \mod ((p-1)(q-1))$.

2. **Encryption**:
   - Convert the plaintext message $M$ into a numerical value.
   - Compute the ciphertext $C$ using the public key $(e, n)$: $C \equiv M^e \mod n$.

3. **Decryption**:
   - Retrieve the ciphertext $C$.
   - Compute the plaintext message $M$ using the private key $(d, n)$: $M \equiv C^d \mod n$.

4. **Data Integrity**:
   - XOR the original message $M$ with a cryptographic hash $H$ to create a signature $S$: $S = M \oplus H$.
   - To verify integrity, XOR the received message $M'$ with the same cryptographic hash $H$ and compare the result with the received signature $S'$: $M' \oplus H = S'$.

5. **Randomness Generation**:
   - Generate a random number $r$.
   - Compute a pseudorandom value $v$ using the modulus operation: $v = r \mod n$.

6. **Secure Communication**:
   - Use XOR to combine the plaintext message $M$ with a one-time pad $K$: $C = M \oplus K$.
   - To decrypt, XOR the ciphertext $C$ with the same one-time pad $K$: $M = C \oplus K$.

7. **Digital Signatures**:
   - Compute a cryptographic hash $H$ of the message $M$.
   - Sign the hash $H$ using the private key: $S = H^d \mod n$.
   - Verify the signature $S$ using the public key: $H' \equiv S^e \mod n$, where $H'$ is the hash computed from the received message.

These examples demonstrate how Coprime (Relatively Prime), XOR (Exclusive OR), and the Modulus Operation play essential roles in various aspects of cryptography, including key generation, encryption, decryption, data integrity, randomness generation, secure communication, and digital signatures.

----

An example of the use of SBOX Shift, Rotate, and Log in a generic cryptography algorithm:


### SBOX Shift, Rotate, and Log in Cryptography

In many cryptography algorithms, SBOX operations play a crucial role in nonlinear transformations and substitution processes. Three common operations used within SBOX are:

## 1. **Shift**: 
This operation involves shifting the bits of a binary number by a certain number of positions to the left or right.

   Mathematically, the shift operation can be represented as follows:
   
$$
\text{Shift}_k(x) = \begin{cases} 
x << k & \text{if shifting left} \\
x >> k & \text{if shifting right} 
\end{cases}
$$


   Here, $x$ represents the binary input, and $k$ denotes the number of positions to shift.

## 2. **Rotate**: 
Rotation involves circularly shifting the bits of a binary number to the left or right.

   The rotation operation can be defined as follows:
   
$$
\text{Rotate}_k(x) = \begin{cases} 
(x << k) \,|\, (x >> (n - k)) & \text{if rotating left} \\
(x >> k) \,|\, (x << (n - k)) & \text{if rotating right}
\end{cases}
$$


   Here, $n$ represents the total number of bits in the binary number.

## 3. **Logarithm**: 
In cryptographic algorithms, logarithmic operations are often used to compute discrete logarithms over finite fields.

   Mathematically, the logarithm operation can be expressed as:
   
$$
\log_b(a) = c
$$


   Here, $a$ is the base, $b$ is the exponent, and $c$ is the result.


These operations are fundamental in many cryptographic algorithms for achieving confusion and diffusion, enhancing security and preventing attacks.


This markdown provides an explanation of how SBOX Shift, Rotate, and Log operations are used in cryptography, along with their corresponding mathematical representations using LaTeX equations.



----
# Encrypt & Decrypt 

Encrypting and decrypting using a combination of shift, XOR, and logarithmic operations involves manipulating the plaintext data in a specific manner to ensure confidentiality and integrity. Here's how these operations can be applied:

1. **Shift Operation**: The shift operation involves moving the bits of a binary representation of the plaintext to the left or right by a certain number of positions.

2. **XOR Operation**: XOR, or exclusive OR, is a binary operation where the result is true (1) only when the inputs differ. It's commonly used in encryption algorithms to combine the plaintext with a secret key or another piece of data.

3. **Logarithmic Operation**: The logarithmic operation involves computing the discrete logarithm of a number. In the context of encryption, logarithmic operations can be used to further obscure the relationship between the plaintext and the encrypted data.

Now, let's illustrate how these operations can be used in the encryption and decryption processes:

### Encryption Process:

1. **Shift**: Initially, the plaintext is shifted by a predetermined number of positions to the left or right.
2. **XOR with Key**: The shifted plaintext is then XORed with a secret key, which adds randomness and ensures that the resulting ciphertext is dependent on both the plaintext and the key.
3. **Logarithmic Operation**: Optionally, a logarithmic operation can be applied to further obscure the ciphertext.

Mathematically, the encryption process can be represented as:

$$
\text{Ψ}(\alpha) = (\text{Φ}_\beta(\text{Γ})) \oplus \phi
$$

### Decryption Process:

1. **Logarithmic Operation**: If a logarithmic operation was applied during encryption, it is reversed in the decryption process.
2. **XOR with Key**: The ciphertext is XORed with the secret key to retrieve the shifted plaintext.
3. **Shift Inverse**: The shifted plaintext is then shifted back in the opposite direction to recover the original plaintext.

Mathematically, the decryption process can be represented as:

$$\[
\alpha = (\Psi \oplus \phi) \cdot \Phi_{\beta}^{-1}(\Phi_{\beta}(\alpha))
\]$$

By combining these operations in a secure and well-designed algorithm, it's possible to create an encryption scheme that protects sensitive information from unauthorized access.


| Symbol                  | Meaning                                                  |
|-------------------------|----------------------------------------------------------|
| $\alpha$                | Plaintext                                                |
| $\beta$                 | Secret key                                               |
| $\phi$                  | Ciphertext                                               |
| $\Psi$                  | Encryption function                                      |
| $\Phi_{\beta}$          | Key transformation function                              |
| $\Gamma$                | Intermediate value in encryption process                 |
| $\oplus$                | XOR (Exclusive OR) operation                             |
| $\text{Γ}$               | Shifted plaintext                                        |
| $\Phi_{\beta}^{-1}$     | Inverse of key transformation function                   |


----


```rust
fn main() {
    // Define plaintext, secret key, and ciphertext
    let alpha = "plaintext";
    let beta = "secret_key";
    let phi = "ciphertext";

    // Encryption process
    let gamma = shift_function(alpha); // Shift plaintext
    let psi_alpha = xor_function(beta, gamma); // XOR shifted plaintext with key
    let encrypted_result = logarithmic_function(psi_alpha, phi); // Apply optional logarithmic operation

    // Decryption process
    let psi_phi = xor_function(beta, phi); // XOR ciphertext with key
    let decrypted_result = shift_inverse_function(psi_phi); // Shift ciphertext back

    println!("Encrypted result: {}", encrypted_result);
    println!("Decrypted result: {}", decrypted_result);
}

// Define shift function
fn shift_function(plaintext: &str) -> String {
    // Implement shift operation (left or right shift)
    format!("{} (shifted)", plaintext)
}

// Define XOR function
fn xor_function(key: &str, data: &str) -> String {
    // Implement XOR operation
    format!("{} XOR {}", key, data)
}

// Define logarithmic function
fn logarithmic_function(data: &str, ciphertext: &str) -> String {
    // Implement optional logarithmic operation
    format!("{} (logarithmic operation) XOR {}", data, ciphertext)
}

// Define shift inverse function
fn shift_inverse_function(data: &str) -> String {
    // Implement shift inverse operation
    format!("{} (shift inverse)", data)
}
```

