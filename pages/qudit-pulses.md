---
title: "Quantum optimal control for high radix computation"
---

[← back to home](../index.md)

# Quantum optimal control for high radix computation

In the summer of 2021, I began research with the <a href="https://www.epiqc.cs.uchicago.edu/" target="_blank" rel="noopener noreferrer">EPiQC</a> group at the University of Chicago (I will now be starting a Ph.D. there in September) working under advisor Fred Chong. My goal was to determine the durations of high radix quantum logic gates, which I did by generating optimal quantum control pulses for various gates. The purpose of this research was to determine whether high radix computation offered a speed advantage over typical 2-state quantum computing.

This project has led to a poster at QIP 2022 and publications at <a href="https://arxiv.org/abs/2206.14975" target="_blank" rel="noopener noreferrer">QCE 2022</a> and ASPLOS 2023 (under review).

### High radix quantum computation

---

Quantum computing typically involves the use of qubits, quantum objects with two distinct states, in analogy to classical bits. Due to the exponential scaling capability of quantum, every qubit matters, especially in the relatively small machines (~100 qubits) in use in the near future. Often, the states of a qubit are the two lowest-energy states of a potentially infinite number - in superconducting quantum computers, a qubit uses the lowest two energy levels of a quantum harmonic oscillator, ignoring the higher-energy states. A qu*dit* is the generalization of a qubit to *d* distinct states (radix > 2), which can store more information than a 2-state qubit without taking up a larger footprint on a device, making it an interesting topic of study. 

In particular, a 4-state qudit (or *ququart*) can completely encode the information of 2 qubits, by encoding the information as in the following table:

Qubit A state | Qubit B state | Ququart state
--- | --- | ---
$$\ket{0}$$ | $$\ket{0}$$ | $$\ket{0}$$
$$\ket{0}$$ | $$\ket{1}$$ | $$\ket{1}$$
$$\ket{1}$$ | $$\ket{0}$$ | $$\ket{2}$$
$$\ket{1}$$ | $$\ket{1}$$ | $$\ket{3}$$

This encoding process can be done in the middle of a quantum circuit, transferring all information of the original two qubits into one of them after promoting it to a ququart and leaving the other qubit as an *ancilla*, an unused bit that is useful in certain quantum computations to hold intermediate data.

I investigated the relationship between qudit dimension *(d)* and the time it takes to apply a logic gate. Previous theoretical work had established that gate duration could be proportional to *d* squared in the worst case, which would make qudit circuits prohibitively slower than qubit-only circuits. However, we found that in practice these gates can be done more efficiently, opening the door to many new possibilities.

### Quantum optimal control

---

In quantum computers, logic gates are applied through control pulses - time-dependent fields such as lasers that drive transitions between qubit states. Quantum optimal control aims to find the ideal control pulse sequence to perform a specified operation. Below is an example of the optimized control pulse and resulting state transition for a single *qutrit* X+ gate (which sends state 0 to 1, state 1 to 2, and state 2 to 0).

![x-pulse](/files/x-pulse.png) ![x-transition](/files/x-transition.png)

Control pulses can also be designed to apply 2-bit gates, the most common of which is the CNOT gate. The CNOT gate applies a NOT operation on the target qubit when the control qubit is in state 1, and does nothing if the control qubit is in state 0. The CNOT, along with several single-qubit gates, forms a universal gate set - meaning that any quantum computation can be written in terms of CNOTs and single qubit gates. Typically, 2-bit gates take far longer to apply than single-bit gates (around ~10x longer), and are also more error-prone.

Previously, the EPiQC research group had found several theoretical improvements to quantum circuits using qutrits or general qudits. For example, a general Toffoli gate (performs a NOT operation on the target qubit if and only if all *n* controls are set to 1) typically takes *O(n)* two-qubit gates to perform without ancilla, but using qutrits instead of qubits decreases this to *O*(log*n*), an exponential improvement (see their <a href="https://arxiv.org/pdf/1905.10481.pdf" target="_blank" rel="noopener noreferrer">paper</a> for more). However, this improvement is not practical if qutrit gates take far longer to perform than qubit gates, nullifying the potential speedup. To determine whether this theoretical improvement is physically possible, I began generating qudit control pulses to determine gate times.

### Qudit circuit improvements

---

While exploring various qudit gates, we found that a single-ququart gate that swapped the states 2 and 3, known as the X<sub>23</sub> gate, could be performed almost as fast as a standard single-qubit NOT gate (i.e. very fast). Interestingly, if the ququart is thought of as an encoding of 2 qubits together, this X<sub>23</sub> gate performs a CNOT between the two encoded qubits, switching the populations of the "10" and "11" states of the ququart, since a CNOT swaps the 0 and 1 states of the target qubit when the control qubit is in state 1. This is interesting because a CNOT between two qubits typically takes a long time and has a lower success rate, while performing it within a single qudit like this appears to be possible in much shorter time with higher fidelity.

For a typical IBM-style transmon system, this "internal CNOT" gate is around 10x faster than running a standard CNOT on two qubits, meaning that for certain quantum circuits, careful use of ququarts in intermediate steps could lead to improvements in both time (faster-running circuits) *and* space (using fewer physical qudits, due to qudit-ququart compression).

### Current and future work

---

We presented our initial pulse work at QIP 2022, poster #650, and will present a <a href="https://arxiv.org/abs/2206.14975" target="_blank" rel="noopener noreferrer">paper</a> on our optimal control methods at QCE 2022 in September.

We have written a compiler that takes advantage of ququart compression to reduce circuit error and increase near-term computational power of quantum computers. This paper is currently under review for the ASPLOS 2023 conference. 

In general, qudits are expected to be more error-prone than qubits since they occupy higher energy states. We are still investigating this and working to quantify the error rates. It remains to be seen whether these errors will prove prohibitive and require us to wait for higher precision quantum computers, but for now we are hopeful that the approach will be useful even in today's noisy devices.

[← back to home](../index.md)