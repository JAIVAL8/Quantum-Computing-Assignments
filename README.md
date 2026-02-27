# Quantum Computing Assignment 1

This repository contains the material for a quantum computing assignment covering
quantum teleportation and superdense coding. All work is contained in the
Jupyter notebook JP_QC_Assignment1.ipynb.

---

## Repository Contents

- **JP_QC_Assignment1.ipynb** Python notebook demonstrating the required
  circuits and including written answers to the conceptual questions.

---

## Requirements

Install the following packages in a Python 3.8+ environment:

`sh
pip install qiskit qiskit-aer numpy matplotlib jupyterlab
`

The notebook was tested with Qiskit 0.41 and Aer simulator 0.11; later versions
should remain compatible.

---

## Running the Notebook

1. Clone this repository and navigate into it:
   `sh
git clone https://github.com/yourusername/yourrepo.git
cd yourrepo
`
2. (Optional) Create and activate a virtual environment:
   `sh
python -m venv venv
venv\\Scripts\\activate   # Windows
source venv/bin/activate  # macOS/Linux
`
3. Launch Jupyter Lab or Notebook and open the assignment file:
   `sh
jupyter lab
`
   Then locate and open JP_QC_Assignment1.ipynb in the browser interface.
4. Execute the cells in order. The code sections simulate the circuits on the
   Aer backend, while markdown cells explain each step and include answers to
   the questions.

> **Note:** No external APIs or hardware are needed; all simulation happens
> locally.

---

## Overview of Implemented Protocols

### Quantum Teleportation

The notebook prepares an arbitrary single-qubit state using rotation gates.
Alice and Bob share a Bell pair, and coherent controlled gates (CX, CZ) perform
corrections without measurement. Finally, the inverse of the preparation
unitary is applied to Bobs qubit to verify that teleportation succeeded.

### Superdense Coding

Alice encodes two classical bits by applying Pauli operators to her qubit of
a shared Bell pair. She then sends the qubit to Bob, who performs the Bell
measurement to recover the two bits.

---

## Additional Notes

- Change the theta and phi parameters in the teleportation cell to test
  different input states.
- The histogram in teleportation should show the |0> state after applying the
  inverse unitary.
- Only a single shot is used for superdense coding since the output is deterministic.

---

## License

This repository is provided under a public-domain/CC0 dedication. Feel free to
reuse and adapt the code for educational purposes.

---

_Generated February 27, 2026_
