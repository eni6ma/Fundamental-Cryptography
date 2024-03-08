
```mermaid
sequenceDiagram
    participant User
    participant AES
    participant KeySchedule
    participant State
    participant SubBytes
    participant ShiftRows
    participant MixColumns
    participant AddRoundKey
    participant Output

    User->>AES: Plaintext
    AES->>KeySchedule: GenerateRoundKeys
    loop Main Rounds
        AES->>State: Initial State
        State->>SubBytes: SubBytes
        SubBytes->>ShiftRows: ShiftRows
        ShiftRows->>MixColumns: MixColumns
        MixColumns->>AddRoundKey: AddRoundKey
        AddRoundKey->>State: Next State
    end
    AES->>State: Final State
    State->>SubBytes: SubBytes
    SubBytes->>ShiftRows: ShiftRows
    ShiftRows->>AddRoundKey: AddRoundKey
    AddRoundKey->>Output: Ciphertext

```

## Greek Symbol Key
- $\alpha$: Input variables, representing initial values or keys.
- $\Phi$: General transformation or function.
- $\Psi$: XOR logic operation or another binary operation.
- $\Lambda$: Function for key generation.
- $\Omega$: Encryption function.
- $\Theta$: Decryption function.
- $\eta, \xi$: Large prime numbers or composite numbers.
- $\Gamma$: Function for pseudo-random values or sequences.


```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    participant Eve

    Alice->>Bob: Generate private key a
    Bob->>Alice: Generate private key b
    Alice->>Bob: Send public key A = g^a mod p
    Bob->>Alice: Send public key B = g^b mod p
    Alice->>Eve: Intercept public key B
    Alice->>Bob: Calculate shared secret s = B^a mod p
    Bob->>Alice: Calculate shared secret s = A^b mod p
```

This sequence diagram illustrates the Diffie-Hellman key exchange algorithm. Both Alice and Bob generate their private keys (a and b, respectively) and then exchange their public keys calculated using these private keys. The shared secret is then independently computed by each party using the other party's public key and their own private key.
