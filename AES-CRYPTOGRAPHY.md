# AES Encryption 
AES is a symmetric block cipher that encrypts and decrypts data in fixed-size blocks (128 bits) using cryptographic keys of 128, 192, or 256 bits. The core operations in AES include SubBytes, ShiftRows, MixColumns, and AddRoundKey, executed over multiple rounds. The number of rounds depends on the key size: 10 rounds for 128-bit keys, 12 rounds for 192-bit keys, and 14 rounds for 256-bit keys.

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

In AES encryption, data confidentiality is achieved through the complex interaction of these operations, ensuring the security of the encrypted data against various cryptographic attacks.

| Claim | Summary |
|-------|---------|
| 1 | Introduces an improved method for generating AES-Rijndael cipher's round-key words "on-the-fly" in reverse for decryption. This involves: storing the final set of Nk round-key words after encryption, setting the key generator for decryption, deriving preceding round-key words using XOR operations with modifications for specific conditions, and employing multiple S-boxes with different power consumption signatures for byte substitution, chosen via a pseudo-random generator. |
| 2 | Details the use of a linear feedback shift register as the pseudo-random generator for selecting pathways to different S-boxes during key generation, enhancing security against differential power analysis by varying the hardware pathway used for byte substitution. |
| 3 | Describes a countermeasure against differential power analysis in AES hardware implementations. A dummy circuit, which matches the delay of the pre-mix subcircuit, uses a pseudo-random generator and XOR array to inject noise into the power signature during the initial XOR operation, blending the encryption process's power usage patterns. |
| 4 | Specifies that the pseudo-random generator in the dummy circuit comprises a set of linear feedback shift registers, further detailing the internal mechanism for generating pseudo-random noise. |
| 5 | States that the pseudo-random generator and XOR array in the dummy circuit have the same word width as the pre-mix subcircuit, ensuring that the dummy operation mimics the actual encryption process in terms of data handling and timing. |
| 6 | Proposes a method that combines the initial pre-mix XOR operation with the first cipher encryption round for efficiency. This involves pre-processing the cipher key to generate the first round-key words while loading the plaintext, thereby executing the first encryption round immediately after the pre-mix operation. |
