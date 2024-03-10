
### RSA Cryptographic Claims Summary



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
