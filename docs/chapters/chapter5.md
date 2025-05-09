# Chapter 5: Algorithms
# Quantum Computing - Expanded Lecture Summaries
### Sharat Batra
### March 15, 2025 

## Lecture 3: Bloch Sphere, Eigenstates, Eigenvectors, Projection Operator


### Key Algorithms

## Superdense Coding with Bell States
Key Insight
Superdense coding demonstrates how entanglement + quantum operations + classical communication can double the classical communication capacity of a quantum channel. It is a powerful example of quantum advantage and plays a central role in quantum communication and information theory.



In superdense coding, Alice and Bob share an entangled Bell state initially:

Great! Here's the **revised Markdown with LaTeX equations** for your lecture section on **superdense coding**, using **standard Dirac (ket) notation** for all 4 Bell states, and fully compatible with VS Code PDF rendering:

---

```markdown
# Superdense Coding

In **superdense coding**, Alice and Bob share an entangled qubit pair in the Bell state:

$$
\left| \Phi^+ \right\rangle = \frac{1}{\sqrt{2}} \left( \left|00\right\rangle + \left|11\right\rangle \right)
$$

Alice can send **two classical bits** of information by applying one of four unitary operations to her qubit and then sending it to Bob. The shared entangled state allows Bob to recover two bits from just one qubit transmission.

## Bell States

The four Bell states used in superdense coding are:

$$
\begin{aligned}
\left| \Phi^+ \right\rangle &= \frac{1}{\sqrt{2}} \left( \left|00\right\rangle + \left|11\right\rangle \right) \\
\left| \Phi^- \right\rangle &= \frac{1}{\sqrt{2}} \left( \left|00\right\rangle - \left|11\right\rangle \right) \\
\left| \Psi^+ \right\rangle &= \frac{1}{\sqrt{2}} \left( \left|01\right\rangle + \left|10\right\rangle \right) \\
\left| \Psi^- \right\rangle &= \frac{1}{\sqrt{2}} \left( \left|01\right\rangle - \left|10\right\rangle \right)
\end{aligned}
$$

## Encoding Scheme

Alice applies one of four operations to her qubit, depending on the 2-bit classical message she wants to send:

| Classical Bits | Operation (on Alice's qubit) | Resulting State |
|----------------|------------------------------|------------------|
| 00             | $I$ (Identity)               | $\left| \Phi^+ \right\rangle$ |
| 01             | $X$ (Bit flip)               | $\left| \Psi^+ \right\rangle$ |
| 10             | $Z$ (Phase flip)             | $\left| \Phi^- \right\rangle$ |
| 11             | $iY$ (Bit and phase flip)    | $\left| \Psi^- \right\rangle$ |

The resulting state is then sent to Bob.

## Alice's Encoding Operations (Step-by-Step)

- **Message 00**:
  $$
  (I \otimes I) \left| \Phi^+ \right\rangle = \left| \Phi^+ \right\rangle
  $$

- **Message 01**:
  $$
  (X \otimes I) \left| \Phi^+ \right\rangle = \left| \Psi^+ \right\rangle
  $$

- **Message 10**:
  $$
  (Z \otimes I) \left| \Phi^+ \right\rangle = \left| \Phi^- \right\rangle
  $$

- **Message 11**:
  $$
  (Y \otimes I) \left| \Phi^+ \right\rangle = i \left| \Psi^- \right\rangle
  $$

> Note: The global phase $i$ does not affect measurement outcomes.

## Bob’s Decoding Procedure

After receiving the qubit from Alice, Bob performs the **reverse entanglement operations** to recover the original 2 classical bits:

1. Apply **CNOT** gate with Alice's qubit as control and Bob's as target.
2. Apply **Hadamard gate** to Alice’s qubit.

This transforms each Bell state to a unique computational basis state:

$$
\begin{aligned}
\left| \Phi^+ \right\rangle &\rightarrow \left|00\right\rangle \\
\left| \Psi^+ \right\rangle &\rightarrow \left|01\right\rangle \\
\left| \Phi^- \right\rangle &\rightarrow \left|10\right\rangle \\
\left| \Psi^- \right\rangle &\rightarrow \left|11\right\rangle
\end{aligned}
$$

Bob then measures the two qubits in the computational basis and perfectly retrieves Alice’s 2-bit message.
