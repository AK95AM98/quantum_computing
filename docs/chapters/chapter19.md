# Chapter 19: IBM Quantum Computing Roadmap

## Overview

IBM has been one of the most transparent companies in the quantum computing industry when it comes to publishing detailed, multi-year roadmaps. Since unveiling its first quantum roadmap in 2020, IBM has consistently delivered on its milestones — from the 65-qubit Hummingbird to the 1,121-qubit Condor — while steadily refining its long-term vision. This chapter examines IBM's latest roadmap, covering the path from today's noisy intermediate-scale quantum (NISQ) processors to large-scale, fault-tolerant quantum computing by 2029.

## Current Hardware (2024–2025)

IBM's current fleet of quantum computers includes processors from two major families:

| Processor | Qubits | Generation |
|-----------|--------|------------|
| Eagle | 127 | 2021 |
| Heron r1 | 133 | 2023 |
| Heron r2 | 156 | 2024 |
| Heron r3 | 156 | 2024 |

The **Heron** family introduced tunable couplers — hardware elements that allow neighboring qubits to be selectively connected or isolated — significantly reducing crosstalk errors compared to the earlier Eagle processors.

## The Nighthawk Processor (2025)

In November 2025, IBM announced **IBM Quantum Nighthawk**, its most advanced processor to date:

- **120 qubits** arranged in a square lattice topology
- **218 next-generation tunable couplers**, providing over 20% greater connectivity than Heron
- Enables circuits with **30% more complexity** while maintaining low error rates
- Supports workloads of up to **5,000 two-qubit gates**

Nighthawk represents a significant architectural shift. The square lattice layout with enhanced couplers enables roughly **16 times the effective circuit depth** compared to Heron, meaning algorithms can run substantially longer before errors accumulate to the point of rendering results meaningless.

### Nighthawk Scaling Targets

| Year | Two-Qubit Gate Target | Qubit Scaling |
|------|----------------------|---------------|
| 2025 | 5,000 gates | 120 qubits |
| 2026 | 7,500 gates | — |
| 2027 | 10,000 gates | — |
| 2028 | 15,000 gates | 1,000+ connected qubits via l-couplers |

By 2028, IBM plans to connect up to **nine Nighthawk-class modules** using long-range **l-couplers** (inter-chip links), scaling the system to over 1,000 interconnected qubits.

## The Loon Processor (2025)

Alongside Nighthawk, IBM unveiled **IBM Quantum Loon**, an experimental processor that demonstrates all the key hardware components required for fault-tolerant quantum computing:

- **Multiple high-quality, low-loss routing layers** that provide pathways for longer on-chip connections called **c-couplers**
- **C-couplers** link distant qubits on the same chip, enabling the connectivity patterns required by advanced error-correcting codes
- **Mid-circuit qubit reset** technologies that allow qubits to be reinitialized between computations — essential for error correction cycles

Loon is not a production processor. Instead, it serves as a technology demonstrator, proving that IBM has the building blocks needed for the fault-tolerant systems on the roadmap.

## Coupler Technologies: C-Couplers and L-Couplers

Two coupler technologies sit at the heart of IBM's scaling strategy: **c-couplers** for long-range on-chip connections and **l-couplers** for inter-chip connections. Understanding how they work requires a brief review of the physics of superconducting qubit coupling.

### Background: Transmon Qubit Hamiltonian

IBM's quantum processors are built from **transmon qubits** — superconducting circuits based on Josephson junctions. The Hamiltonian of a single transmon is:

$$
\hat{H}_{\text{transmon}} = 4E_C(\hat{n} - n_g)^2 - E_J \cos\hat{\varphi}
$$

where:

- $E_C = \frac{e^2}{2C_\Sigma}$ is the **charging energy**, with $C_\Sigma$ being the total capacitance of the qubit island
- $E_J$ is the **Josephson energy**, set by the critical current of the junction
- $\hat{n}$ is the Cooper pair number operator (counts pairs of electrons tunneling across the junction)
- $n_g$ is the offset charge induced by the electrostatic environment
- $\hat{\varphi}$ is the gauge-invariant superconducting phase difference across the junction

In the transmon regime, $E_J / E_C \gg 1$ (typically 50–100), which exponentially suppresses charge noise sensitivity while preserving sufficient anharmonicity to address individual energy levels.

### Nearest-Neighbor Tunable Couplers

In IBM's Heron and Nighthawk processors, adjacent qubits are connected through **tunable couplers** — small auxiliary transmon circuits placed between each pair of neighboring qubits. The system Hamiltonian for two qubits $A$ and $B$ connected by a tunable coupler $C$ is:

$$
\hat{H} = \hat{H}_A + \hat{H}_B + \hat{H}_C + \hat{H}_{\text{int}}
$$

The interaction term includes both direct capacitive coupling and coupler-mediated coupling:

$$
\hat{H}_{\text{int}} = g_{AB}^{\text{direct}}(\hat{a}^\dagger \hat{b} + \hat{a}\hat{b}^\dagger) + g_{AC}(\hat{a}^\dagger \hat{c} + \hat{a}\hat{c}^\dagger) + g_{BC}(\hat{b}^\dagger \hat{c} + \hat{b}\hat{c}^\dagger)
$$

where $\hat{a}^\dagger$, $\hat{b}^\dagger$, $\hat{c}^\dagger$ are creation operators for qubits $A$, $B$, and coupler $C$ respectively, and the $g$ values are capacitive coupling strengths given by:

$$
g_{ij} = \frac{1}{2} \frac{C_{ij}}{\sqrt{C_{\Sigma,i}\, C_{\Sigma,j}}} \sqrt{\omega_i \omega_j}
$$

Here $C_{ij}$ is the mutual capacitance between elements $i$ and $j$, $C_{\Sigma,i}$ is the total capacitance of element $i$, and $\omega_i$ is its resonance frequency.

The key physics is **destructive interference**: when the coupler frequency $\omega_C$ is tuned (via an external magnetic flux through the coupler's SQUID loop), the coupler-mediated interaction can partially or fully cancel the direct capacitive coupling. The effective qubit-qubit coupling becomes:

$$
g_{\text{eff}} = g_{AB}^{\text{direct}} + \frac{g_{AC}\, g_{BC}}{\Delta_{AC}}
$$

where $\Delta_{AC} = \omega_A - \omega_C$ is the detuning between qubit $A$ and the coupler. By tuning $\omega_C$, IBM can set $g_{\text{eff}}$ to zero (idle/off state) or to a desired value for performing two-qubit gates (on state). This tunability is what enables high-fidelity gates with low crosstalk.

### C-Couplers: Long-Range On-Chip Connections

Standard tunable couplers only connect **nearest-neighbor** qubits on the chip. However, advanced error-correcting codes like the bivariate bicycle qLDPC codes require connectivity patterns where a qubit must interact with distant, non-adjacent qubits. This is where **c-couplers** come in.

#### Physical Structure

A c-coupler is implemented by adding one or more **metal routing layers** above the qubit plane on the chip. These additional superconducting metal planes act as bridges — they carry microwave signals over the top of intervening qubits to connect two distant qubits on the same chip.

The physical structure can be modeled as a transmission line resonator of length $\ell$ connecting two distant qubits. The resonator has a fundamental frequency:

$$
\omega_r = \frac{\pi v}{\ell}
$$

where $v = \frac{1}{\sqrt{LC}}$ is the phase velocity of the microwave signal in the superconducting transmission line, with $L$ and $C$ being the inductance and capacitance per unit length.

#### Coupling Mechanism

Each qubit couples capacitively to one end of the c-coupler resonator. The resulting Hamiltonian follows the **Jaynes-Cummings model** for each qubit-resonator interaction:

$$
\hat{H}_{\text{c-coupler}} = \omega_r \hat{r}^\dagger \hat{r} + \sum_{k \in \{A,B\}} \left[ \frac{\omega_k}{2} \hat{\sigma}_z^{(k)} + g_k \left( \hat{\sigma}_+^{(k)} \hat{r} + \hat{\sigma}_-^{(k)} \hat{r}^\dagger \right) \right]
$$

where $\hat{r}^\dagger$ and $\hat{r}$ are the creation and annihilation operators for the resonator mode, $g_k$ is the coupling strength of qubit $k$ to the resonator, and $\hat{\sigma}_{\pm}^{(k)}$ are the raising/lowering operators for qubit $k$.

In the **dispersive regime** (where the qubit-resonator detuning $\Delta_k = \omega_k - \omega_r$ is much larger than $g_k$), the resonator can be adiabatically eliminated, yielding an effective qubit-qubit interaction:

$$
\hat{H}_{\text{eff}} = J_{\text{eff}} \left( \hat{\sigma}_+^{(A)} \hat{\sigma}_-^{(B)} + \hat{\sigma}_-^{(A)} \hat{\sigma}_+^{(B)} \right)
$$

with the effective coupling strength:

$$
J_{\text{eff}} = \frac{g_A \, g_B}{2} \left( \frac{1}{\Delta_A} + \frac{1}{\Delta_B} \right)
$$

This is a **virtual photon exchange** — the two qubits swap excitations through the resonator without the resonator ever being physically populated. The process is mediated by virtual photons, analogous to how the Coulomb force between charged particles is mediated by virtual photons in quantum electrodynamics.

#### Performance

IBM has demonstrated c-coupler test chips achieving two-qubit error rates between distant qubits of:

$$
\varepsilon_{\text{c-coupler}} \approx 2 \times 10^{-3} \text{ to } 5 \times 10^{-3}
$$

This is comparable to the error rates between nearest-neighbor qubits with standard tunable couplers — a remarkable achievement, since long-range connections typically suffer from higher loss and decoherence. The key to this performance is the use of high-quality, low-loss superconducting routing layers that minimize microwave photon loss.

#### Why C-Couplers Matter for Error Correction

Surface codes — the most commonly studied error-correcting codes — only require nearest-neighbor connectivity but have high overhead (many physical qubits per logical qubit). IBM's qLDPC bivariate bicycle codes are far more efficient but require specific long-range connectivity patterns. Consider the [[144, 12, 12]] code: each of the 144 data qubits must be connected to specific syndrome check qubits that may be located far away on the chip. Without c-couplers, implementing these codes would require routing through many SWAP gates, each adding errors:

$$
\varepsilon_{\text{SWAP chain}} = 1 - (1 - \varepsilon_{\text{gate}})^{3d}
$$

where $d$ is the distance in the qubit lattice and the factor of 3 arises because each SWAP decomposes into three CNOT gates. For $d = 6$ hops and $\varepsilon_{\text{gate}} = 10^{-3}$, this gives $\varepsilon_{\text{SWAP chain}} \approx 1.8\%$ — far worse than a direct c-coupler connection.

### L-Couplers: Inter-Chip Quantum Links

While c-couplers connect distant qubits on the **same** chip, **l-couplers** connect qubits on **separate** chips. This is essential for scaling beyond the limits of a single monolithic processor.

#### Physical Structure

An l-coupler consists of a **superconducting coaxial cable** (approximately one meter in length) that connects dedicated communication resonators on two separate quantum chips. The entire assembly operates inside a **dilution refrigerator** at millikelvin temperatures (typically 10–20 mK), the same environment as the quantum processors themselves.

The physical components are:

1. **Communication resonator on Chip A** — a superconducting microwave cavity coupled to one or more qubits
2. **Superconducting coaxial cable** — an aluminum coaxial line with mechanically-intermixed indium joins for low-loss connections
3. **Communication resonator on Chip B** — the matching cavity on the remote chip

#### Coupling Mechanism: Dark Mode Architecture

The l-coupler exploits a phenomenon from coupled oscillator physics. When two resonators (one on each chip) are connected through the coaxial cable, the combined system supports multiple modes. The Hamiltonian of the coupled resonator system is:

$$
\hat{H}_{\text{link}} = \omega_{r_1} \hat{r}_1^\dagger \hat{r}_1 + \omega_{r_2} \hat{r}_2^\dagger \hat{r}_2 + \omega_{\text{cable}} \hat{c}^\dagger \hat{c} + g_1(\hat{r}_1^\dagger \hat{c} + \hat{r}_1 \hat{c}^\dagger) + g_2(\hat{r}_2^\dagger \hat{c} + \hat{r}_2 \hat{c}^\dagger)
$$

where $\hat{r}_1$, $\hat{r}_2$ are the operators for the two chip resonators, $\hat{c}$ is the cable mode operator, and $g_1$, $g_2$ are the coupling strengths at each junction.

When the two communication resonators are tuned to the same frequency ($\omega_{r_1} = \omega_{r_2} = \omega_r$), the normal modes of the system include a **dark mode**:

$$
\hat{d} = \frac{1}{\sqrt{2}}(\hat{r}_1 - \hat{r}_2)
$$

This dark mode has a remarkable property: it has **zero amplitude in the coaxial cable**. Because the cable is the primary source of photon loss in the link, the dark mode is highly immune to cable-induced decoherence. Quantum information encoded in the dark mode can be transferred between chips with significantly higher fidelity than would be possible using a simple resonant transfer through the cable.

The effective inter-chip qubit-qubit coupling, after adiabatic elimination of the resonator modes, takes the form:

$$
J_{\text{inter}} = \frac{g_{q_1} g_{q_2}}{2\Delta} \cdot \frac{g_1 g_2}{\delta^2 - g_{\text{eff}}^2}
$$

where $g_{q_i}$ are the qubit-to-resonator couplings, $\Delta$ is the qubit-resonator detuning, $\delta$ is the resonator-cable detuning, and $g_{\text{eff}}$ captures the hybridization between the resonators and the cable.

#### Quantum State Transfer Protocol

To transfer a quantum state $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ from a qubit on Chip A to a qubit on Chip B, the l-coupler uses a sequence of calibrated microwave pulses:

1. **Qubit A → Resonator A**: A $\pi$-pulse swaps the qubit state into the communication resonator on Chip A
2. **Resonator A → Dark Mode → Resonator B**: The state transfers through the dark mode of the coupled resonator-cable system, evolving under the link Hamiltonian for a time $t_{\text{transfer}} = \frac{\pi}{2J_{\text{link}}}$
3. **Resonator B → Qubit B**: A second $\pi$-pulse maps the state onto the target qubit on Chip B

The total transfer time is on the order of hundreds of nanoseconds, governed by the coupling strengths in the system.

#### Inter-Chip Gate Operations

Rather than transferring states, l-couplers can also implement **direct inter-chip two-qubit gates**. IBM's Flamingo architecture demonstrated inter-chip CNOT gates between Heron R2 chips connected by meter-long superconducting l-couplers. The l-coupler natively supports analog **iSWAP-like interactions**:

$$
U_{\text{iSWAP}}(\theta) = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos\theta & i\sin\theta & 0 \\
0 & i\sin\theta & \cos\theta & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

By calibrating the interaction time and applying single-qubit corrections, this can be compiled into standard gate sets including CNOT.

#### Performance

Current l-coupler performance on IBM's Flamingo system:

| Metric | On-Chip (Heron R2) | Inter-Chip (L-Coupler) |
|--------|-------------------|----------------------|
| Two-qubit gate error | $8 \times 10^{-4}$ (99.92% fidelity) | $3.5 \times 10^{-2}$ (96.5% fidelity) |
| Connectivity | Nearest-neighbor | Chip-to-chip (~1 meter) |

The inter-chip error rate is currently about **40 times higher** than on-chip gates. Closing this gap is a major focus of IBM's research. Improvements in cable loss, junction quality, and pulse calibration are expected to bring inter-chip fidelity closer to on-chip levels by the time Cockatoo and Starling arrive.

#### Scaling with L-Couplers

IBM's modular scaling plan uses l-couplers to build systems far larger than any single chip:

$$
N_{\text{total}} = n_{\text{modules}} \times N_{\text{qubits/module}} + N_{\text{link qubits}}
$$

For the 2028 target, nine Nighthawk-class modules connected via l-couplers yield:

$$
N_{\text{total}} = 9 \times 120 = 1{,}080 \text{ connected qubits}
$$

Each module retains its high-fidelity on-chip gates for local computation, while l-couplers handle the less frequent but essential inter-module operations required by distributed error correction protocols.

### C-Couplers vs. L-Couplers: Comparison

| Property | C-Coupler | L-Coupler |
|----------|-----------|-----------|
| **Scope** | On-chip (same processor) | Inter-chip (separate processors) |
| **Physical medium** | Metal routing layers above qubit plane | Superconducting coaxial cable (~1 m) |
| **Operating temperature** | Millikelvin (on-chip) | Millikelvin (in dilution refrigerator) |
| **Two-qubit error rate** | $2\text{–}5 \times 10^{-3}$ | $\sim 3.5 \times 10^{-2}$ |
| **Primary use** | qLDPC code connectivity | Modular scaling beyond single chip |
| **Coupling mechanism** | Virtual photon exchange via resonator | Dark mode transfer via coaxial link |
| **First demonstration** | Loon (2025) | Flamingo (2024) |
| **Production deployment** | Kookaburra (2026) | Cockatoo (2027) |

## Path to Quantum Advantage (2026)

IBM defines **quantum advantage** as the point where a quantum computer can solve a computation more accurately, cheaply, or efficiently than any classical method. IBM expects the first verified cases of quantum advantage to be confirmed by the broader research community by the end of 2026.

### Kookaburra Processor (2026)

The key hardware milestone for 2026 is **IBM Quantum Kookaburra**:

- First processor module capable of storing information in a **quantum low-density parity check (qLDPC) memory**
- Includes an attached **logical processing unit (LPU)** for operating on the stored logical qubits
- Designed to work alongside classical high-performance computing (HPC) systems to deliver quantum advantage

The qLDPC memory is a breakthrough in error correction efficiency. IBM's approach uses **bivariate bicycle (BB) codes**:

$$
\text{[[144, 12, 12]] gross code:} \quad 144 \text{ data qubits} + 144 \text{ syndrome qubits} \rightarrow 12 \text{ logical qubits}
$$

This achieves equivalent error correction to surface codes while requiring approximately **10 times fewer physical qubits** — a dramatic improvement in overhead.

### Quantum Advantage Tracker

IBM has introduced a community-led **quantum advantage tracker** that monitors three categories of experiments:

1. **Observable estimation** — computing expectation values of quantum observables
2. **Variational problems** — optimization and machine learning tasks using variational quantum algorithms
3. **Efficiently verifiable problems** — tasks where quantum results can be checked classically

## Path to Fault Tolerance (2027–2029)

### Cockatoo Processor (2027)

**IBM Quantum Cockatoo** is planned to demonstrate:

- **Entanglement between separate processor modules** using universal adapters
- Inter-module quantum information transfer
- Multi-module error correction across physically separated chips

This is a critical milestone: to build truly large-scale quantum computers, qubits on different chips must be entangled as reliably as qubits on the same chip.

### Starling Proof-of-Concept (2028)

The 2028 milestone focuses on:

- **Magic state injection** across multiple modules — a technique essential for performing universal quantum computation with error-corrected qubits
- Integration of **error-correcting decoder hardware** (FPGAs or ASICs)

IBM's **Relay-BP decoder** achieves a 5–10 times reduction in decoding overhead compared to other leading approaches, and it is compact enough to run on standard FPGAs.

### IBM Quantum Starling (2029)

The culmination of IBM's roadmap is **IBM Quantum Starling** — a large-scale, fault-tolerant quantum computer with the following targets:

$$
\text{Starling:} \quad 200 \text{ logical qubits} \times 100{,}000{,}000 \text{ quantum gates}
$$

Key specifications:

- **200 logical qubits** — each protected by layers of error correction
- Capable of running circuits with **100 million quantum gates**
- Will be constructed at IBM's **Poughkeepsie, New York** facility

To put this in perspective, today's best quantum processors can handle circuits of a few thousand gates before errors dominate. Starling aims for a 20,000-fold increase in circuit depth — enough to run algorithms like quantum phase estimation and quantum chemistry simulations that require deep circuits.

## Error Correction Breakthroughs

A key enabler of the roadmap is IBM's progress in quantum error correction:

### Real-Time qLDPC Decoding

IBM demonstrated that classical hardware can accurately decode quantum errors in real time using qLDPC codes:

- Decoding latency: **under 480 nanoseconds**
- **10 times faster** than the previous leading approach
- Achieved **one year ahead of schedule**

Real-time decoding is critical because error correction must keep pace with the quantum processor's clock speed. If decoding is too slow, errors accumulate faster than they can be corrected.

### Bivariate Bicycle Codes

IBM's error correction strategy is built on bivariate bicycle codes:

| Code | Data Qubits | Logical Qubits | Code Distance |
|------|-------------|-----------------|---------------|
| [[144, 12, 12]] gross | 144 | 12 | 12 |
| [[288, 12, 18]] two-gross | 288 | 12 | 18 |

The **code distance** $d$ determines how many physical errors can be tolerated before a logical error occurs. Higher distance means better protection at the cost of more physical qubits.

## Software and Tools: Qiskit

IBM's open-source quantum SDK, **Qiskit**, continues to evolve alongside the hardware:

- **24% accuracy increase** with dynamic circuits at 100+ qubit scale
- **100 times cost reduction** for extracting accurate results via HPC-powered error mitigation
- New **C++ interface** for integration with classical HPC environments
- Planned **computational libraries** for machine learning and optimization by 2027

Qiskit's transpiler automatically maps high-level quantum circuits onto the specific connectivity of IBM's processors, optimizing gate sequences and minimizing errors.

## Manufacturing Advances

IBM has made significant investments in quantum chip fabrication:

- Primary fabrication shifted to a **300mm wafer facility** at NY Creates' Albany NanoTech Complex
- Processor build time has been **cut in half** through semi-automated tooling
- **10-fold increase** in quantum chip physical complexity
- Multiple processor designs can now be researched **in parallel**

These manufacturing improvements are essential for the roadmap: building fault-tolerant systems with thousands of qubits requires the same kind of scalable fabrication processes used in the classical semiconductor industry.

## Roadmap Summary

| Year | Processor | Key Milestone |
|------|-----------|---------------|
| 2023 | Heron r1 | 133-qubit tunable coupler processor |
| 2024 | Heron r2/r3 | 156-qubit improved fidelity |
| 2025 | Nighthawk | 120 qubits, square lattice, 5,000 gates |
| 2025 | Loon | Fault-tolerance component demonstrator |
| 2026 | Kookaburra | qLDPC memory + LPU, quantum advantage |
| 2027 | Cockatoo | Multi-module entanglement |
| 2028 | Starling PoC | Magic state injection, decoder hardware |
| 2029 | Starling | 200 logical qubits, 100M gates, fault-tolerant |

## Summary

IBM's quantum roadmap is one of the most detailed and ambitious in the industry. The company is pursuing two parallel tracks: **near-term quantum advantage** through increasingly powerful Nighthawk-class processors, and **long-term fault tolerance** through the Loon → Kookaburra → Cockatoo → Starling pipeline. The key enabling technologies — qLDPC error correction codes, real-time decoding, c-couplers, l-couplers, and 300mm fabrication — are all progressing on or ahead of schedule. If IBM delivers on its targets, by 2029 we will have a quantum computer capable of running algorithms that are fundamentally beyond the reach of any classical supercomputer.

## References

- [IBM Quantum Hardware and Roadmap](https://www.ibm.com/quantum/hardware)
- [IBM Quantum Roadmap 2025](https://www.ibm.com/roadmaps/quantum/2025/)
- [IBM Newsroom: New Quantum Processors, November 2025](https://newsroom.ibm.com/2025-11-12-ibm-delivers-new-quantum-processors,-software,-and-algorithm-breakthroughs-on-path-to-advantage-and-fault-tolerance)
- [IBM Quantum Blog: Path to Large-Scale Fault-Tolerant QC](https://www.ibm.com/quantum/blog/large-scale-ftqc)
- [IBM Nighthawk Processor Coverage](https://www.helpnetsecurity.com/2025/11/12/ibm-quantum-nighthawk-processor/)
- [IBM Networked Quantum Computers Blog](https://www.ibm.com/quantum/blog/networked-quantum-computers)
- [Hardware-Aware Compilation for Chip-to-Chip Coupler-Connected Modular Quantum Systems (arXiv)](https://arxiv.org/html/2505.09036v1)
- [Tunable Coupler Documentation — qucat](https://qucat.org/tutorials/tuneable_coupler.html)
- [Context-Aware Coupler Reconfiguration for Tunable Coupler-Based Superconducting Quantum Computers (arXiv)](https://arxiv.org/html/2401.03817v2)
