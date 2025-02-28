# Chapter 1: Introduction
\documentclass{article}
\usepackage{amsmath, amssymb, graphicx}
\usepackage{qcircuit}

\title{Lecture 1: Fundamentals of Quantum States and Measurements}
\date{February 24, 2025}

\begin{document}
\maketitle

\section{Introduction}
Quantum computing relies on quantum mechanics principles to manipulate information. This lecture introduces:
\begin{itemize}
    \item Basis and Orthonormal Basis
    \item Bra-Ket Notation (Dirac Notation)
    \item Quantum Measurement
    \item Representing a state in different basis sets
\end{itemize}

\section{Basis and Orthonormal Basis}
A basis is a set of vectors that spans a vector space. Any vector in that space can be expressed as a linear combination of basis vectors.
For example, in $\mathbb{R}^2$, the standard basis is:
$$
e_1 = \begin{bmatrix}1\0\end{bmatrix}, \quad e_2 = \begin{bmatrix}0\1\end{bmatrix}
$$

A vector $v \in \mathbb{R}^2$ can be written as:
\[
    v = a e_1 + b e_2
\]
A basis is orthonormal if:
\begin{enumerate}
    \item The basis vectors are orthogonal: $\langle e_i | e_j \rangle = 0$ for $i \neq j$.
    \item The basis vectors are normalized: $\langle e_i | e_i \rangle = 1$.
\end{enumerate}
The computational basis for qubits is:
\[
    |0\rangle = \begin{bmatrix}1\\0\end{bmatrix}, \quad |1\rangle = \begin{bmatrix}0\\1\end{bmatrix}
\]

\section{Bra-Ket Notation (Dirac Notation)}
\begin{itemize}
    \item A ket $|\psi\rangle$ represents a column vector in Hilbert space.
    \item A bra $\langle \psi|$ is the conjugate transpose (row vector).
\end{itemize}
Example:
\[
    |\psi\rangle = \begin{bmatrix}a\\b\end{bmatrix}, \quad \langle \psi| = \begin{bmatrix}a^* & b^*\end{bmatrix}
\]
Inner product:
\[
    \langle \phi | \psi \rangle = \sum_i \phi^*_i \psi_i
\]
Outer product:
\[
    |\psi\rangle \langle \phi|
\]

\section{Quantum Measurement}
A qubit state can be written as:
\[
    |\psi\rangle = \alpha |0\rangle + \beta |1\rangle
\]
where $\alpha, \beta$ are complex numbers satisfying $|\alpha|^2 + |\beta|^2 = 1$.
When measured in the computational basis:
\begin{itemize}
    \item $|0\rangle$ occurs with probability $|\alpha|^2$.
    \item $|1\rangle$ occurs with probability $|\beta|^2$.
\end{itemize}
Example:
\[
    |\psi\rangle = \frac{1}{\sqrt{2}} |0\rangle + \frac{1}{\sqrt{2}} |1\rangle
\]
Measurement results in $|0\rangle$ or $|1\rangle$ with equal probability.

\section{Representing a State in Different Basis Sets}
Besides the computational basis, we can use:
\subsection{Hadamard Basis}
\[
    |+\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}, \quad |-\rangle = \frac{|0\rangle - |1\rangle}{\sqrt{2}}
\]
\subsection{Eigenbasis of Pauli-X}
Eigenvectors:
\[
    X = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
\]
\[
    |+\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}, \quad |-\rangle = \frac{|0\rangle - |1\rangle}{\sqrt{2}}
\]

\section{Python and Qiskit Implementation}
\begin{verbatim}
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_bloch_vector
import numpy as np

# Define a quantum circuit with one qubit
qc = QuantumCircuit(1)
qc.h(0)  # Apply Hadamard gate
qc.measure_all()

# Simulate
simulator = Aer.get_backend('aer_simulator')
result = execute(qc, simulator, shots=1000).result()
counts = result.get_counts()
print("Measurement Results:", counts)

def plot_state():
    plot_bloch_vector([1/np.sqrt(2), 0, 1/np.sqrt(2)])  # |+> state
plot_state()
\end{verbatim}

\section{Summary}
\begin{itemize}
    \item Basis and Orthonormal Basis: Computational and Hadamard basis.
    \item Bra-Ket Notation: Representation of quantum states.
    \item Measurement: Probabilistic collapse to basis states.
    \item Different Basis Representations: Transforming states across different bases.
\end{itemize}

\end{document}
