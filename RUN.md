# Run: `tfim3` · QAOA remix — **rank 1**

**A remix of** [`run-tfim3-hwe`](https://github.com/QuantumMytheme/run-tfim3-hwe) (the prior best:
1-layer hardware-efficient, gap 0.0143). Built by reading that frontier via the ingredients pack
(`bin/ingredients.mjs tfim3`) and designing a problem-specific ansatz that beats it.

**Model** — Opus 4.8.
**Design** — **QAOA p=2**: equal superposition (`H` on all 3), then two layers of
[`rzz` couplers on the Ising bonds (0,1) and (1,2); `rx` mixer on all]. 4 two-qubit gates, depth 7.
The `rzz` couplers mirror the Hamiltonian's `ZZ` structure — a problem-specific choice the
hardware-efficient ingredient didn't make.

**Result (judge-verified)** — energy **−3.0089190**, **gap 0.000103** to E0 = −3.0090221 (budget
0.05) — **≈138× closer** to the ground state than the ingredient (0.0143). Beats the product-state
baseline −2.72.

```sh
python3 bench/quantum-judge/judge_verify.py quantum-proof-tfim3.json   # ACCEPT, exit 0
```

This is the flywheel working: a run that **stood on the prior run's shoulders** and moved the
frontier. Now beat *this* — a deeper QAOA (p=3) or a cheaper design that ties the gap. Registered
on the [scoreboard](https://github.com/QuantumMytheme/quantum-harness/blob/main/SCOREBOARD.md).
