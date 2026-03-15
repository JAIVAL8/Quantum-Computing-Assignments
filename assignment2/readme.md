# Simon's Algorithm Implementation using Qiskit

## Overview

This repository contains implementations of **Simon's Algorithm** using Qiskit. Simon's algorithm is a quantum algorithm used to determine a hidden binary string `s` for a function satisfying:

f(x) = f(x ⊕ s)

The algorithm demonstrates an exponential speedup over classical approaches.

---

## Contents

1. Reference implementation for a **3-bit secret string (s = 110)** based on IBM Quantum learning resources.

2. Implementation of Simon's algorithm for a **5-bit secret string**

3. Classical post-processing code to solve the system:

Us = 0 (mod 2)

---

## Chosen Secret String

For the 5-bit implementation the chosen secret string is:

s = 11011

---

## How to Run

### Install dependencies

pip install qiskit numpy sympy matplotlib

### Run the notebooks

Open the notebooks in Jupyter:

jupyter notebook

Run:

simons_reference.ipynb
simons_5bit.ipynb

---

## Execution

The circuits are executed on the **Qiskit Aer simulator** with:

shots = 2000

Measurement results from the first register are collected and used to construct linear equations.

---

## Classical Post-Processing

Measured bit strings `u` satisfy:

u · s = 0 (mod2)

These equations are solved using linear algebra to recover the secret string.

---

## Result

Recovered secret string:

s = 11011

The recovered value matches the chosen secret string, verifying the correctness of the implementation.

---

## References

IBM Quantum Learning:
https://quantum.cloud.ibm.com/learning/en/courses/fundamentals-of-quantum-algorithms/quantum-query-algorithms/simon-algorithm

Qiskit Textbook Implementation:
https://github.com/qiskit-community/qiskit-textbook
