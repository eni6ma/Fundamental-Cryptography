# Fundamental-Cryptography

# Primitive functions for Cryptographic systems
## Key of Greek Symbols and Mathematical Notation

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

----

# AES : Cyptography Sequence
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


