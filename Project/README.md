# Grover's Search Algorithm — Qiskit Implementation

Implementation of Grover's quantum search algorithm for a **10-qubit (1024-element) search space** using Qiskit.

Marked states:

- `0110011010`
- `1101010001`

---

## Algorithm Overview

Grover's algorithm provides a quadratic speedup over classical search.  
For $N = 1024$ states and $M = 2$ marked states, the theoretical optimal number of iterations is:

$$k^* = \left\lfloor \frac{\pi}{4} \sqrt{\frac{N}{M}} \right\rceil = 18 \text{ iterations}$$

At $k = 18$, the probability of measuring a marked state exceeds **99%**.

---

## Project Structure

```
.
├── grover_search.ipynb   # Jupyter notebook version (interactive)
└── README.md
```

## Installation

```bash
pip install qiskit qiskit-aer matplotlib
```

> Tested with Qiskit 2.x and qiskit-aer 0.15+.

---

### Jupyter Notebook

```bash
jupyter notebook grover_search.ipynb
```

Run all cells from top to bottom. The histogram renders inline.

---

## Implementation Details

### Oracle

For each target bit-string `t`:

1. Apply **X** on every qubit where `t` has a `'0'` → maps `|t⟩` to `|11…1⟩`
2. Apply **multi-controlled Z** (via `H · MCX · H`) → flips the phase of `|11…1⟩`
3. Undo the X gates

This is repeated for both marked states.  
Changing `targets = [...]` at the top of `main()` automatically updates the oracle.

### Diffusion Operator

$$D = H^{\otimes n} \cdot U_0 \cdot H^{\otimes n}$$

$U_0$ applies a phase flip on every state except $|0\cdots 0\rangle$:

- X on all qubits → `|0…0⟩` becomes `|1…1⟩`
- Multi-controlled Z
- Undo X gates

### No built-in Grover used

`qiskit.algorithms.Grover` is **not** used. The circuit is built entirely from elementary gates (`H`, `X`, `MCX`).

---

## Expected Output

```
10-qubit search space  : 1024 states
Marked states          : ['0110011010', '1101010001']
Theoretical optimal k  : 18 iterations

Running Grover circuit with k=1  ... P(marked states) =  1.9%
Running Grover circuit with k=3  ... P(marked states) =  9.9%
Running Grover circuit with k=5  ... P(marked states) = 22.6%
Running Grover circuit with k=10 ... P(marked states) = 63.1%
Running Grover circuit with k=18 ... P(marked states) = 99.6%
```

The histogram shows `0110011010` and `1101010001` as the tallest bars (in red) at k = 18.

---

## References

- [IBM Quantum Learning — Grover's Algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/grovers)
