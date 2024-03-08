
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
