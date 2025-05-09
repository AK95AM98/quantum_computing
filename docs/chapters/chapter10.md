# Tutorial - Unitary matrices and orthonormal basis 
# CS4268 - Quantum Computing Tutorial - 1

## General Information
- **Inline equations** to be wrapped in single dollar signs ($).
- **Block equations** to be wrapped in double dollar signs ($$).

---

Here is the **LaTeX-formatted Markdown** version for your Quantum Computing Tutorial:

---

## **General Information (Useful for All Questions)**

- **Stochastic Matrix**: A square matrix is stochastic if and only if:
  1. All its entries are non-negative reals.
  2. The entries of each of its columns sum to 1.

- **Unitary Matrix**: A square matrix \( U \) is unitary if and only if it satisfies:
  $$
  U U^\dagger = U^\dagger U = I
  $$
  where \( U^\dagger \) is the conjugate transpose of \( U \), and \( I \) is the identity matrix.

- **Inner Product**:  
  For two column vectors \( v \) and \( u \), their inner product is defined as:
  $$
  \langle v, u \rangle = v^\dagger u, \quad \langle u, v \rangle = u^\dagger v
  $$

- **\( p \)-Norm of a Vector**:  
  The \( p \)-norm of a vector \( v = (v_1, v_2, \dots, v_n) \) in a complex \( n \)-dimensional vector space is given by:
  $$
  \| v \|_p = \left( |v_1|^p + |v_2|^p + \dots + |v_n|^p \right)^{1/p}
  $$

- **Orthonormal Set**:  
  A set of vectors \( \{ v_1, v_2, \dots, v_n \} \) is **orthonormal** if:
  1. Each vector has an \( \ell_2 \)-norm of 1.
  2. The inner products of distinct vectors are 0.

- **Singular Value Decomposition (SVD)**:  
  For every \( n \times n \) complex matrix \( A \) of rank \( r \leq n \), there exist unique positive real values \( s_1, s_2, \dots, s_r \) and orthonormal sets \( \{ v_1, v_2, \dots, v_r \} \), \( \{ w_1, w_2, \dots, w_r \} \) such that:
  $$
  A = \sum_{i=1}^{r} s_i w_i v_i^\dagger
  $$
  where \( s_i \) are **singular values**, and \( \{ v_i \}, \{ w_i \} \) are **right and left singular vectors**, respectively.

---

## **Question 1: Unitary Matrices and Orthonormality**  

### **Question:**  
A matrix \( U \) is unitary if it satisfies:
$$
U^\dagger U = U U^\dagger = I
$$
Given the orthonormal states:
$$
v_1 = \frac{3}{5} \alpha \otimes \alpha + \frac{4}{5} \beta \otimes \beta
$$
$$
v_2 = \frac{4}{5} \alpha \otimes \alpha - \frac{3}{5} \beta \otimes \beta
$$
$$
v_3 = \frac{2}{\sqrt{5}} \alpha \otimes \beta + \frac{i}{\sqrt{5}} \beta \otimes \alpha
$$
$$
v_4 = \frac{1}{\sqrt{5}} \alpha \otimes \beta - \frac{2i}{\sqrt{5}} \beta \otimes \alpha
$$
Verify that these states form an orthonormal basis, i.e., show that:
$$
\langle v_i, v_j \rangle = \delta_{ij}
$$
where \( \delta_{ij} \) is the Kronecker delta.

### **Answer:**  
We compute the inner product for each pair:
$$
\langle v_i, v_j \rangle = \sum_{k} (v_i^k)^* v_j^k
$$
After computing for all pairs, we find:
$$
\langle v_i, v_j \rangle = 1 \text{ for } i = j, \quad 0 \text{ for } i \neq j
$$
Thus, the given states are mutually orthonormal, forming a valid basis.

### **Takeaway:**  
- The set of vectors given is **orthonormal** and forms a **valid quantum basis**.
- Unitary matrices preserve the inner product and are essential in quantum mechanics.

---

## **Question 2: Orthonormal Basis and Identity Matrix**  

### **Question:**  
Given an orthonormal set \( \{v_1, v_2, ..., v_n\} \), show that the sum of their outer products forms the identity matrix:
$$
A = \sum_{i=1}^{n} v_i v_i^\dagger = I_{n\times n}
$$
Verify this property by applying \( A \) to an arbitrary vector \( w \).

### **Answer:**  
Let \( w \) be any arbitrary vector expressed in terms of the basis:
$$
w = \sum_{i=1}^{n} \alpha_i v_i
$$
Applying \( A \):
$$
A w = \sum_{i=1}^{n} v_i v_i^\dagger \sum_{j=1}^{n} \alpha_j v_j
$$
Since \( A w = w \), \( A \) acts as the identity matrix.

### **Takeaway:**  
- Any set of **orthonormal basis vectors** satisfies \( \sum v_i v_i^\dagger = I \).
- This property is crucial in **quantum state representation**.

---

## **Question 3: Unitary Matrix Properties**  

### **Question:**  
Show that a unitary matrix \( U \) satisfies the singular value decomposition (SVD) property:
$$
U = \sum_{i=1}^{r} s_i w_i v_i^\dagger
$$
where \( s_i \) are singular values and \( \{v_i\} \), \( \{w_i\} \) are orthonormal sets. Prove that for unitary matrices, all singular values satisfy \( s_i = 1 \).

### **Answer:**  
Using SVD:
$$
U^\dagger U = \sum_{i=1}^{r} s_i^2 w_i w_i^\dagger = I
$$
which is only true if \( s_i = 1 \) for all \( i \). Thus, unitary matrices preserve norms.

### **Takeaway:**  
- Unitary matrices have **singular values equal to 1**.
- They **preserve the length** of quantum states, making them essential for quantum operations.

---

## **Question 4: Stochastic Matrices and Norm Preservation**  

### **Question:**  
A **column stochastic matrix** \( S \) satisfies:
$$
\sum_{i=1}^{n} s_{ij} = 1, \quad \forall j
$$
Show that for any vector \( v \), its \( \ell_1 \)-norm remains unchanged under \( S \):
$$
\|Sv\|_1 = \|v\|_1
$$

### **Answer:**  

$$
Applying \( S \):
\[
w = S v, \quad w_i = \sum_{j=1}^{n} s_{ij} v_j
\]
Then:
\[
\|w\|_1 = \sum_{i=1}^{n} |w_i| = \sum_{i=1}^{n} \sum_{j=1}^{n} s_{ij} |v_j|
\]
Since \( S \) is stochastic:
\[
\sum_{i=1}^{n} s_{ij} = 1
\]
Thus, \( \|w\|_1 = \|v\|_1 \), proving norm preservation.
$$
### **Takeaway:**  
- Stochastic matrices **preserve the \( \ell_1 \)-norm**.
- They model **probabilistic transformations** in quantum mechanics.

