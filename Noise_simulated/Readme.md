# Quantum Teleportation with Noise (Qiskit)

This repository contains a **Jupyter Notebook implementation of quantum teleportation** simulated under **realistic noise models** using **Qiskit Aer**. The project demonstrates how decoherence and gate imperfections affect teleportation fidelity using the **density matrix formalism**.

---

##  Project Overview

Quantum teleportation is a foundational protocol in quantum communication, enabling the transfer of an **unknown quantum state** using:

* Quantum entanglement
* Classical communication
* Local quantum operations

In this project, we simulate teleportation of a single qubit while incorporating **hardware-inspired noise**, closely mimicking near-term quantum devices.

---

## Key Concepts Covered

* Quantum teleportation protocol
* Bell-state preparation and measurement
* Dynamic circuits with classical conditioning (`if_test`)
* Density matrix simulation
* Depolarizing noise
* Thermal relaxation (T1, T2 decoherence)
* Partial trace and reduced states
* Teleportation fidelity
* Measurement statistics and histograms

---

## Simulation Details

### Qubits

* **Alice_C** : Qubit to be teleported
* **Alice_A** : Alice’s half of Bell pair
* **Bob_B**   : Bob’s half of Bell pair

### Noise Model

The following noise mechanisms are included:

* **Depolarizing noise**
  Models imperfect gate control

* **Thermal relaxation noise**
  Models energy relaxation (T1) and dephasing (T2)

Noise is applied to:

* Single-qubit gates (H, X, Z)
* Two-qubit gate (CX)

---

## Performance Metric

Teleportation performance is evaluated using **quantum state fidelity**:

$[ F = \langle \psi | \rho_B | \psi \rangle ]$

where:

* $(|\psi\rangle)$ is the ideal input state
* $(\rho_B)$ is Bob’s reduced density matrix

---

## Repository Structure

```
├── Noise_simulated_quantum_teleportation.ipynb
├── Readme.md
```

---

## How to Run

### 1. Install Dependencies

```bash
pip install qiskit qiskit-aer numpy matplotlib
```

### 2. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 3. Open the Notebook

```text
quantum_teleportation_with_noise.ipynb
```

Run all cells sequentially to reproduce the results.

---

## Outputs

* Teleportation fidelity under realistic noise
* Bob’s reduced density matrix
* Measurement histograms showing output statistics

---

## Results & Discussion

### Teleportation Fidelity

In the presence of depolarizing and thermal relaxation noise, the teleportation fidelity is observed to be **less than unity**, indicating deviation from ideal teleportation. This reduction arises from:

* Accumulated decoherence during gate execution (T1 and T2 effects)
* Higher error rates associated with two-qubit (CX) gates
* Classical feedforward conditioned on noisy measurement outcomes

Nevertheless, fidelities significantly above the classical limit (~2/3 for qubit teleportation) confirm that **quantum teleportation remains successful despite noise**.

### Bob’s Measurement Statistics

The measurement histogram of Bob’s qubit shows an approximately equal distribution between |0⟩ and |1⟩ outcomes, consistent with the input state:

|ψ⟩ = (|0⟩ + |1⟩)/√2

Deviations from the ideal 50–50 distribution directly reflect the impact of noise and imperfect corrections.

### Physical Interpretation

This simulation highlights key features of near-term quantum hardware:

* Two-qubit gates dominate error budgets
* Decoherence accumulates with circuit depth
* Density matrix simulation is essential for realistic modeling

Overall, the results demonstrate how quantum teleportation degrades gracefully under noise, offering insight into the challenges faced by practical quantum communication systems.

---

## Limitations

While this simulation captures several important aspects of realistic quantum teleportation, it has the following limitations:

### 1. Simplified Noise Model

* Depolarizing and thermal relaxation noise are **phenomenological models**.
* Real hardware noise is often **non-Markovian**, time-dependent, and device-specific.

### 2. Fixed Noise Parameters

* T1, T2, and depolarizing probabilities are held constant.
* In practice, these parameters vary across qubits and drift over time.

### 3. No Crosstalk or Measurement Error Modeling

* Qubit–qubit crosstalk is not included.
* Measurement (readout) errors are not explicitly modeled.

### 4. Single-Qubit Input State

* The teleportation protocol is demonstrated for a specific superposition state.
* Performance may differ for arbitrary states or mixed input states.

### 5. Simulator-Based Study

* Results are obtained from classical simulation.
* Real quantum hardware may exhibit additional imperfections not captured here.

These limitations motivate further studies using **hardware-calibrated noise models**, **error mitigation techniques**, and execution on **real quantum processors**.

---

## Dependence of Fidelity on Noise Parameters

Teleportation fidelity is strongly influenced by the physical noise parameters used in the simulation. Below we summarize the qualitative dependence observed and expected from theory.

### Effect of T1 (Energy Relaxation Time)

* **Larger T1 → Higher fidelity**
  Energy relaxation causes |1⟩ → |0⟩ decay during gate execution.
* When T1 is short compared to total circuit duration, population loss becomes significant, reducing fidelity.

**Interpretation:** Teleportation circuits with multiple gates are highly sensitive to amplitude damping.

---

### Effect of T2 (Dephasing Time)

* **Larger T2 → Higher fidelity**
  Dephasing destroys phase coherence between |0⟩ and |1⟩.
* Superposition states (like the input state used here) are especially sensitive to T2.

**Interpretation:** Loss of phase coherence directly degrades teleportation of quantum information.

---

### Effect of p1 (Single-Qubit Depolarizing Probability)

* **Increasing p1 → Gradual fidelity reduction**
* Single-qubit gate errors accumulate linearly with circuit depth.

**Interpretation:** While less damaging than two-qubit errors, repeated single-qubit imperfections still limit performance.

---

### Effect of p2 (Two-Qubit Depolarizing Probability)

* **Increasing p2 → Rapid fidelity degradation**
* Two-qubit gates dominate the error budget in teleportation.

**Interpretation:** Entanglement generation and Bell measurements rely on CX gates, making p2 the most critical parameter.

---

### Summary Table

| Parameter | Increase Leads To     | Physical Cause            |
| --------- | --------------------- | ------------------------- |
| T1 ↑      | Fidelity ↑            | Reduced energy relaxation |
| T2 ↑      | Fidelity ↑            | Improved phase coherence  |
| p1 ↑      | Fidelity ↓ (moderate) | Single-qubit gate errors  |
| p2 ↑      | Fidelity ↓ (strong)   | Two-qubit gate errors     |

This analysis highlights why improving **two-qubit gate fidelities** and **coherence times** is crucial for scalable quantum communication.

---

## Intended Audience

This project is suitable for:

* Physics and Engineering students
* Beginners to intermediate learners in quantum computing
* Researchers exploring noisy quantum communication protocols

---

## References

* M. A. Nielsen and I. L. Chuang, *Quantum Computation and Quantum Information*
* Qiskit Documentation: [https://qiskit.org](https://qiskit.org)
* IBM Quantum Experience

---
