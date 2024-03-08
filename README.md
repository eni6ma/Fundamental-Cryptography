# Fundamental-Cryptography

# Primitive functions for Cryptographic systems

The cryptographic algorithms AES-Rijndael, RSA, and Diffie-Hellman, while distinct in application and design, share common mathematical underpinnings that facilitate secure communication. Each of these systems begins with the reception of input values or keys, denoted as $\alpha$ and $\beta$. These initial values are crucial as they seed the subsequent transformations and encryptions. In particular, these inputs are subjected to an initial transformation $\Phi$, which may involve key expansion in AES, the generation of public keys in Diffie-Hellman, or modular arithmetic in RSA.

Key generation is central to each of these algorithms and is represented by the function $\Lambda$. This function takes the initial inputs and possibly large prime or composite numbers, denoted as $\eta$ or $\xi$, to produce encryption and decryption keys. The RSA algorithm utilizes these prime numbers to establish a robust framework for secure key exchange, while Diffie-Hellman leverages them for creating a shared secret over an insecure channel. AES uses a similar process for generating a series of round keys for its block cipher operation. 

The heart of these cryptographic systems is the encryption and decryption process, signified by the functions $\Omega$ and $\Theta$. Encryption transforms plaintext into unreadable ciphertext using generated keys, while decryption inverts this process, returning the ciphertext to its original plaintext form. These operations rely on complex mathematical computations like modular exponentiation, ensuring that without the correct keys, deciphering the encrypted information is computationally infeasible.

Finally, an additional layer of security in cryptographic systems is introduced through pseudo-random operations, represented by the function $\Gamma$. These operations add complexity and unpredictability to the cryptographic process, thwarting attempts at pattern recognition, such as those used in differential power analysis. By incorporating pseudo-random values into the encryption process or using them in the generation of cryptographic keys, these algorithms enhance their resilience against various forms of cryptographic attacks.

In summary, although AES-Rijndael, RSA, and Diffie-Hellman differ in their specific mechanisms and use cases, they share a reliance on initial value processing, complex transformations for key generation, and the fundamental principles of encryption and decryption. Each system utilizes mathematical rigor and computational complexity to achieve its security goals, with prime number theory and modular arithmetic forming the backbone of these cryptographic giants.


In cryptographic systems like AES-Rijndael, RSA, and Diffie-Hellman, secure communication is enabled through a series of mathematical transformations. The initial stage in these algorithms involves the acceptance of input values or keys, denoted by $\alpha$ and $\beta$. These inputs are essential, as they set the stage for the key generation and encryption processes that follow. They are subjected to an initial transformation function, $\Phi$, which can take different forms depending on the algorithm:

- For AES-Rijndael, $\Phi$ might represent key expansion.
- In Diffie-Hellman, $\Phi$ typically involves generating public keys.
- For RSA, $\Phi$ could represent the modular arithmetic used in generating public and private keys.

This can be represented mathematically as:
$$\Phi(\alpha, \beta) \rightarrow \text{Intermediate values for further processing}$$

Key generation, represented by the function $\Lambda$, is the next critical step. It leverages the initial inputs and may incorporate large prime or composite numbers, symbolized by $\eta$ or $\xi$, to produce keys essential for the encryption and decryption processes. This step is described by the equation:
$$\Lambda(\alpha, \beta, \eta \text{ or } \xi) \rightarrow \text{Keys for encryption and decryption}$$

For encryption and decryption, the algorithms use two functions, $\Omega$ for encryption and $\Theta$ for decryption, which utilize the keys generated by $\Lambda$ to transform plaintext to ciphertext and vice versa:
$$\Omega(\text{Plaintext}, \text{Key}) \rightarrow \text{Ciphertext}$$
$$\Theta(\text{Ciphertext}, \text{Key}) \rightarrow \text{Plaintext}$$

These functions perform complex mathematical operations like modular exponentiation, ensuring that without the correct keys, deciphering the encrypted data remains a challenging task.

An additional security layer is introduced by the function $\Gamma$, which handles pseudo-random operations to add complexity and unpredictability, effectively enhancing the security of cryptographic processes. This could involve generating pseudo-random values for use in the encryption process or the generation of cryptographic keys:
$$\Gamma(\text{Input parameters}) \rightarrow \text{Pseudo-random values or sequences}$$

While AES-Rijndael, RSA, and Diffie-Hellman have unique mechanisms and applications, they share fundamental principles like the processing of initial values, complex transformations for key generation, and encryption/decryption methods. All three algorithms employ mathematical rigor and computational complexity, relying on the security provided by prime number theory and modular arithmetic to protect data.


## Key of Greek Symbols and Mathematical Notation

Pseudo Code Algorithm Sequence:

1. Initialize Variables
   $$\alpha, \beta$$

2. Initial Transformations
   $$\gamma = \Phi(\alpha)$$
   $$\delta = \Phi(\beta)$$

3. Key Generation
   if $$\eta$$ and $$\xi$$ are provided:
       $$\text{keys} = \Lambda(\alpha, \beta, \eta, \xi)$$
   else:
       $$\text{keys} = \Lambda(\alpha, \beta)$$

4. Encryption/Decryption
   $$C = \Omega(M, \text{keys})$$
   $$M = \Theta(C, \text{keys})$$

5. Pseudo-random Operations
   $$\text{random\_value} = \Gamma()$$

Explicit Equations in Math Notation:

- For the Initial Transformation:
  $$\Phi(\alpha) \rightarrow \gamma$$
  $$\Phi(\beta) \rightarrow \delta$$

- For the Key Generation Function:
  $$\Lambda(\alpha, \beta, \eta, \xi) \rightarrow \text{keys}$$

- For the Encryption Function:
  $$\Omega(M, \text{keys}) \rightarrow C$$

- For the Decryption Function:
  $$\Theta(C, \text{keys}) \rightarrow M$$

- For the Generation of Pseudo-random Values or Sequences:
  $$\Gamma() \rightarrow \text{random\_value}$$


## Claim 1: Key Generation Improvement
- **Context**: In a key generator for AES—Rijndael algorithm.
- **Objective**: Generate round-key words "on-the-fly" in reverse direction for decryption.
- **Method Steps**:
  1. **Provide memory** for storing a final set of $N_k$ round-key words.
  2. **Perform key expansion** in a forward direction during encryption, storing the final $N_k$ words.
  3. **Set key generator** for decryption.
  4. **Derive preceding round-key words** "on-the-fly" using XOR logic, with specific conditions for transformations.
- **Implementation**: As a hardware circuit with multiple S-boxes for S-box byte substitutions, featuring different power consumption signatures. A pseudo-random generator selects pathways to these S-boxes during key expansion.

## Claim 2: Pseudo-random Generator Specification
- **Relation**: Refers to the method of claim 1.
- **Specification**: The pseudo-random generator is detailed as a linear feedback shift register with n-bit output, coupled with a look-up table for pathway selection control signals.

## Claim 3: Differential Power Analysis Countermeasure
- **Context**: In a hardware block cipher circuit with a pre-mix XOR operation.
- **Objective**: Introduce a countermeasure against differential power analysis.
- **Implementation**: A dummy circuit with matched propagation delay to the pre-mix subcircuit, incorporating a pseudo-random generator and an XOR array, to insert pseudo-random noise into the power signature during the initial pre-mix XOR operation.

## Claim 4: Pseudo-random Generator Detail for Claim 3
- **Relation**: Refers to the circuit of claim 3.
- **Specification**: The pseudo-random generator consists of linear feedback shift registers.

## Claim 5: Word Width Matching
- **Relation**: Refers to the circuit of claim 3.
- **Specification**: The pseudo-random generator and XOR array of the dummy circuit match the word width in bits of the pre-mix subcircuit.

## Claim 6: Pre-mix and Encryption Round Combination
- **Context**: In a hardware block cipher circuit for a cipher algorithm.
- **Objective**: Combine the pre-mix operation with the first cipher encryption round.
- **Method Steps**:
  1. **Pre-process the cipher key** for first cipher encryption round key words while loading plaintext.
  2. **Execute the first cipher encryption round** on the pre-mixed plaintext with pre-generated first round-key words.

Each claim specifies a novel aspect of the cryptographic process, focusing on efficiency, security (particularly against differential power analysis), and the practical implementation of these cryptographic methods in hardware. The structure of these claims reflects a typical approach in patent documentation to provide a clear definition of the inventive elements, their implementation details, and, in some cases, specific embodiments or applications of the invention.

- $\alpha, \beta$: Input variables, representing initial values or keys.
- $\Phi$: General transformation or function, applicable in various contexts such as key expansion, encryption, or modular exponentiation.
- $\Psi$: XOR logic operation or another binary operation used in transformations.
- $\Lambda$: Function for key generation or the process of deriving new values in a cryptographically secure manner.
- $\Omega$: Encryption function, transforming plaintext into ciphertext using keys and specific operations.
- $\Theta$: Decryption function, the inverse of $\Omega$, recovering plaintext from ciphertext.
- $\eta, \xi$: Large prime numbers or composite numbers, foundational to the security of cryptographic algorithms.
- $\Gamma$: Function representing the generation or application of pseudo-random values or sequences.

## Common Cryptographic Algorithm Sequence

| Step | Process                  | Mathematical Representation              |
|------|--------------------------|------------------------------------------|
| 1    | Input Reception          | Receive $\alpha$ and $\beta$ as inputs.  |
| 2    | Initial Transformation   | Apply $\Phi$ to $\alpha$ and $\beta$, generating intermediate values. |
| 3    | Key Generation           | Use $\Lambda$ with inputs $\alpha$, $\beta$, and possibly $\eta$ or $\xi$ to generate keys. |
| 4    | Encryption/Decryption    | Apply $\Omega$ for encryption and $\Theta$ for decryption using generated keys. |
| 5    | Pseudo-random Operations | Utilize $\Gamma$ for operations requiring pseudo-randomness or additional security measures. |


The claims related to cryptographic key generation and encryption mechanisms, specifically in the context of the Advanced Encryption Standard (AES)—Rijndael block cipher algorithm. Here's a breakdown of these claims into a more structured format for clarity:

----

# AES : Cyptography Sequence

The claims related to cryptographic key generation and encryption mechanisms, specifically in the context of the Advanced Encryption Standard (AES)—Rijndael block cipher algorithm. Here's a breakdown of these claims into a more structured format for clarity:

## Claim 1: Key Generation Improvement
- **Context**: In a key generator for AES—Rijndael algorithm.
- **Objective**: Generate round-key words "on-the-fly" in reverse direction for decryption.
- **Method Steps**:
  1. **Provide memory** for storing a final set of $N_k$ round-key words.
  2. **Perform key expansion** in a forward direction during encryption, storing the final $N_k$ words.
  3. **Set key generator** for decryption.
  4. **Derive preceding round-key words** "on-the-fly" using XOR logic, with specific conditions for transformations.
- **Implementation**: As a hardware circuit with multiple S-boxes for S-box byte substitutions, featuring different power consumption signatures. A pseudo-random generator selects pathways to these S-boxes during key expansion.

## Claim 2: Pseudo-random Generator Specification
- **Relation**: Refers to the method of claim 1.
- **Specification**: The pseudo-random generator is detailed as a linear feedback shift register with n-bit output, coupled with a look-up table for pathway selection control signals.

## Claim 3: Differential Power Analysis Countermeasure
- **Context**: In a hardware block cipher circuit with a pre-mix XOR operation.
- **Objective**: Introduce a countermeasure against differential power analysis.
- **Implementation**: A dummy circuit with matched propagation delay to the pre-mix subcircuit, incorporating a pseudo-random generator and an XOR array, to insert pseudo-random noise into the power signature during the initial pre-mix XOR operation.

## Claim 4: Pseudo-random Generator Detail for Claim 3
- **Relation**: Refers to the circuit of claim 3.
- **Specification**: The pseudo-random generator consists of linear feedback shift registers.

## Claim 5: Word Width Matching
- **Relation**: Refers to the circuit of claim 3.
- **Specification**: The pseudo-random generator and XOR array of the dummy circuit match the word width in bits of the pre-mix subcircuit.

## Claim 6: Pre-mix and Encryption Round Combination
- **Context**: In a hardware block cipher circuit for a cipher algorithm.
- **Objective**: Combine the pre-mix operation with the first cipher encryption round.
- **Method Steps**:
  1. **Pre-process the cipher key** for first cipher encryption round key words while loading plaintext.
  2. **Execute the first cipher encryption round** on the pre-mixed plaintext with pre-generated first round-key words.

Each claim specifies a novel aspect of the cryptographic process, focusing on efficiency, security (particularly against differential power analysis), and the practical implementation of these cryptographic methods in hardware. The structure of these claims reflects a typical approach in patent documentation to provide a clear definition of the inventive elements, their implementation details, and, in some cases, specific embodiments or applications of the invention.


## Key of Greek Symbols and Mathematical Notation

- $\Lambda$: Function representing the key expansion routine.
- $N_k$: Number of cipher key words.
- $N_b$: Cipher block size in words.
- $N_r$: Number of rounds in the cipher algorithm.
- $w[i]$: Round-key words.
- $\oplus$: XOR logic operation.
- $\Theta$: Transformation sequence including cyclic byte shift, S-box byte substitution, and XOR with a round constant.
- $S$: S-box function for byte substitution.
- $R$: Pseudo-random generator function.
- $\Sigma$: Function representing the differential power analysis countermeasure.
- $P$: Pre-mix operation.
- $E$: Encryption operation.
- $D$: Decryption operation.

## Algorithmic Sequence in Table Format

| Step | Process | Mathematical Representation |
|------|---------|-----------------------------|
| 1    | Key Storage | Store final set of $N_k$ round-key words. |
| 2    | Key Expansion | Perform $\Lambda$ in a forward direction to obtain $w[i]$ for $i = 0$ to $N_b(N_r + 1) - 1$. |
| 3    | On-the-fly Key Generation for Decryption | For $i \geq N_k$, generate $w[i - N_k]$ using $\Psi(w[i], w[i - 1], \Theta)$ as needed. |
| 4    | S-box Substitution | Apply $S$ for byte substitution in $\Theta$ based on conditions (e.g., $i \mod N_k = 0$). |
| 5    | Pseudo-random Pathway Selection | Use $R$ to select pathways to S-boxes for byte substitution in $\Theta$. |
| 6    | Differential Power Analysis Countermeasure | Implement $\Sigma$ using a dummy circuit with pseudo-random noise for the initial $P$ operation. |
| 7    | Pre-mix and Encryption Round Combination | Combine $P$ with the first $E$ round, applying pre-processed cipher key and pre-mixed plaintext. |

----

# Diffie Hellman - Encryption

The Diffie-Hellman claims detail the invention of a secure key generation and communication system that operates over an insecure communication channel. The system uses transformations of signals to generate secure cipher keys that are infeasible to invert or generate without proper inputs. This method ensures secure communication by encrypting and decrypting messages using the generated keys. Here's a breakdown of the claims:

## Claim 1: Secure Key Generator
- **Components**: Consists of a first input, second input, first output, second output, and means for generating signals.
- **Functionality**: Generates a third signal from the first signal and a fourth signal from the second signal. Both transformations are infeasible to invert, and the fourth signal, representing a secure key, cannot be generated with just the second and third signals.

## Claim 2: Secure Communication Method
- **Involves**: Generating transformed signals at both transmitter and receiver that are infeasible to invert.
- **Secure cipher keys**: Generated by both the transmitter and receiver through specific transformations, ensuring they match (third and fourth signals).
- **Messages**: Encrypted with the secure cipher key before transmission and decrypted at the receiver.

## Claim 3: Authentication Feature
- **Adds**: A step to Claim 2's method by authenticating the receiver at the transmitter through the receiver's ability to generate the correct secure cipher key.

## Claim 4: Secure Cipher Key Generation Method
- **Similar**: To Claim 2 but focuses on the steps involved in generating the secure cipher key between transmitter and receiver.

## Claim 5: Apparatus for Generating Secure Cipher Key
- **Describes**: A more complex system involving two secure key generators for transforming signals into secure keys through infeasible-to-invert transformations.

## Claim 6: Specific Method for Generating Secure Cipher Key
- **Specifies**: The mathematical operations for transforming signals into secure cipher keys, including raising numbers to powers modulo a second number.

## Claim 7: Specific Apparatus for Secure Cipher Key Generation
- **Similar**: To Claim 5 but details the mathematical operations for the transformations, including exponentiation modulo a prime number.

## Claim 8: Detailed Apparatus for Generating Secure Cipher Key
- **Provides**: A detailed mathematical description of the transformations used to generate the secure cipher keys, including specific equations and conditions involving prime numbers and random numbers.

Each claim builds upon the previous ones by adding details or new elements to the secure key generation and communication process. The progression from claims about general methods and apparatuses to specific mathematical operations and authentication features illustrates the thoroughness in covering various aspects of secure communication over insecure channels.

To represent the Diffie-Hellman key exchange mechanism into mathematical notation with a focus on functions and variables at each stage, we outline the algorithm sequence using a table format.

## Key of Greek Symbols and Mathematical Notation

- $\Sigma$: Function for generating signals or performing transformations.
- $\alpha, \beta$: Input signals.
- $\gamma, \delta$: Output signals, where $\gamma$ represents a transformed version of $\alpha$, and $\delta$ represents a secure key generated from $\alpha$ and $\beta$.
- $q$: A large prime number.
- $a$: A primitive root modulo $q$.
- $x_i, x_j$: Private keys chosen by the first and second parties, respectively.
- $Y_i, Y_j$: Public keys generated by the first and second parties, respectively.
- $K_{ij}, K_{ji}$: Secure cipher keys generated by the first and second parties, respectively.

## Algorithm Sequence in Table Format

| Step | Process                         | Mathematical Representation                                    |
|------|---------------------------------|----------------------------------------------------------------|
| 1    | Input Reception                 | Receive $\alpha$ and $\beta$ as input signals.                  |
| 2    | Signal Transformation           | $\gamma = \Sigma(\alpha), \delta = \Sigma(\beta, \alpha)$       |
| 3    | Secure Key Generation (Transmitter) | $Y_i = a^{x_i} \mod q$                                   |
| 4    | Secure Key Generation (Receiver) | $Y_j = a^{x_j} \mod q$                                   |
| 5    | Transmission of Transformed Signals | Transmitter sends $Y_i$ to Receiver; Receiver sends $Y_j$ to Transmitter. |
| 6    | Generation of Matching Secure Keys | Transmitter: $K_{ij} = Y_j^{x_i} \mod q$; Receiver: $K_{ji} = Y_i^{x_j} \mod q$ |
| 7    | Authentication (Optional)       | Verify the ability to generate $K_{ij}$ or $K_{ji}$ as proof of identity.  |

## Process Description

- **Step 1**: Both parties (transmitter and receiver) introduce their initial signals ($\alpha$ and $\beta$).
- **Step 2**: Each signal is transformed using function $\Sigma$, aimed at generating a secure cipher key through subsequent transformations.
- **Steps 3 & 4**: Both parties generate their public keys ($Y_i$ and $Y_j$) using their private keys ($x_i$ and $x_j$) and a common base ($a$) and prime ($q$).
- **Step 5**: The parties exchange their public keys over the insecure channel.
- **Step 6**: Each party computes the secure cipher key by raising the received public key to the power of their private key, modulo $q$, resulting in matching keys ($K_{ij} = K_{ji}$) for encryption and decryption.
- **Step 7** (Optional): Authentication can be performed based on the ability to correctly generate and use the secure cipher key.


## Key of Greek Symbols and Mathematical Notation

- $\Sigma$: Function for generating signals or performing transformations.
- $\alpha, \beta$: Input signals.
- $\gamma, \delta$: Output signals, where $\gamma$ represents a transformed version of $\alpha$, and $\delta$ represents a secure key generated from $\alpha$ and $\beta$.
- $q$: A large prime number.
- $a$: A primitive root modulo $q$.
- $x_i, x_j$: Private keys chosen by the first and second parties, respectively.
- $Y_i, Y_j$: Public keys generated by the first and second parties, respectively.
- $K_{ij}, K_{ji}$: Secure cipher keys generated by the first and second parties, respectively.

## Algorithm Sequence in Table Format

| Step | Process                        | Mathematical Representation                        |
|------|--------------------------------|----------------------------------------------------|
| 1    | Input Reception                | Receive $\alpha$ and $\beta$ as input signals.     |
| 2    | Signal Transformation          | $\gamma = \Sigma(\alpha), \delta = \Sigma(\beta, \alpha)$ |
| 3    | Secure Key Generation (Transmitter) | $Y_i = a^{x_i} \mod q$                              |
| 4    | Secure Key Generation (Receiver) | $Y_j = a^{x_j} \mod q$                              |
| 5    | Transmission of Transformed Signals | Transmitter sends $Y_i$ to Receiver; Receiver sends $Y_j$ to Transmitter. |
| 6    | Generation of Matching Secure Keys | Transmitter: $K_{ij} = Y_j^{x_i} \mod q$ Receiver: $K_{ji} = Y_i^{x_j} \mod q$ |
| 7    | Authentication (Optional)      | Verify the ability to generate $K_{ij}$ or $K_{ji}$ as proof of identity. |

----

# RSA - Encryption Algorithm

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


