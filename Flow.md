
Here's the Mermaid diagram for the secret commitment ceremony algorithm including Alice, Bob, and Victor stages:

```mermaid
graph TD
    subgraph Alice
        A[Choose secret value s]
        B[Compute commitment to s]
        C[Send commitment to Victor]
    end
    subgraph Bob
        D[Choose secret value r]
        E[Compute commitment to r]
        F[Send commitment to Victor]
    end
    subgraph Victor
        G[Receive commitments from Alice and Bob]
        H[Send challenge to Alice and Bob]
        I[Receive responses from Alice and Bob]
        J[Verify responses and commitments]
        K[Announce result]
    end
    A --> B
    B --> C
    D --> E
    E --> F
    C --> G
    F --> G
    G --> H
    H --> I
    I --> J
    J --> K
``` 

This diagram illustrates the process of a secret commitment ceremony involving Alice, Bob, and Victor, including the stages of choosing secret values, computing commitments, sending commitments to Victor, Victor receiving commitments, sending challenges, receiving responses, verifying responses and commitments, and announcing the result.

----

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

----

```mermaid
sequenceDiagram
    participant Alice
    participant Bob

    Alice->>Bob: Generate two large prime numbers p and q
    Alice->>Bob: Calculate n = p * q
    Alice->>Bob: Choose e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
    Alice->>Bob: Publish n and e as the public key
    Bob->>Alice: Encrypt message M using Alice's public key (n, e)
    Bob-->>Alice: Send the encrypted message C
    Alice->>Bob: Decrypt the message C using her private key
```

This sequence diagram illustrates the RSA key exchange algorithm. Alice generates two large prime numbers, calculates the public modulus (n), chooses a public exponent (e), and publishes these as her public key. Bob encrypts a message using Alice's public key and sends it to Alice. Alice decrypts the message using her private key.

----

The  diagram depicting a basic Sigma Schnorr ceremony algorithm, including the commitment stage:

```mermaid
graph TD
    subgraph Prover
        A[Choose random value k]
        B[Compute commitment to k]
        C[Compute challenge]
        D[Compute response]
    end
    subgraph Verifier
        E[Send commitment to k]
        F[Verify commitment]
        G[Send challenge]
        H[Verify challenge]
        I[Send response]
        J[Verify response]
    end
    A --> B
    B --> E
    E --> F
    F -->|Acceptance or rejection of commitment| G
    G --> H
    H --> I
    I --> J
    J -->|Acceptance or rejection of proof| D
    D -->|Repeat with new k if rejected| A

``` 

This diagram illustrates the Sigma Schnorr ceremony algorithm. The Prover first selects a random value \( k \) and computes a commitment to it. Then, the Prover and Verifier interact to verify the commitment, generate a challenge based on the message and commitment, and respond accordingly. The Verifier ultimately verifies the response and either accepts or rejects the proof. If rejected, the Prover repeats the process with a new random value \( k \).

```mermaid
sequenceDiagram
    participant Prover
    participant Verifier

    Prover->>Prover: Generate a random private key x
    Prover->>Prover: Compute corresponding public key h = g^x mod p
    Prover->>Verifier: Send public key h
    Verifier->>Prover: Challenge c
    Prover->>Prover: Compute response r = x + c * w mod q
    Prover->>Verifier: Send response r
    Verifier->>Verifier: Verify if g^r * h^c mod p equals v
```

This sequence diagram illustrates Schnorr's Sigma algorithm. The Prover generates a random private key, computes the corresponding public key, and sends it to the Verifier. The Verifier then sends a challenge to the Prover. The Prover computes a response based on the challenge and sends it back to the Verifier. Finally, the Verifier verifies the response based on predefined criteria.


----


```mermaid
graph TD
    subgraph Prover
        A[Choose secret value s]
        B[Compute commitment to s]
        C[Choose random value r]
        D[Compute response]
    end
    subgraph Verifier
        E[Send commitment to s]
        F[Verify commitment]
        G[Send response]
        H[Verify response]
    end
    A --> B
    B --> E
    E --> F
    F -->|Acceptance or rejection of commitment| A
    A --> C
    C --> G
    G --> H
    H -->|Acceptance or rejection of proof| D
``` 

This  mermaid diagram illustrates a basic Zero-Knowledge Proof (ZKP) algorithm, including the commitment stage. The Prover first selects a secret value and computes a commitment to it. This commitment is then sent to the Verifier, who verifies it. After verification, the Prover generates a response based on a challenge from the Verifier and sends it back. Finally, the Verifier verifies the response and either accepts or rejects the proof.

----

```mermaid
sequenceDiagram
    participant Prover
    participant Verifier

    Prover->>Prover: Choose secret value s
    Prover->>Prover: Compute commitment to s: commit(s)
    Prover->>Verifier: Send commitment to s
    Verifier->>Verifier: Verify commitment
    Verifier-->>Prover: Acceptance or rejection of commitment

    Prover->>Prover: Choose random value r
    Prover->>Prover: Compute response: response = s + r * challenge
    Prover->>Verifier: Send response
    Verifier->>Verifier: Verify response
    Verifier-->>Prover: Acceptance or rejection of proof
```

This sequence diagram outlines a basic Zero-Knowledge Proof (ZKP) algorithm, including the commitment stage. The Prover selects a secret value and computes a commitment to it, which is sent to the Verifier. After verifying the commitment, the Verifier either accepts or rejects it. Then, the Prover generates a response based on a challenge from the Verifier, which is sent back for verification. Finally, the Verifier evaluates the response and either accepts or rejects the proof.
