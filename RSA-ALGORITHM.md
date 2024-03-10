
# RSA - Key Exchange Algorithm

Overview of Cryptographic Communications Systems and Methods

The claims broadly cover systems and methods for secure cryptographic communication between terminals or within a communications system. They involve encoding (encrypting) and decoding (decrypting) message signals using specific mathematical operations based on prime numbers, composite numbers, and modular arithmetic, which are foundational to cryptography.

## System Components and Operations

1. **Cryptographic System Configuration**:
   - Communications channel.
   - Encoding and decoding mechanisms.
   - Use of composite numbers $n = p \cdot q$, where $p$ and $q$ are prime numbers for encryption keys.
   - Encryption and decryption transformations based on modular exponentiation.

2. **Encoding and Decoding Processes**:
   - Transformation of message signals into encrypted or decrypted forms using keys characterized by specific mathematical properties (e.g., relatively prime numbers, multiplicative inverses).
   - Implementation of encoding and decoding steps via hardware components, such as registers and modular multiplication networks.

3. **Key Generation and Management**:
   - Methods for generating and using encoding and decoding keys.
   - Procedures for managing keys across multiple terminals within a communication system.

4. **Security Enhancements and Countermeasures**:
   - Introduction of pseudo-random noise and other mechanisms to counter differential power analysis attacks.
   - Utilization of multiple, diverse hardware implementations to obscure power consumption patterns.

5. **Detailed Implementations**:
   - Specific descriptions of hardware components and their interconnections for performing cryptographic operations.
   - Use of exponentiation by repeated squaring and multiplication for efficient encryption and decryption.

## Key Mathematical Principles

- Modular arithmetic operations form the basis of encryption and decryption methods, utilizing properties of prime numbers and their relationships.
- The system relies on the difficulty of factoring large composite numbers $(n = p \cdot q)$ and the mathematical properties of modular exponentiation for security.
- Encryption and decryption transformations are defined by equations involving modular exponentiation, where encryption keys $(e)$ and decryption keys $(d)$ have specific relationships to ensure reversibility of the process.

## Security and Efficiency

- The claims outline methods to enhance the security and efficiency of cryptographic communications, including the use of pseudo-random generators and specific hardware configurations to thwart side-channel attacks.
- Emphasis on modular arithmetic and exponentiation by repeated squaring and multiplication underscores the focus on efficient and secure cryptographic operations.

## Summary

The described claims in the text detail a comprehensive approach to securing communications through cryptographic systems, utilizing advanced mathematical operations, hardware implementations, and security measures. They encompass a broad range of technologies and methods integral to modern cryptography, highlighting the importance of secure key management, efficient encryption and decryption processes, and countermeasures against potential security threats.

To mathematically represent the RSA cryptographic communications systems and methods as described in the patent claims, we will express the encryption and decryption processes, key generation, and secure communication protocol. This structured mathematical representation will provide clarity on the algorithm's sequence and its components.

## Key of Greek Symbols and Mathematical Notation

- $n$: Composite number, $n = p \cdot q$ where $p$ and $q$ are prime numbers.
- $e$: Public exponent, relatively prime to $(p-1) \cdot (q-1)$.
- $d$: Private exponent, multiplicative inverse of $e \mod \lambda(n)$, where $\lambda$ is Carmichael's totient function.
- $M$: Plaintext message.
- $C$: Ciphertext message.
- $E$: Encryption function.
- $D$: Decryption function.
- $\Phi$: General transformation or function.
- $K$: Secure cipher key.

## Algorithmic Sequence in Table Format

| Step | Process         | Mathematical Representation                         |
|------|-----------------|-----------------------------------------------------|
| 1    | Key Generation  | $\Phi_{KeyGen}(p, q) \to (n, e, d)$                 |
| 2    | Encryption      | $E(M, e, n) = M^e \mod n \to C$                     |
| 3    | Decryption      | $D(C, d, n) = C^d \mod n \to M$                     |
| 4    | Secure Communication | $E(M) \to C \to D(C) \to M$                   |
| 5    | Key Exchange    | $K_{ij} = Y_i^{x_j} \mod q$                         |


----

# RSA Cryptographic Claims Summary

## Process Description

1. **Key Generation**: Generate two large prime numbers $p$ and $q$. Calculate $n = p \cdot q$ and $\lambda(n)$, where $\lambda$ is the least common multiple of $p-1$ and $q-1$. Choose $e$ such that $1 < e < \lambda(n)$ and $e$ is coprime to $\lambda(n)$. Determine $d$ as the multiplicative inverse of $e \mod \lambda(n)$.

2. **Encryption**: Using the public key $(n, e)$, the plaintext message $M$ is encrypted to produce ciphertext $C$ using $C = M^e \mod n$.

3. **Decryption**: With the private key $(n, d)$, the ciphertext $C$ is decrypted back to the original message $M$ using $M = C^d \mod n$.

4. **Secure Communication**: A message $M$ is securely transmitted by encrypting it into $C$ using the sender's encryption function, transmitted over an insecure channel, and then decrypted back into $M$ using the receiver's decryption function.

5. **Key Exchange**: The secure key $K_{ij}$ for communication is established between two parties by exponentiating a shared base $a$ to their respective private values $x_i$ and $x_j$, and exchanging the resulting values $Y_i$ and $Y_j$ over a public channel. Each party then raises the received value to their private exponent to compute the shared secret key $K_{ij}$.

This representation outlines the mathematical foundation of the RSA encryption and decryption process, highlighting the algorithm's reliance on prime numbers, modular arithmetic, and the infeasibility of factoring large composite numbers for security.

----

## Key of Greek Symbols and Mathematical Notation

- $n$: Composite number, $n = p \cdot q$ where $p$ and $q$ are prime numbers.
- $e$: Public exponent, relatively prime to $(p - 1) \cdot (q - 1)$.
- $d$: Private exponent, multiplicative inverse of $e \mod \lambda(n)$, where $\lambda$ is Carmichael's totient function.
- $M$: Plaintext message.
- $C$: Ciphertext message.
- $E$: Encryption function.
- $D$: Decryption function.
- $\Phi$: General transformation or function.
- $K$: Secure cipher key.

## Algorithm Sequence in Table Format

| Step | Process         | Mathematical Representation                          |
|------|-----------------|------------------------------------------------------|
| 1    | Key Generation  | $\Phi_{KeyGen}(p, q) \rightarrow (n, e, d)$          |
| 2    | Encryption      | $E(M, e, n) = M^e \mod n \rightarrow C$              |
| 3    | Decryption      | $D(C, d, n) = C^d \mod n \rightarrow M$              |
| 4    | Secure Communication | $E(M) \rightarrow C \rightarrow D(C) \rightarrow M$ |
| 5    | Key Exchange    | $K_{ij} = Y_i^{x_j} \mod q$                         |




The cryptographic communications system outlined through claims provides a comprehensive framework for secure message transmission. 

| Claim | Description | Equations |
|-------|-------------|-----------|
| 1 | Cryptographic system with encoding and decoding. | $0 \leq M \leq n-1$, $n = p \cdot q$, $C \equiv M^e \, (\text{mod} \, n)$, $M' \equiv C^d \, (\text{mod} \, n)$ |
| 2 | Details on transforming means with register and multiplication network. | - |
| 3 | System for transferring signals with $k$ terminals. | $0 \leq M_i \leq n_i-1$, $n_i = p_i \cdot q_i$, $M_{\text{As}} \equiv M_A^{d_A} \, (\text{mod} \, n_A)$ |
| 4 | First register means for storing and transforming signals. | - |
| 5 | Transmission and decoding of $M_{\text{As}}$ to $M_A$. | $M_A \equiv M_{\text{As}}^{e_A} \, (\text{mod} \, n_A)$ |
| 6 | Encoding $M_{\text{As}}$ into $C_{\text{As}}$. | $C_{\text{As}} \equiv M_{\text{As}}'^{e_B} \, (\text{mod} \, n_B)$ |
| 7 | Decoding $C_{\text{As}}$ to $M_A$. | $M_{\text{As}}' \equiv C_{\text{As}}^{d_B} \, (\text{mod} \, n_B)$, $M_A \equiv M_{\text{As}}^{e_A} \, (\text{mod} \, n_A)$ |
| 8 | Encoding $M_A$ to $C_A$. | $C_A \equiv M_A'^{e_B} \, (\text{mod} \, n_B)$ |
| 9 | Transforming means similar to claim 2. | - |
| 10 | Transmitting and decoding $C_A$ to $M_A$. | $M_A \equiv C_A^{d_B} \, (\text{mod} \, n_B)$ |
| 11 | Encoding $C_A$ into $C_{\text{As}}$. | $C_{\text{As}} \equiv C_A'^{d_A} \, (\text{mod} \, n_A)$ |
| 12 | Decoding $C_{\text{As}}$ to $M_A$. | $C_A' \equiv C_{\text{As}}^{e_A} \, (\text{mod} \, n_A)$ |

 - Claim 1 establishes the foundation by introducing a system that encodes a message $M$ into ciphertext $C$ using a composite number $n = p \cdot q$, where $p$ and $q$ are prime numbers. The encoding and decoding mechanisms are mathematically defined by $C \equiv M^e \mod n$ and $M' \equiv C^d \mod n$, respectively, showcasing the system's capability to transform messages for secure communication.

 - Claim 2 delves into the operational details of the transformation process, highlighting the use of register means for storing digital signals and an exponentiation network that processes these signals via modulo multiplication. This technical setup facilitates the secure encoding and decoding of messages.

 -  Claim 3 to describe a communications system capable of transferring message signals $M_i$ across multiple terminals, each equipped with unique encoding and decoding keys. This extends the system's application to a broader network, emphasizing scalability and security in message transmission across different nodes.

 - Claim 4 reiterates the importance of the system components in supporting the transformation process, specifically within the context of encoding messages for transmission. This emphasizes the robustness of the system's design in handling the encoding process.

 - Claim 5 introduces the functionality of transmitting encoded messages between terminals and subsequently decoding them back to their original format. This process ensures that messages remain secure throughout their transmission journey.

 - Claim 6 broadens the encoding mechanism by incorporating the conversion of signed messages into block word signals and then into signed ciphertext word signals, enhancing the system's versatility in encoding messages.

 -  Claim 7, the focus shifts to the transmission of signed ciphertext between terminals and its decryption back to the original message, highlighting the system's comprehensive approach to maintaining message integrity and confidentiality.

 - Claim 8 describes a scalable communication system where message signals $M_i$ are transferred among multiple terminals, each capable of encoding messages into block word signals for secure transmission. This showcases the system's adaptability to various communication needs.

 - Claim 9, similar to claims 2 and 4, revisits the system's capabilities in transforming message signals, emphasizing the critical role of registers and an exponentiation network in secure message processing.

 - Claims 10 through 14 further elaborate on the system's encoding and decoding processes, detailing the transmission of ciphertext between terminals, the enhancement of encoding systems, and the decryption capabilities to recover original messages. These claims collectively underscore the system's comprehensive approach to secure communications.

 - Claims 15 through 22, while not detailed individually, imply extensions and variations of the described system and methods. These claims suggest additional functionalities and adaptations that bolster the cryptographic communications system's robustness and flexibility, catering to a wide range of encryption and decryption processes for secure message handling.


| Claim Number | Summary |
|--------------|---------|
| 1 | Establishes a cryptographic communications system that includes a communications channel, an encoding mechanism to transform a message $M$ into a ciphertext $C$ using a composite number $n = p \cdot q$ (where $p$ and $q$ are prime), and a decoding mechanism to transform $C$ back to message $M'$. $C$ and $M'$ are determined by $C \equiv M^e \mod n$ and $M' \equiv C^d \mod n$ respectively, with $e$ and $d$ being specially chosen numbers. |
| 2 | Describes the components involved in the transformation process, including registers for storing digital signals and an exponentiation network for processing these signals based on modulo multiplication. |
| 3 | Details a communications system for transferring message signals $M_i$ across $k$ terminals, each with unique encoding and decoding keys, highlighting how messages are encoded for transmission. |
| 4 | Similar to claim 2, focusing on the system components that support the transformation process within the context of message signal encoding across terminals. |
| 5 | Adds the functionality of transmitting the encoded message from the first terminal to the second terminal and decoding it back to the original message format. |
| 6 | Expands the encoding mechanism to include conversion of a signed message into one or more signed message block word signals and then into signed ciphertext word signals for enhanced message encoding. |
| 7 | Involves transmitting the signed ciphertext from the first to the second terminal and decoding it back to the original signed message and then to the plain message. |
| 8 | Describes a system for transferring a message signal $M_i$ among $k$ terminals, where each terminal can encode a message into block word signals for transmission, indicating a scalable communication system. |
| 9 | Reiterates the system's capabilities in transforming message signals through a series of registers and an exponentiation network, similar to claims 2 and 4. |
| 10 | Focuses on transmitting ciphertext word signals between terminals and decoding them to recover the original message signals. |
| 11 | Enhances the encoding system to include the transformation of ciphertext into signed ciphertext word signals for secure transmission between terminals. |
| 12 | Details the process of decoding signed ciphertext word signals to recover the original message signal, highlighting the system's decryption capabilities. |
| 13 | Describes a communications system with multiple terminals capable of encoding and decoding message signals through specified encoding and decoding keys, emphasizing secure message transmission. |
| 14 | Similar to previous transformation process descriptions, focusing on the encoding and decoding mechanisms within a multi-terminal communications system. |
| 15 - 22 | Extensions and variations of the described system and methods, emphasizing the robustness and flexibility of the cryptographic communications system in handling different types of message signals and encryption/decryption processes. |



## RSA Cryptographic Algorithm Explained with Pseudocode

#### 1. Initialization:
The first step in the RSA algorithm is to generate the keys used for encryption and decryption. This involves selecting prime numbers and computing necessary values based on them.


#### [1] Select two distinct large prime numbers `p` and `q`.
 - Compute $n = p \times q$. ($n$ is used as the modulus for both the public and private keys)
 - Calculate the totient: $\phi = (p - 1) \times (q - 1)$.
 - Choose an integer $e$ such that $1 < e < \phi$ and $\gcd(e, \phi) = 1$; $e$ is the public key exponent.
 - Calculate $d$ as the modular multiplicative inverse of $e$ modulo $\phi$. ($d$ is the private key exponent)

#### [2] Public and Private Keys:
 - Public Key: The public key is a pair $(e, n)$. It is used for encrypting messages and is shared openly.
 - Private Key: The private key is a pair $(d, n)$. It is used for decrypting messages and must be kept secret.

#### [3] Encoding (Encryption):
To encrypt a message $M$ into a ciphertext $C$ using the recipient's public key $(e, n)$, follow this process.
Ensure that the message $M$ is a numeric value smaller than $n$.

 -  Represent the plaintext message $M$ as an integer in $[0, n-1]$.
 -  Compute the ciphertext $C$ using the equation: $C = M^e \mod n$.

#### [4] Decoding (Decryption):
To decrypt a ciphertext $C$ back into the original message $M$ using the private key $(d, n)$, follow this process:

 - Compute the original message $M$ using the equation: $M = C^d \mod n$.

```golang

package main

import (
    "math/big"
    "crypto/rand"
)

// KeyGeneration generates RSA keys given prime numbers p and q
func KeyGeneration(p, q *big.Int) (publicKey, privateKey *[2]*big.Int) {
    n := new(big.Int).Mul(p, q)
    phi := new(big.Int).Mul(new(big.Int).Sub(p, big.NewInt(1)), new(big.Int).Sub(q, big.NewInt(1)))
    e := big.NewInt(3)
    d := new(big.Int).ModInverse(e, phi)
    return &[2]*big.Int{e, n}, &[2]*big.Int{d, n}
}

// Encrypt encrypts message M with public key
func Encrypt(M *big.Int, publicKey *[2]*big.Int) *big.Int {
    e, n := publicKey[0], publicKey[1]
    C := new(big.Int).Exp(M, e, n)
    return C
}

// Decrypt decrypts ciphertext C with private key
func Decrypt(C *big.Int, privateKey *[2]*big.Int) *big.Int {
    d, n := privateKey[0], privateKey[1]
    M := new(big.Int).Exp(C, d, n)
    return M
}

func main() {
    // Example usage
    p, _ := rand.Prime(rand.Reader, 1024)
    q, _ := rand.Prime(rand.Reader, 1024)
    publicKey, privateKey := KeyGeneration(p, q)

    M := big.NewInt(123456789) // Example message
    C := Encrypt(M, publicKey)
    decryptedM := Decrypt(C, privateKey)

    fmt.Println("Original Message:", M)
    fmt.Println("Encrypted Message:", C)
    fmt.Println("Decrypted Message:", decryptedM)
}


```

Important Notes:
 - RSA's security is rooted in the difficulty of prime factorization.
 - The choice of e and the computation of d ensure that only the private key holder can decrypt messages encrypted with the public key.
 - RSA serves both data encryption and digital signature purposes.

---- 

## RSA Cryptographic System Pseudocode

#### Initialization:
1. Generate two large prime numbers, `p` and `q`.
2. Compute $n = p \times q$.
3. Calculate Euler's totient function, $\phi = (p-1) \times (q-1)$.
4. Choose an encryption exponent, `e`, such that $1 < e < \phi$ and $\gcd(e, \phi) = 1$.
5. Determine the decryption exponent, `d`, as the multiplicative inverse of `e` modulo $\phi$.

#### Encoding (Encryption):
- **Input**: Message `M` to be encoded, ensuring $0 \leq M < n$.
- **Process**:
  - Convert the message `M` into a number representative of the message within the range $[0, n-1]$.
  - Compute the ciphertext `C` by raising `M` to the power of `e` and taking the modulus `n`: $C = M^e \mod n$.
- **Output**: Ciphertext `C`.

#### Decoding (Decryption):
- **Input**: Ciphertext `C` to be decoded.
- **Process**:
  - Recover the original message `M'` by raising `C` to the power of `d` and taking the modulus `n`: $M' = C^d \mod n$.
- **Output**: Decoded message `M'`.

#### Functional Blocks:
- **KeyGeneration**(`p`, `q`):
  - Compute $n = p \times q$.
  - Calculate $\phi = (p-1) \times (q-1)$.
  - Choose `e` such that $\gcd(e, \phi) = 1$.
  - Compute `d = e^{-1} \mod \phi`.
  - Return `(e, d, n)`.

- **Encrypt**(`M`, `e`, `n`):
  - Verify $0 \leq M < n$.
  - Calculate $C = M^e \mod n$.
  - Return `C`.

- **Decrypt**(`C`, `d`, `n`):
  - Calculate $M' = C^d \mod n$.
  - Return `M'`.

#### Example Usage:
- `(e, d, n) = KeyGeneration(p, q)`
- `C = Encrypt(M, e, n)`
- `M' = Decrypt(C, d, n)`

Ensure $M = M'$ for the process to be correct. The security of the RSA system relies on the difficulty of factoring the product of two large primes.




| Claim | Summary | Equation(s) |
|-------|---------|-------------|
| 1 | Cryptographic system comprising a communications channel, an encoding means, and a decoding means for transforming messages M to ciphertext C and vice versa. | $0 \leq M \leq n-1$, $n = p \cdot q$, $C \equiv M^e \mod n$, $M' \equiv C^d \mod n$ |
| 2 | Details on transforming means, including register means for storing and an exponentiation network for processing digital signals. | - |
| 3 | System for transferring message signals among k terminals, each characterized by unique encoding and decoding keys. | $0 \leq M_i \leq n_i-1$, $n_i = p_i \cdot q_i$ |
| 4 | Transformation of messages using first register means for storing and processing digital signals. | - |
| 5 | Transmission and decoding of signed message word signals to original message signals. | $M_A \equiv M_{\text{As}}^{e_A} \mod n_A$ |
| 6 | Encoding and transformation of signed message word signals into one or more block word signals, then to signed ciphertext word signals. | $C_{\text{As}} \equiv M_{\text{As}}'^{e_B} \mod n_B$ |
| 7 | Decoding signed ciphertext word signals to original message word signals. | $M_{\text{As}}' \equiv C_{\text{As}}^{d_B} \mod n_B$, $M_A \equiv M_{\text{As}}^{e_A} \mod n_A$ |
| 8 | System for encoding digital message word signals into one or more block word signals for transmission. | $C_A \equiv M_A'^{e_B} \mod n_B$ |
| 9 | Similar transforming means as in claim 2 for encoding digital message word signals. | - |
| 10 | Transmission and decoding of ciphertext word signals to original message word signals. | $M_A \equiv C_A^{d_B} \mod n_B$ |
| 11 | Encoding ciphertext word signals into one or more block word signals, then to signed ciphertext word signals. | $C_{\text{As}} \equiv C_A'^{d_A} \mod n_A$ |
| 12 | Decoding signed ciphertext word signals to original message word signals. | $C_A' \equiv C_{\text{As}}^{e_A} \mod n_A$, $M_A \equiv C_A'^{d_B} \mod n_B$ |
| 13 | System for transforming transmit message word signals to signed message word signals and back. | $M_A \equiv M_{\text{As}}^{d_A} \mod n_A$, $M_A' \equiv M_{\text{As}}^{e_A} \mod n_A$ |
| 14 | Transforming means as in claim 13 but for both encoding and decoding processes. | - |
| 15 - 22 | Extensions and variations of claims 1-14, detailing the processing, encoding, and decoding mechanisms for secure communications. | Various transformations based on $e$, $d$, $n$, including block processing and encryption/decryption strategies. |



