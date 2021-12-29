[← back to home](../README.md)

# Quantum Optimal Control

In the summer of 2021, I began research with the EPiQC group at the University of Chicago. My goal was to determine the durations of high radix quantum logic gates, which I did by generating optimal quantum control pulses for various gates. The purpose of this research was to determine whether high radix computation offered a speed advantage over typical 2-state quantum computing (spoiler alert: it looks like it does!).

### High radix quantum computation

---

Quantum computing typically involves the use of qubits, quantum objects with two distinct states, in analogy to the classical bit. Due to the exponential scaling capability of quantum, every qubit matters, especially in the relatively small machines (~100 qubits) in use in the near future. Often, the states of a qubit are the two lowest-energy states of a potentially infinite number; for example, in superconducting quantum computers, a qubit uses the lowest two energy levels of a quantum harmonic oscillator, ignoring the higher-energy states. A qudit is the generalization of a qubit to *d* distinct states, which can store more information than a 2-state qubit without taking up a larger footprint on a device, making it an interesting topic of study. 

I investigated the relationship between qudit dimension (*d*) and the time it takes to apply a logic gate. Previous theoretical work had established that gate duration could be proportional to *d*<sup>2</sup> in the worst case, which would make qudit circuits prohibitively slower than qubit-only circuits. However, I found that in practice these gates can be done more efficiently, opening the door to many new possibilities.

### Quantum optimal control

---

(coming soon)
### Qudit circuit improvements

---

(coming soon)

[← back to home](https://jasonchadwick.github.io)