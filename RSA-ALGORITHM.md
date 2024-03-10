
### RSA Cryptographic Claims Summary

### RSA Cryptographic Algorithm Explained with Pseudocode

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


### RSA Cryptographic System Pseudocode

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
