# Chapter 21: Try1
# Quantum Computing - Expanded Lecture Summaries

## Lecture 3: Bloch Sphere, Eigenstates, Eigenvectors, Projection Operator


### Key Concepts

## Pauli-X Gate Matrix

The Pauli-X gate matrix is:

$$
X = \begin{bmatrix} 
0 & 1 \\
1 & 0 
\end{bmatrix}
$$

## Hadamard Gate Matrix

The Hadamard gate matrix is:

$$
H = \frac{1}{\sqrt{2}} \begin{bmatrix} 
1 & 1 \\
1 & -1 
\end{bmatrix}
$$

#### Pauli-X Gate Identity
The Pauli-X (NOT) gate satisfies the identity:

$$
X = HZH
$$
where \(H\) is the Hadamard gate.

The Pauli-X gate matrix representation:

$$
X = \begin{bmatrix} 
0 & 1 \\
1 & 0 
\end{bmatrix}
$$

#### Hadamard Transform
The Hadamard gate creates superposition states:

$$
H|0\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle), \quad H|1\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)
$$

Matrix representation:

$$
H = \frac{1}{\sqrt{2}} \begin{bmatrix} 
1 & 1 \\
1 & -1 
\end{bmatrix}
$$

#### Pauli-Z Gate Identity
The Pauli-Z gate affects the phase of a qubit:

$$
Z|0\rangle = |0\rangle, \quad Z|1\rangle = -|1\rangle
$$

Matrix representation:

$$
Z = \begin{bmatrix} 
1 & 0 \\
0 & -1 
\end{bmatrix}
$$

#### Projection Operator
The projection operator for a qubit basis state:

$$
P_0 = |0\rangle\langle0| = \begin{bmatrix} 
1 & 0 \\
0 & 0 
\end{bmatrix}, \quad P_1 = |1\rangle\langle1| = \begin{bmatrix} 
0 & 0 \\
0 & 1 
\end{bmatrix}
$$

#### Two-Qubit States and Matrices
A general two-qubit state:

$$
|\psi\rangle = c_{00}|00\rangle + c_{01}|01\rangle + c_{10}|10\rangle + c_{11}|11\rangle
$$

Matrix representation:

$$
|\psi\rangle = \begin{bmatrix} 
c_{00} \\
c_{01} \\
c_{10} \\
c_{11} 
\end{bmatrix}
$$

#### Toffoli Gate (CCNOT)
A three-qubit gate that flips the target qubit if both control qubits are \( |1\rangle \).

Matrix representation:

$$
\text{Toffoli} = \begin{bmatrix}
1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & 0
\end{bmatrix}
$$
