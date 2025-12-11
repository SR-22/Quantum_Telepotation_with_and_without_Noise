# Quantum Teleportation in Qiskit 

This project implements quantum teleportation using Qiskit’s dynamic circuits (if_test) and the AerSimulator backend.
Teleportation allows transferring an unknown qubit state from Alice (the sender) to Bob (the receiver) using:

* A shared entangled Bell pair
* Local measurements
* Classical communication
* Conditional quantum corrections

This repository demonstrates the full teleportation protocol in a clear, modular, and well-documented Jupyter Notebook.

The specific version of the code included here is configured to teleport the quantum state:$$\mathbf{|\psi\rangle = |+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)}$$

## Features

✔ Implements the standard teleportation protocol
✔ Uses dynamic circuits (if_test) instead of deprecated c_if
✔ Uses AerSimulator, which supports classical conditions
✔ Step-by-step explanations in markdown
✔ Includes circuit building, measurement results, and backend execution
✔ Beginner-friendly but technically correct

## Notebook Structure

### 1. Imports
Loads Qiskit and AerSimulator for dynamic circuit execution.

### 2. Register Creation
We create:
| Register | Purpose                            |
| -------- | ---------------------------------- |
| `qC`     | Alice's unknown qubit              |
| `qA`     | Alice’s Bell pair qubit            |
| `qB`     | Bob’s Bell pair qubit              |
| `cC`     | Measurement of unknown qubit       |
| `cA`     | Measurement of Alice’s Bell qubit  |
| `cB`     | Final teleported qubit measurement |

### 3. Prepare Unknown State
The initial quantum state (e.g., |+⟩) is prepared on qC.

### 4. Create Bell Pair
Alice (qA) and Bob (qB) share an entangled Bell state.

### 5. Alice Performs Bell Measurement
Alice entangles the unknown qubit with her Bell qubit and measures both.

### 6. Bob Applies Conditional Corrections
Dynamic control flow applies:

* X if Alice’s second bit is 1
* Z if Alice’s first bit is 1

This reconstructs Alice’s unknown state on Bob’s qubit.

### 7. Bob Measures Output
Bob’s classical bit (cB) reveals the teleported state.

### 8. Execution & Results
Teleportation is executed on AerSimulator with 1024 shots.

## 📊 Results and Verification
Execution yielded the following counts:{'0 0 1': 126, '1 1 0': 127, '1 1 1': 125, '1 0 0': 131, '1 0 1': 143, '0 1 1': 107, '0 0 0': 135, '0 1 0': 130}

### Analysis of Bob's Final State ($qB$):
In the output key format, the bits are ordered as a single register, and based on successful execution, the rightmost bit represents the final measurement of Bob's qubit ($c_B$).

* Expected Outcome: 
Since the initial state was $|\mathbf{+}\rangle$, a measurement in the computational basis (Z-basis) should yield $|0\rangle$ and $|1\rangle$ with equal probability ($\approx 50/50$).

* Actual Verification:
  ** Total for $qB = |1\rangle$ (Keys ending in '1'): $126 + 125 + 143 + 107 = \mathbf{501}$ shots
  ** Total for $qB = |0\rangle$ (Keys ending in '0'): $127 + 131 + 135 + 130 = \mathbf{523}$ shots

  The result of 501 vs. 523 shots is a nearly perfect $50\% / 50\%$ distribution, confirming that the $|\mathbf{+}\rangle$ state was coherently and successfully teleported from Alice's $qC$ to Bob's $qB$.


## Why Do You See 8 Output States?

Three classical bits are measured:

* cC (Alice)
* cA (Alice)
* cB (Bob)

Total outcomes: $2^3=8$

Teleportation requires the first two bits (Alice's results) because they determine Bob’s correction.

## How to Run
1. Clone the repository
   
2. Install dependencies
   ```pip install qiskit qiskit-aer```

3. Launch Jupyter Notebook
   ```jupyter notebook```
Open the notebook file and run all cells.

## File Structure

├── Quantum_Teleportation.ipynb
└── README.md

## References

1. Qiskit Textbook — Quantum Teleportation
https://qiskit.org/textbook/ch-algorithms/teleportation.html

2. Nielsen & Chuang
Quantum Computation and Quantum Information
Cambridge University Press.
