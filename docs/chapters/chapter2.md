# Chapter 2: Basis of quantum
## Introduction to Quantum Computing and Physical Basics of Computing 
### Sharat Batra
### March 15, 2025 


## Class Lecture: Fundamental Quantum Computing Concepts  

Good morning, everyone! Today we're going to explore some fundamental concepts in quantum computing that help us understand how quantum systems differ from classical systems and the unique properties of quantum operations.  

## Information Scaling in Classical vs. Quantum Computing  

**Question:** How does the information content of a computing system scale under classical vs. quantum computing with each extra (q)bit added to the system? How does the picture change after measurement?  

In **classical computing**, we work with bits that can be either 0 or 1. When we add bits to a classical system, the number of possible configurations scales as \( 2^n \), where \( n \) is the number of bits. Each additional bit doubles the number of possible states the system can represent.  

For example:  

- 1 bit: 2 possible states (0 or 1)  
- 2 bits: 4 possible states (00, 01, 10, 11)  
- 3 bits: 8 possible states  

However, in **quantum computing**, qubits can exist in **superposition** states, meaning an \( n \)-qubit system can represent \( 2^n \) states **simultaneously**. This property creates **exponential scaling potential**.  

Upon **measurement**, the superposition collapses to a **single classical outcome**, meaning we retrieve only one of the possible configurations, reducing the quantum advantage to a classical state.  

## Quantum Gates and the Bloch Sphere  

**Question:** Each quantum gate transforms the input state (i.e., the point on the Bloch sphere) to the output state. Each point on the surface of the sphere can represent the outcome of a transformation, thus an infinite number of quantum gates exist. Does this hold for all quantum gates, for an arbitrary number of qubits?  

For **single-qubit systems**, the Bloch sphere provides a complete visualization. Any pure quantum state can be represented as a point on the sphere. Single-qubit quantum gates correspond to rotations or transformations on this sphere. Since these transformations are **continuous** (described by **unitary matrices**), there are **infinitely many possible single-qubit quantum gates**.  

For **multi-qubit systems**, the Bloch sphere representation no longer suffices. A **two-qubit system** requires a **4-dimensional complex vector space**, making it impossible to represent on a simple sphere. Instead, quantum gates operate within this **higher-dimensional space** using **unitary transformations** such as the **CNOT gate**, which entangles qubits and cannot be represented solely on the Bloch sphere.  

## Measurement Gates and Unitarity  

**Question:** Does the measurement gate represent a unitary operation?  

The answer is **no**. Measurement is **not** a unitary operation because:  

1. **Unitary operations preserve probability** (\( U^{\dagger} U = I \)).  
2. **Unitary operations are reversible**, meaning we can determine the input state from the output state.  

Measurement collapses a quantum state into one of the basis states, irreversibly reducing the quantum superposition into a classical outcome. For example, measuring a qubit in the state  

$$
\ket{\Psi} = \alpha \ket{0} + \beta \ket{1}
$$  

yields:  

- \( \ket{0} \) with probability \( |\alpha|^2 \)  
- \( \ket{1} \) with probability \( |\beta|^2 \)  

Since measurement fundamentally changes the system and does not allow for state recovery, it is a **non-unitary operation**.  

## Example: Common Quantum Gates as Matrices  

Below are representations of some important quantum gates as matrices:  

## Pauli-X Gate Matrix

- **Pauli-X (NOT Gate):**  

$$
X = \begin{bmatrix} 
0 & 1 \\
1 & 0 
\end{bmatrix}
$$

- **Pauli-Y Gate:**  

$$
  Y =
  \begin{bmatrix}
  0 & -i \\
  i & 0
  \end{bmatrix}
$$  

- **Pauli-Z Gate:**  

$$
  Z =
  \begin{bmatrix}
  1 & 0 \\
  0 & -1
  \end{bmatrix}
$$  

- **Hadamard Gate:**  

$$
  H =
  \frac{1}{\sqrt{2}}
  \begin{bmatrix}
  1 & 1 \\
  1 & -1
  \end{bmatrix}
$$  

- **CNOT (Controlled-NOT) Gate:**  

$$
  CNOT =
  \begin{bmatrix}
  1 & 0 & 0 & 0 \\
  0 & 1 & 0 & 0 \\
  0 & 0 & 0 & 1 \\
  0 & 0 & 1 & 0
  \end{bmatrix}
$$  

- **General Unitary Transformation for a Single Qubit:**  

$$
  U =
  \begin{bmatrix}
  a & b \\
  c & d
  \end{bmatrix}, \quad \text{where} \quad U^{\dagger} U = I
$$  

**Final Thoughts:** Any questions before we move on to our next topic? These concepts form the foundation of how we think about quantum information processing and the differences between quantum and classical computing paradigms.  

# Scaling of Information in Classical vs. Quantum Computing  

- **Classical computing** scales **linearly**, with each additional bit **doubling** the number of possible states. An \( n \)-bit system has \( 2^n \) possible configurations.  
- **Quantum computing** scales **exponentially**, as an \( n \)-qubit system can exist in a **superposition** of \( 2^n \) states simultaneously before measurement.  
- **After measurement**, a quantum system collapses to a **classical state**, losing the exponential advantage in terms of information storage but retaining computational benefits like **entanglement** and **interference**.  

# Quantum Gates and State Transformations on the Bloch Sphere  

- **Single-qubit gates** perform **unitary transformations**, moving a quantum state on the **Bloch sphere**. Since these transformations are **continuous**, **infinitely many single-qubit gates exist**.  
- **Multi-qubit gates** operate in a **higher-dimensional Hilbert space**, making **Bloch sphere visualization impractical beyond one qubit**.  
  - While the concept of **unitary transformations** still applies, **multi-qubit interactions** (e.g., the **CNOT gate**) involve **entanglement** and more complex transformations.  
