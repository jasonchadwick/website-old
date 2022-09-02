---
title: "Decomposing arbitrary unitaries into multi-controlled X gates"
---

[← back to home](../index.md)

# Decomposing arbitrary unitaries into multi-controlled X gates

One benefit of neutral atom quantum computers is that they can natively support multi-qubit gates (typically in the form of multi-controlled Z gates). Most quantum compilers focus on decomposing all the way down to CNOTs or other two-qubit gates. Some tools such as [GEYSER](https://dl.acm.org/doi/10.1145/3470496.3527428) have been developed to turn these CNOT-based circuits back into multi-controlled circuits, and [others](https://arxiv.org/pdf/2102.08451.pdf) have avoided further decomposition of three-qubit gates, but none have explicitly decomposed arbitrary circuits into multi-controlled gates from the start.

### Recursive cosine-sine decomposition

---

[← back to home](../index.md)