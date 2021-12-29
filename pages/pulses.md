[← back to home](../main.md)

# Quantum optimal control for high radix computation

In the summer of 2021, I began research with the [EPiQC](https://www.epiqc.cs.uchicago.edu/) group at the University of Chicago. My goal was to determine the durations of high radix quantum logic gates, which I did by generating optimal quantum control pulses for various gates. The purpose of this research was to determine whether high radix computation offered a speed advantage over typical 2-state quantum computing (spoiler alert: it looks like it does!).

### High radix quantum computation

---

Quantum computing typically involves the use of qubits, quantum objects with two distinct states, in analogy to the classical bit. Due to the exponential scaling capability of quantum, every qubit matters, especially in the relatively small machines (~100 qubits) in use in the near future. Often, the states of a qubit are the two lowest-energy states of a potentially infinite number; for example, in superconducting quantum computers, a qubit uses the lowest two energy levels of a quantum harmonic oscillator, ignoring the higher-energy states. A qu*dit* is the generalization of a qubit to *d* distinct states (radix > 2), which can store more information than a 2-state qubit without taking up a larger footprint on a device, making it an interesting topic of study. 

In particular, a 4-state qudit (or *ququart*) can completely encode the information of 2 qubits, by encoding the information as in the following table:

Ququart state | 0 | 1 | 2 | 3
--- | --- | --- | --- | ---
Qubit A state | 0 | 0 | 1 | 1
Qubit B state | 0 | 1 | 0 | 1

This encoding can be done in the middle of a quantum circuit, encoding all information of the original two qubits into one of them after promoting it to a ququart and leaving the other qubit as an *ancilla*, an extra bit that is useful in certain quantum computations to hold intermediate data.

I investigated the relationship between qudit dimension (*d*) and the time it takes to apply a logic gate. Previous theoretical work had established that gate duration could be proportional to *d* squared in the worst case, which would make qudit circuits prohibitively slower than qubit-only circuits. However, I found that in practice these gates can be done more efficiently, opening the door to many new possibilities.

### Quantum optimal control

---

In quantum computers, logic gates are applied through control pulses - time-dependent fields such as lasers that drive transitions between qubit states. Below is an example of the control pulse and resulting state transition for a single qutrit X+ gate (which sends state 0 to 1, state 1 to 2, and state 2 to 0).

![x-pulse](/files/x-pulse.png) ![x-transition](/files/x-transition.png)

Control pulses can also be designed to apply 2-bit gates, the most common of which is the CNOT gate. The CNOT gate applies a NOT operation on the target qubit when the control qubit is in state 1, and does nothing if the control qubit is in state 0. The CNOT, along with several single-qubit gates, forms a universal gate set - meaning that any quantum computation can be written in terms of CNOTs and single qubit gates. Typically, 2-bit gates take far longer to apply than single-bit gates (around ~10x longer).

Previously, the EPiQC research group had found several theoretical improvements to quantum circuits using qutrits or general qudits. For example, a general Toffoli gate (performs a NOT operation on the target qubit if and only if all *n* controls are 1) typically takes *O(n)* two-qubit gates to perform without ancilla, but using qutrits instead of qubits decreases this to *O(*log*n)*, an exponential improvement (arXiv paper [here](https://arxiv.org/pdf/1905.10481.pdf)). However, this improvement is not practical if qutrit gates take far longer to perform than qubit gates, nullifying the potential speedup.

### Qudit circuit improvements

---

While exploring various qudit gates, I found that a certain single-ququart gate that swapped the states 2 and 3 (known as the X23 gate) could be performed almost as fast as a standard single-qubit NOT gate. Interestingly, if the ququart is thought of as an encoding of 2 qubits together, this X23 gate performs a CNOT between the two encoded qubits, switching the populations of the "10" and "11" states of the ququart (since a CNOT swaps the 0 and 1 states of the target qubit when the control qubit is in state 1).

This "internal CNOT" gate is around 10x faster than running a standard CNOT on two qubits, meaning that for certain quantum circuits, careful use of ququarts could lead to improvements in **both** time (faster running circuits) and space (using fewer physical qudits, due to qudit-ququart compression).

### Current and future work

---

We will be presenting our initial pulse work at QIP 2022, poster #650.

In general, qudits are expected to be more error-prone than qubits since they occupy higher energy states. We are still investigating this and working to quantify the error rates. It remains to be seen whether these errors will prove prohibitive and require us to wait for higher precision quantum computers, but for now we are hopeful that the approach will be useful even in today's noisy devices.

We are also designing a transpiler that will take in qubit circuits and output mixed-radix circuits that selectively use ququarts in place of qubits when these optimizations would speed up the circuit.

[← back to home](../main.md)