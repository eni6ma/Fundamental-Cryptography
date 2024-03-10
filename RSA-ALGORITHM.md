
### RSA Cryptographic Claims Summary

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
