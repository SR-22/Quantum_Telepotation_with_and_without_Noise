# Quantum Teleportation Simulations (Qiskit)

This repository contains **two structured implementations of the quantum teleportation protocol** using **Qiskit**, progressing from an **ideal (noise-free) model** to a **realistic noise-simulated model**. The project is designed to help learners and researchers understand how quantum teleportation behaves under both theoretical and practical conditions.

---

## Repository Overview

Quantum teleportation is a cornerstone protocol in quantum communication, enabling the transfer of an unknown quantum state using entanglement and classical communication.

This repository is organized to clearly distinguish between:

* **Ideal teleportation** (theoretical benchmark)
* **Noisy teleportation** (hardware-realistic behavior)

Such a comparison is essential for understanding the gap between textbook quantum mechanics and near-term quantum hardware.

---

## 📁 Repository Structure

```
├── Quantum_Teleportation/
│   └── Quantum_teleportation.ipynb
│
├── Noise_simulated/
│   └── Noise_simulated_quantum_teleportation.ipynb
│
├── README.md
```

---

## Folder Descriptions

### 1️⃣ Quantum Teleportation (Without Noise)

📂 `Quantum_Teleportation/`

This folder contains an implementation of **quantum teleportation assuming perfect quantum operations**.

#### Features

* Pure statevector simulation
* Perfect Bell-state preparation
* Ideal measurements and corrections

#### Purpose

* Serves as a **baseline reference**
* Helps verify correctness of the teleportation protocol
* Useful for beginners learning the fundamentals of quantum circuits

---

### 2️⃣ Noise_simulated_quantum_teleportation

📂 `Noise_simulated/`

This folder extends the ideal protocol by incorporating **realistic noise models** inspired by quantum hardware.

#### Features

* Density matrix simulation
* Depolarizing noise (gate imperfections)
* Thermal relaxation noise (T1, T2 decoherence)
* Partial trace to extract Bob’s state
* Fidelity analysis under noise
* Measurement statistics and histograms

#### Purpose

* Demonstrates how teleportation degrades under noise
* Models near-term quantum hardware behavior
* Introduces open quantum system concepts

---

## Key Learning Outcomes

By exploring both folders, users will learn:

* How quantum teleportation works in theory
* How noise affects entanglement and fidelity
* Why density matrices are necessary for noisy systems
* The dominant role of two-qubit gate errors
* How to evaluate protocol performance using fidelity

---

## How to Run the Code

### 1. Install Dependencies

```bash
pip install qiskit qiskit-aer numpy matplotlib
```

### 2. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 3. Run Notebooks

Start with:

1. `Quantum_Teleportation.ipynb`
2. `Noise_simulated.ipynb`

---

##  Intended Audience

This repository is suitable for:

* Physics and engineering students
* Beginners to intermediate learners in quantum computing
* Researchers exploring quantum communication protocols

---

## References

* M. A. Nielsen and I. L. Chuang, *Quantum Computation and Quantum Information*
* Qiskit Documentation: [https://qiskit.org](https://qiskit.org)
* IBM Quantum Experience

---

## 📜 License

This repository is intended for **academic and educational use**.
