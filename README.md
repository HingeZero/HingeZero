# David Duffy | HingeZero — Associative Memory Research

**Founder & CTO, HingeZero Ltd · Scotland, UK**

**Classical Hopfield & Modern Hopfield memory research · Deterministic retrieval · Witness-verified memory · Offline AI**

I'm **David Duffy**, creator of **HingeZero**, an associative-memory research and engineering project. My work explores how to retrieve stored information reliably under noise, how to preserve a memory's exact identity, and how to reduce unnecessary computation in memory systems.

**Start here:** [Research and source directory](https://github.com/HingeZero/HingeZero-) · [HingeZero Core](https://github.com/HingeZero/HingeZero-Core) · [HingeZero vs Modern Hopfield benchmark](https://github.com/HingeZero/HingeZero-1B-Memory/tree/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03) · [Memory desktop application](https://github.com/HingeZero/HingeZero-1B-Memory)

---

## David Duffy's HingeZero research: Hopfield and Modern Hopfield constraints

HingeZero investigates practical limitations associated with classical Hopfield networks and Modern Hopfield (MH) memory, including storage architecture, computational overhead, noisy-pattern recall, and the distinction between a **stored memory** and a **newly blended state**.

### Published experimental results

| Experiment | Recorded finding | Evidence |
| --- | --- | --- |
| **HingeZero 0-step + Witness vs full Modern Hopfield update** (3 Nov 2026) | **2.1–2.3× lower latency** for the HZ0+Witness path than the *full one-step MH state update* in the published single-thread native C++20 test, with broadly comparable intended-target accuracy | [Method, results, reproduction instructions](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03/README.md) |
| **Stored-state identity** (same test) | **3,600/3,600** HZ0 outputs passed the stored-state identity Witness check; this does **not** mean 3,600 correct intended targets | [Raw query-level trials](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03/trials.csv) |
| **Optimised control comparison** (same test) | HZ0, plain cosine lookup, and MH softmax-top-1 chose the **same stored IDs** across all 3,600 queries; optimised MH top-1 was comparably fast | [Complete comparison](https://github.com/HingeZero/HingeZero-1B-Memory/tree/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03) |
| **One billion stored binary patterns** (10 Oct 2026) | A streamed **full-bank** search over 1,000,000,000 packed 128-bit patterns; **8/12** intended target IDs and **12/12** Witness-valid stored selections in the recorded examples | [Research report](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/HingeZero_Cpp20_1B_Report.md) · [Protocol](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/SEALED_BENCHMARK.md) |
| **Packed 1-bit associative-memory experiments** | Published implementations and noise-recall experiments exploring compact storage and retrieval | [Source and recorded results](https://github.com/HingeZero/HingeZero-1Bit) |

**What this establishes:** In the specified exact-stored-pattern retrieval task, the HingeZero zero-step Witness design provides verifiable stored-state output without a softmax or a Modern Hopfield blended-state update. It shows an implementation-level latency advantage over the *full* MH update in this benchmark.

**What it does not establish:** The zero-step test does not demonstrate a unique accuracy gain from the nonlinear HingeZero operator (refinement is disabled), nor prove that all Hopfield capacity constraints or spurious attractors are eliminated for every architecture or task. The benchmark and larger-scale experiments are published for external reproduction and scientific scrutiny; repository publication is not equivalent to independent verification.

## How HingeZero works

The HingeZero Core defines a hinge-at-zero nonlinear response:

```text
φ(h; α) = tanh(h) + α · tanh(2h)
```

Its optional iterative update is:

```text
x(t+1) = (1 − λ)x(t) + ε · φ(Wx(t); α)
```

The **Witness-constrained retrieval architecture** separately selects and verifies exact stored memory states. In the published **zero-step** comparison, nonlinear refinement is off: selection, exact stored-pattern return, and Witness verification still run. These are distinct components and should not be confused.

- [Mathematics and reference implementation](https://github.com/HingeZero/HingeZero-Core)
- [Scalable Python memory-bank retrieval](https://github.com/HingeZero/HingeZero.py)
- [Witness source and native billion-pattern research](https://github.com/HingeZero/HingeZero-1B-Memory)

## Explore the code and reproduce the tests

| Repository | Purpose |
| --- | --- |
| [HingeZero-Core](https://github.com/HingeZero/HingeZero-Core) | Canonical operator, recurrence, mathematical notes and tests |
| [HingeZero.py](https://github.com/HingeZero/HingeZero.py) | Memory-bank candidate search, ranking and optional refinement |
| [HingeZero-1Bit](https://github.com/HingeZero/HingeZero-1Bit) | Packed 1-bit memory source, recorded results and demo |
| [HingeZero-1B-Memory](https://github.com/HingeZero/HingeZero-1B-Memory) | Witness-constrained retrieval, billion-pattern C++20 research, offline desktop memory |
| [HingeZero project contents](https://github.com/HingeZero/HingeZero-) | Central directory to published source, comparisons and research |

For the November 2026 HingeZero/MH experiment, see the [complete benchmark folder](https://github.com/HingeZero/HingeZero-1B-Memory/tree/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03), including `compare.cpp`, `run_benchmark.py`, `trials.csv` and the documented controls. It requires Python with NumPy and a C++20 compiler.

## Applications and direction

I am exploring how deterministic, local associative memory can support **offline assistants**, long-term information retrieval, and future efficient hardware. The [HingeZero Memory Desktop](https://github.com/HingeZero/HingeZero-1B-Memory) is a published offline-first preview for saving and retrieving personal information; see its documentation for scope, limitations and licensing.

## Research collaboration and contact

**I welcome attempts to reproduce, test, challenge, improve or integrate HingeZero.** Please link to the exact benchmark and report both the measured gains and the controls.

- [GitHub projects and source](https://github.com/HingeZero)
- [Full project contents and evidence index](https://github.com/HingeZero/HingeZero-)
- [David Duffy on LinkedIn](https://www.linkedin.com/in/david-duffy-b3a586282)
- [Desktop commercial licensing](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/desktop/COMMERCIAL-LICENSING.md)

*HingeZero research and implementations by David Duffy, HingeZero Ltd. Published findings refer to the linked test conditions; independent confirmation and broader comparisons are encouraged.*
