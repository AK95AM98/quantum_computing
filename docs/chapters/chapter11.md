# Chapter 11: LatexA
This is a simple document with LaTeX rendering.
$$
E = mc^2
$$

\section*{Lecture 11: Quantum Gates and Operators}

\subsection*{Pauli-X Gate}
The Pauli-X gate can be represented in terms of the Hadamard (\(H\)) and Pauli-Z (\(Z\)) gates as:

\begin{equation}
    X = H Z H
\end{equation}

Matrix representation of the Pauli-X gate:

\begin{equation}
    X = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
\end{equation}

\subsection*{Hadamard Gate}
The Hadamard gate transforms the basis states as follows:

\begin{equation}
    H|0\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle), \quad
    H|1\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)
\end{equation}

Matrix representation:

\begin{equation}
H = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 & 1 \\ 1 & -1 \end{bmatrix}
\end{equation}

\subsection*{Bloch Sphere Representation}
A qubit state can be visualized on the Bloch Sphere and is given by:

\begin{equation}
    |\psi\rangle = \cos\frac{\theta}{2}|0\rangle + e^{i\phi} \sin\frac{\theta}{2}|1\rangle
\end{equation}

where:
\begin{itemize}
    \item \( \theta \) represents the polar angle, determining the probability distribution between \( |0\rangle \) and \( |1\rangle \).
    \item \( \phi \) represents the phase difference between \( |0\rangle \) and \( |1\rangle \).
\end{itemize}

\subsection*{Eigenstates and Operators}

\textbf{Pauli-Z Operator:}

\begin{equation}
    Z|0\rangle = +|0\rangle, \quad Z|1\rangle = -|1\rangle
\end{equation}

Matrix representation:

\begin{equation}
    Z = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}
\end{equation}

\subsection*{Projection Operators}
Projection operators for measuring in the computational basis:

\begin{equation}
    \mathbf{P}_0 = |0\rangle\langle0| = \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}, \quad
    \mathbf{P}_1 = |1\rangle\langle1| = \begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix}
\end{equation}

Measurement probabilities for a general qubit state \( \psi = \alpha|0\rangle + \beta|1\rangle \):

\begin{equation}
    P(|0\rangle) = |\alpha|^2, \quad P(|1\rangle) = |\beta|^2
\end{equation}

\subsection*{CNOT Gate (Controlled-NOT)}
Matrix representation of the Controlled-NOT (CNOT) gate:

\begin{equation}
    \text{CNOT} = \begin{bmatrix} 
        1 & 0 & 0 & 0 \\ 
        0 & 1 & 0 & 0 \\ 
        0 & 0 & 0 & 1 \\ 
        0 & 0 & 1 & 0 
    \end{bmatrix}
\end{equation}

\section*{Lecture 11: Quantum Gates and Operators}

\subsection*{Pauli-X Gate}
The Pauli-X gate can be represented in terms of the Hadamard (\(H\)) and Pauli-Z (\(Z\)) gates as:

\begin{equation}
    X = H Z H
\end{equation}

\begin{equation}
    X = H Z H
\end{equation}