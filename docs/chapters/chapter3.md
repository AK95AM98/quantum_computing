# Chapter 3: Teleportation
Here is the complete question along with its detailed solution:
### **Problem Description**  

The goal of this problem is to analyze and demonstrate a quantum teleportation protocol involving three parties: **Alice, Bob, and Charlie**. The task is to verify whether a shared entangled state can be successfully transferred from Alice to Bob and Charlie, ensuring that the final state is preserved.  

### **Initial Quantum State of Alice, Bob, and Charlie**  

We begin with a **three-qubit system**, where Alice initially possesses **two qubits** (denoted as \( A1 \) and \( A2 \)), while Charlie and Bob each have **one qubit** (denoted as \( C \) and \( B \), respectively).  

- Alice has a **two-qubit entangled state** \( |\Psi\rangle_{A1C} \) with Charlie.  
- Bob and Alice also share a **maximally entangled Bell state** \( |\phi^+\rangle_{A2B} \).  

Thus, the **initial state** before the protocol starts is given by:  

\[
|\Psi\rangle_{A1C} \otimes |\phi^+\rangle_{A2B}
\]

where:  

\[
|\Psi\rangle_{A1C} = \alpha |00\rangle + \beta |01\rangle + \gamma |10\rangle + \delta |11\rangle
\]

represents the **unknown quantum state** shared between Alice and Charlie, and  

\[
|\phi^+\rangle_{A2B} = \frac{1}{\sqrt{2}} \big(|00\rangle + |11\rangle \big)
\]

represents the **pre-shared Bell pair** between Alice and Bob.  

Expanding this tensor product, the **full initial state** of the system becomes:  

\[
|\Psi\rangle_{A1C} \otimes |\phi^+\rangle_{A2B} = \frac{1}{\sqrt{2}} \big( \alpha |0000\rangle + \alpha |0011\rangle + \beta |0100\rangle + \beta |0111\rangle + \gamma |1000\rangle + \gamma |1011\rangle + \delta |1100\rangle + \delta |1111\rangle \big)
\]

where the qubits are ordered as \( A1, A2, C, B \).

### **Objective**  

Alice will apply a series of quantum operations (CNOT and Hadamard), measure her qubits, and communicate the results to Bob, who will then apply **correction unitaries** to ensure that Bob and Charlie recover the original state \( |\Psi\rangle_{CB} \). The goal is to prove that the **entangled state is successfully teleported**, preserving its properties.  

Stated below as:
### **Question 1**  

Alice, Bob, and Charlie share a quantum system where Alice holds two qubits (\(A1, A2\)), Bob holds one qubit (\(B\)), and Charlie holds one qubit (\(C\)). Alice wants to transfer an unknown quantum state \( |\Psi\rangle \) to Bob and Charlie using quantum teleportation.  

#### **Initial State of the System:**  
Alice’s first qubit \(A1\) and Charlie’s qubit \(C\) are entangled in an unknown quantum state:  

\[
|\Psi\rangle_{A1C} = \alpha |00\rangle + \beta |01\rangle + \gamma |10\rangle + \delta |11\rangle
\]

where \(\alpha, \beta, \gamma, \delta\) are complex coefficients satisfying the normalization condition:  

\[
|\alpha|^2 + |\beta|^2 + |\gamma|^2 + |\delta|^2 = 1
\]

Additionally, Alice’s second qubit (\(A2\)) and Bob’s qubit (\(B\)) are entangled in a **maximally entangled Bell state**:  

\[
|\phi^+\rangle_{A2B} = \frac{1}{\sqrt{2}} (|00\rangle + |11\rangle)
\]

Thus, the total **initial state** of the system before Alice applies any operations is:  

\[
|\Psi\rangle_{A1C} \otimes |\phi^+\rangle_{A2B} = \frac{1}{\sqrt{2}} \Big( \alpha |0000\rangle + \alpha |0011\rangle + \beta |0100\rangle + \beta |0111\rangle + \gamma |1000\rangle + \gamma |1011\rangle + \delta |1100\rangle + \delta |1111\rangle \Big)
\]

### **Solution**  

#### **Step 1: Alice Applies a CNOT Gate on Her Qubits**  

Alice applies a **CNOT gate** on her qubits \( A1 \) (control) and \( A2 \) (target). The CNOT operation flips the target qubit if the control qubit is \( |1\rangle \).  

Applying CNOT to \( A1 \) (control) and \( A2 \) (target):  

\[
\frac{1}{\sqrt{2}} \Big( \alpha |0000\rangle + \alpha |0011\rangle + \beta |0100\rangle + \beta |0111\rangle + \gamma |1100\rangle + \gamma |1111\rangle + \delta |1000\rangle + \delta |1011\rangle \Big)
\]

#### **Step 2: Alice Applies a Hadamard Gate on Her First Qubit (A1)**  

The Hadamard gate creates a superposition:  

\[
H |0\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle), \quad H |1\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)
\]

Applying Hadamard on \( A1 \):  

\[
\frac{1}{2} \Big[ |0\rangle \big( \alpha |000\rangle + \alpha |011\rangle + \beta |010\rangle + \beta |001\rangle + \gamma |110\rangle + \gamma |101\rangle + \delta |100\rangle + \delta |111\rangle \big) 
\]

\[
+ |1\rangle \big( \alpha |000\rangle + \alpha |011\rangle + \beta |010\rangle + \beta |001\rangle - \gamma |110\rangle - \gamma |101\rangle - \delta |100\rangle - \delta |111\rangle \big) \Big]
\]

This transformation entangles Alice’s qubits, preparing them for measurement.

#### **Step 3: Alice Measures Her Qubits**  

Alice measures her two qubits (\(A1, A2\)) in the **computational basis** (\(|00\rangle, |01\rangle, |10\rangle, |11\rangle\)). The system collapses into one of four possible states, and Bob must apply a correction based on Alice’s result.  

Possible outcomes and remaining states for Bob and Charlie:  

1. If Alice measures **\( |00\rangle \)**:  
\[ 
$|\Psi\rangle_{CB} = \alpha |00\rangle + \beta |01\rangle + \gamma |10\rangle + \delta |11\rangle$
\]
   → **No correction needed**. 

2. If Alice measures **\( |01\rangle \)**:  
\[
   $|\Psi\rangle_{CB} = \alpha |00\rangle + \beta |01\rangle - \gamma |10\rangle - \delta |11\rangle$
\]
   → **Bob applies \( Z \) correction**.  

3. If Alice measures **\( |10\rangle \)**:  
   \[
   $|\Psi\rangle_{CB} = \alpha |10\rangle + \beta |11\rangle + \gamma |00\rangle + \delta |01\rangle$
   \]
   → **Bob applies \( X \) correction**.  

4. If Alice measures **\( |11\rangle \)**:  
   \[
   $|\Psi\rangle_{CB} = \alpha |10\rangle + \beta |11\rangle - \gamma |00\rangle - \delta |01\rangle$
   \]
   → **Bob applies \( XZ \) correction**.  

#### **Step 4: Bob’s Correction Based on Alice’s Measurement**  

Alice **sends her measurement results** (2 classical bits) to Bob:  
- \( |00\rangle \) → No correction.  
- \( |01\rangle \) → Apply \( Z \).  
- \( |10\rangle \) → Apply \( X \).  
- \( |11\rangle \) → Apply \( XZ \).  

After Bob applies the necessary corrections, he and Charlie now share the original state \( |\Psi\rangle_{CB} \), successfully completing the quantum teleportation protocol.  

---

### **Conclusion**  

This process successfully transfers a quantum state using **entanglement and classical communication**:  

1. **Pre-shared entanglement** between Alice & Bob.  
2. **Quantum operations (CNOT, Hadamard)** applied by Alice.  
3. **Measurement** of Alice’s qubits.  
4. **Classical communication** of Alice’s measurement results to Bob.  
5. **Bob’s unitary correction operations** based on the received classical bits.  

Thus, the quantum state \( |\Psi\rangle \) is teleported from Alice to Bob and Charlie.
