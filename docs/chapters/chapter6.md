# Chapter 6: D-Wave
# Quantum Annealing and Ising Models

## What is D-Wave Technology?

D-Wave builds quantum annealers designed to solve combinatorial optimization problems. Unlike gate-based quantum computers, D-Wave's systems use **quantum annealing**, a process based on the principle of energy minimization.

## Quantum Annealing vs Gate-based QC

- **Quantum Annealing (QA)**: Uses adiabatic evolution of a system's Hamiltonian.
- **Gate-Based QC**: Uses logic gates to construct quantum circuits for universal computation.

## Why Do Errors in Qubits Not Greatly Affect D-Wave Results?

In QA, the final result is **not a quantum state** but a **classical state** corresponding to the **minimum energy configuration**. Errors during the anneal may shift the path slightly but do not necessarily prevent reaching a good approximation of the global minimum.

## Why is it Called "Annealing"?

Inspired by **classical annealing**, which heats a system and then slowly cools it to remove defects.

In **quantum annealing**, we do:
- Start in the ground state of a known initial Hamiltonian:
  $$
  H(t=0) = H_{\text{driver}} = -\sum_{i} \sigma^x_i
  $$
- Slowly evolve to the problem Hamiltonian:
  $$
  H(t=T) = H_{\text{problem}} = \sum_{i} h_i \sigma^z_i + \sum_{i<j} J_{ij} \sigma^z_i \sigma^z_j
  $$
- System ideally remains in the ground state (via adiabatic theorem).

## Mapping Optimization Problems to Ising Model

A general quadratic unconstrained binary optimization (QUBO) problem:
$$
\text{minimize} \quad x^T Q x \quad \text{where} \quad x_i \in \{0, 1\}
$$

Can be transformed to an Ising form:
$$
\text{minimize} \quad \sum_i h_i s_i + \sum_{i<j} J_{ij} s_i s_j \quad \text{where} \quad s_i \in \{-1, +1\}
$$

## Example: Financial Portfolio Optimization

Minimize risk and maximize return:
$$
\text{maximize} \quad \mu^T x - \lambda x^T \Sigma x
$$

Subject to:
- Budget constraint: $\sum x_i = k$
- Binary decision: $x_i \in \{0, 1\}$

This can be formulated as a QUBO and solved using D-Wave or other Ising-based methods.

## Coupled Oscillator-Based Ising Model (COBI)

COBI uses coupled oscillators to represent spins. The dynamics naturally evolve toward energy-minimizing configurations:
- Oscillators represent binary spins.
- Couplings mimic $J_{ij}$ terms.
- Stable phase-locking corresponds to a low-energy Ising state.

## COBI vs QUBO Optimization Results

Studies have shown that COBI implementations can match or approximate QUBO solutions well for small problem sizes, such as:
- MAX-CUT problems
- Graph coloring
- Portfolio selection (toy models)

---

