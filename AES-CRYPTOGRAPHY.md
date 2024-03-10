# AES Encryption 

AES is a symmetric block cipher that encrypts and decrypts data in fixed-size blocks (128 bits) using cryptographic keys of 128, 192, or 256 bits. The core operations in AES include SubBytes, ShiftRows, MixColumns, and AddRoundKey, executed over multiple rounds. The number of rounds depends on the key size: 10 rounds for 128-bit keys, 12 rounds for 192-bit keys, and 14 rounds for 256-bit keys.

## AES Explained

 1. **Key Expansion (Key Schedule):**
   AES generates a series of round keys from the cipher key using the Rijndael key schedule. The round keys are used in each round of the AES encryption and decryption processes.

 2. **Initial Round:**
   - **AddRoundKey:**
     Each byte of the state is combined with the round key using bitwise XOR.
     $$\text{State} \oplus \text{RoundKey}$$

 3. **Main Rounds:**
   Each main round consists of four operations:
   - **SubBytes:** A non-linear substitution step where each byte is replaced with another according to a lookup table.
   - **ShiftRows:** A transposition step where each row of the state is shifted cyclically a certain number of steps.
   - **MixColumns:** A mixing operation that operates on the columns of the state, combining the four bytes in each column.
   - **AddRoundKey:** Each byte of the state is combined with the round key using bitwise XOR.
   
   The MixColumns step is skipped in the final round.

 4. **Final Round:**
   The final round is similar to the main rounds but does not include the MixColumns operation.


To convert the pseudocode functions into mathematical notations, I'll describe each operation with equations using Greek symbols for functions and variables. Note that these representations are simplified and conceptual, aiming to capture the essence of the AES operations rather than detailed algorithmic steps.

### 1. Key Expansion ${\Κappa}$
Given a cipher key $\( k \)$, produce a series of round keys $\( \mathbf{W} \)$ for each round \( r \).

$$\mathbf{W}_r = \text{Κ}(k, r)$$

This involves operations like byte rotation $\( \text{RotWord} \)$, S-box substitution $\( \text{SubWord} \)$, and round constant addition $\( \text{Rcon} \)$ application.

### 2. Add Round Key ${\Αlpha}$
For each byte in the state \( s \) and the round key \( w \), perform an XOR operation.

$$s_{i} = s_{i} \oplus w_{i}, \quad \forall i \in \text{state indices}$$

### 3. SubBytes ${\Sigma}$
For each byte $\( s_i \)$ in the state, apply the S-box transformation $\( \Sigma \)$.

$$s_{i} = \Sigma(s_{i}), \quad \forall i \in \text{state indices}$$

### 4. ShiftRows ${Sigma}$
Shift rows of the state matrix $\( S \)$ by different offsets.

$$S = \text{Σ}(S)$$

Where the shift operation depends on the row index.

### 5. MixColumns $Μ$
For each column $\( c \)$ in the state matrix, apply the MixColumns transformation $\( \text{Μ} \)$.

$$c = \text{Μ}(c), \quad \forall c \in \text{columns of } S$$

Involves polynomial multiplication over $\( \text{GF}(2^8) \)$.

Each of these equations represents a step in the AES encryption process, utilizing transformations and operations defined in the AES specification.


## PSEUDO CODE
Here's a simplified representation of the AES algorithm in pseudo-code format:

```plaintext
KeyExpansion(Key)
initialRound(state, Key[0])
for round = 1 to Nr-1
    SubBytes(state)
    ShiftRows(state)
    MixColumns(state)
    AddRoundKey(state, Key[round])
end for
SubBytes(state)
ShiftRows(state)
AddRoundKey(state, Key[Nr])
```

## Specific function pseudo code examples 
 This pseudocode aims to represent the key operations within the AES encryption process without delving into the detailed mathematics or the specific implementations that would be required in a real-world programming scenario.

### 1. KeyExpansion
```
func KeyExpansion(key []byte) -> [][]byte:
    Initialize an empty array for round keys
    Derive the first round key directly from the input key
    For each round:
        Derive the next round key based on the previous round key and the AES key schedule algorithm
        This includes operations like RotWord, SubWord, and Rcon application for key expansion
    Return the array of round keys
```

### 2. AddRoundKey
```
func AddRoundKey(state, roundKey []byte) -> []byte:
    Initialize a new byte array for the resulting state
    For each byte in the state:
        XOR the byte with the corresponding byte in the roundKey
        Store the result in the new state array
    Return the new state array
```

### 3. SubBytes
```
func SubBytes(state []byte) -> []byte:
    Initialize a new byte array for the resulting state
    For each byte in the state:
        Substitute the byte using the AES S-box
        Store the result in the new state array
    Return the new state array
```

### 4. ShiftRows
```
func ShiftRows(state []byte) -> []byte:
    Perform the row shifting operation on the state matrix
    Shift the first row by 0 (no shift)
    Shift the second row by 1 to the left
    Shift the third row by 2 to the left
    Shift the fourth row by 3 to the left
    Return the modified state as a byte array
```

### 5. MixColumns
```
func MixColumns(state []byte) -> []byte:
    For each column in the state matrix:
        Apply the MixColumns transformation
        This involves multiplying the column by a fixed polynomial in GF(2^8)
    Return the modified state as a byte array
```

These pseudocode snippets provide a high-level overview of each function's purpose within the AES encryption process. The actual implementation of these functions requires a deeper understanding of cryptographic principles, as well as specific algorithms for operations like byte substitution (S-box), row shifting, and column mixing.

## The AES Algorithm Sequence
Various cryptographic communication systems and methods that revolve around encoding (encryption) and decoding (decryption) mechanisms for secure message transmission. Here are the mathematical operations and principles extracted and expressed in LaTeX notation:

 1. **Encoding and Decoding Operations**:
   - Encoding (encryption): $C \equiv M^e \mod n$
   - Decoding (decryption): $M' \equiv C^d \mod n$
   Where $C$ is the ciphertext, $M$ is the plaintext message, $M'$ is the recovered plaintext message, $e$ and $d$ are the encryption and decryption exponents respectively, and $n$ is the modulus, a composite number obtained from two primes $p$ and $q$.

 2. **Key Generation**:
   - The relationship between $e$ and $d$: $ed \equiv 1 \mod \lambda(n)$
   Where $\lambda(n)$ is Carmichael's totient function, providing a value that satisfies the modular multiplication inverse for $e$ and $d$ in the key generation process.

 3. **Public Key Infrastructure (PKI)**:
   - Conditions for public and private keys in a PKI system are discussed, focusing on the computational infeasibility of deriving the private key from the public key.

 4. **Polynomial Evaluation for Encoding and Decoding**:
   - Alternative encoding method: $C = f(M) \mod n$, where $f(M)$ is a polynomial function of $M$.
   - Corresponding decoding operations involve finding roots of polynomial equations modulo $n$ and selecting the correct root based on message structure or additional information.

 5. **Block Transformation**:
   - For long messages that exceed the range of $n$, a blocking system is employed to partition the message into smaller blocks, each of which can be individually encoded or decoded.

 6. **Composite Numbers and Prime Factors**:
   - The security of the system is highlighted as relying on the difficulty of factoring the composite number $n = pq$, where $p$ and $q$ are large prime numbers.

 7. **Use of Chinese Remainder Theorem (CRT)**:
   - Mention of alternative decoding methodologies using the CRT for systems where $n$ is a product of three or more primes.

 8. **Signature and Verification**:
   - A process for signing and verifying messages using the cryptographic system is described, ensuring message authenticity and integrity.

 9. **Practical Considerations**:
   - Discussion on practical implementation aspects of the cryptographic system, including handling of messages larger than the modulus $n$ and the public availability of encryption keys versus the secrecy of decryption keys.

These equations and concepts form the backbone of the cryptographic methods outlined in the patent, emphasizing secure message transmission, the generation and use of cryptographic keys, and the mathematical underpinnings of encryption and decryption processes.


## The AES Patent Claims

In AES encryption, data confidentiality is achieved through the complex interaction of these operations, ensuring the security of the encrypted data against various cryptographic attacks.

| Claim | Summary |
|-------|---------|
| 1 | Introduces an improved method for generating AES-Rijndael cipher's round-key words "on-the-fly" in reverse for decryption. This involves: storing the final set of Nk round-key words after encryption, setting the key generator for decryption, deriving preceding round-key words using XOR operations with modifications for specific conditions, and employing multiple S-boxes with different power consumption signatures for byte substitution, chosen via a pseudo-random generator. |
| 2 | Details the use of a linear feedback shift register as the pseudo-random generator for selecting pathways to different S-boxes during key generation, enhancing security against differential power analysis by varying the hardware pathway used for byte substitution. |
| 3 | Describes a countermeasure against differential power analysis in AES hardware implementations. A dummy circuit, which matches the delay of the pre-mix subcircuit, uses a pseudo-random generator and XOR array to inject noise into the power signature during the initial XOR operation, blending the encryption process's power usage patterns. |
| 4 | Specifies that the pseudo-random generator in the dummy circuit comprises a set of linear feedback shift registers, further detailing the internal mechanism for generating pseudo-random noise. |
| 5 | States that the pseudo-random generator and XOR array in the dummy circuit have the same word width as the pre-mix subcircuit, ensuring that the dummy operation mimics the actual encryption process in terms of data handling and timing. |
| 6 | Proposes a method that combines the initial pre-mix XOR operation with the first cipher encryption round for efficiency. This involves pre-processing the cipher key to generate the first round-key words while loading the plaintext, thereby executing the first encryption round immediately after the pre-mix operation. |
