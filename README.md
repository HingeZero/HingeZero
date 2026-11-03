# HingeZero — Project Contents

**Public code, reproducible benchmarks, applications and research from David Duffy / HingeZero.**

This page is the central directory for the [HingeZero GitHub account](https://github.com/HingeZero). Each link opens the actual public source or evidence. It is an index, not a claim that every experiment has been independently reproduced.

**Start here:** [HingeZero Core](https://github.com/HingeZero/HingeZero-Core) · [Python associative memory](https://github.com/HingeZero/HingeZero.py) · [Witness memory and desktop application](https://github.com/HingeZero/HingeZero-1B-Memory) · [Latest HingeZero vs Modern Hopfield benchmark](https://github.com/HingeZero/HingeZero-1B-Memory/tree/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03)

---

## 1. Implementations

| Project | What it contains | Where to start |
| --- | --- | --- |
| **[HingeZero Core](https://github.com/HingeZero/HingeZero-Core)** | The dual-tanh operator, canonical recurrence, definitions and small tests. This is the **recurrence-level** reference, not the complete Witness retrieval architecture. | [Core explanation](https://github.com/HingeZero/HingeZero-Core/blob/main/CORE_IMPLEMENTATION.md) · [Recall test](https://github.com/HingeZero/HingeZero-Core/blob/main/test_associative_recall.py) |
| **[HingeZero.py](https://github.com/HingeZero/HingeZero.py)** | Python memory-bank retrieval, candidate ranking and optional local refinement. | [Python source](https://github.com/HingeZero/HingeZero.py/blob/main/HingeZero.py) · [Overview](https://github.com/HingeZero/HingeZero.py/blob/main/README.md) |
| **[HingeZero 1-Bit](https://github.com/HingeZero/HingeZero-1Bit)** | Packed-binary associative memory experiments and an interactive browser demonstration. | [C++ packed-memory source](https://github.com/HingeZero/HingeZero-1Bit/blob/main/hingezero_core.cpp) · [Recorded results](https://github.com/HingeZero/HingeZero-1Bit/blob/main/Results) · [Demo](https://github.com/HingeZero/HingeZero-1Bit/blob/main/index.html) |
| **[HingeZero Witness / 1B Memory](https://github.com/HingeZero/HingeZero-1B-Memory)** | Witness-constrained stored-state retrieval, C++20 billion-memory research, and the separate offline memory desktop application. | [Original Witness Core](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/HingeZero_Core.py) · [Native C++20](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/HingeZero_Native_1B.cpp) |

**Retrieval-mode distinction:** In the published zero-refinement Witness benchmark, **0 steps** means no dual-tanh refinement; it still performs memory scoring, selection, exact stored-pattern return and Witness identity checks. Refinement is an optional, separately measurable operation. Individual repositories may retain their historical reference defaults and experimental settings.

## 2. Benchmarks and reproducible results

| Experiment | Evidence and source | What was measured |
| --- | --- | --- |
| **0-step HingeZero + Witness vs Modern Hopfield** (3 Nov 2026) | **[Read benchmark report](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03/README.md)** · [All files](https://github.com/HingeZero/HingeZero-1B-Memory/tree/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03) · [C++20 comparison](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03/compare.cpp) · [Raw trials](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/benchmarks/hingezero0-vs-modern-hopfield-2026-11-03/trials.csv) | 3,600 queries per method, matched stored-pattern banks and noisy cues, native single-thread CPU. HZ0+Witness was about 2.1–2.3× faster than the **full** one-step MH update, with comparable target-ID accuracy. Optimised MH top-1 and cosine retrieval were comparably fast and selected the same IDs. |
| **One billion stored 128-bit memories** (10 Oct 2026) | [Research report](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/HingeZero_Cpp20_1B_Report.md) · [Frozen protocol](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/SEALED_BENCHMARK.md) · [12 recorded cases](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/billion_results.csv) · [Reproduction script](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/run_1b.sh) | A 16 GB packed bank, all-bank scan, 8/12 correct target IDs and 12/12 Witness-valid selections in the original run; a few target examples, not a statistical accuracy estimate. |
| **1-bit packed recall** | [1-bit repository](https://github.com/HingeZero/HingeZero-1Bit) · [Results file](https://github.com/HingeZero/HingeZero-1Bit/blob/main/Results) · [Implementation](https://github.com/HingeZero/HingeZero-1Bit/blob/main/hingezero_core.cpp) | Compact binary representation and noisy-pattern recall tests. Consult the source for each test's dimensions, trial count, search stages and refinement settings. |
| **HingeZero Core recall tests** | [Strengths benchmark](https://github.com/HingeZero/HingeZero-Core/blob/main/benchmark_hingezero_strengths.py) · [Associative recall test](https://github.com/HingeZero/HingeZero-Core/blob/main/test_associative_recall.py) · [Unit tests](https://github.com/HingeZero/HingeZero-Core/blob/main/test_hingezero.py) | Controlled experiments with the Core's recurrence and associative matrices. Different from full-bank Witness tests. |

**How to read the numbers:** Witness verification shows that the *selected output is a stored state*; correct-target recall measures whether it is the *intended* memory. These are separate metrics. The results above are reported local experiments; publication of runnable code does not itself imply independent verification.

## 3. Download and use HingeZero Memory Desktop

The desktop memory vault is in [HingeZero-1B-Memory](https://github.com/HingeZero/HingeZero-1B-Memory), alongside — but distinct from — the billion-pattern research kit.

- [Latest desktop preview / releases](https://github.com/HingeZero/HingeZero-1B-Memory/releases/latest)
- [Desktop installation and user guide](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/desktop/README.md)
- [Local application API and integration](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/desktop/README.md#local-api-for-existing-ai-tools)
- [ChatGPT bridge notes](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/desktop/chatgpt-bridge/README.md)
- [Commercial licensing information](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/desktop/COMMERCIAL-LICENSING.md)

The published desktop builds are previews. Consult each release for platform support, checksums, permissions and limitations.

## 4. Benchmark frameworks used for experimentation (forks)

These public repositories are **forks of external benchmark projects**, not standalone evidence of a verified HingeZero score.

| Repository | Upstream framework |
| --- | --- |
| [HingeZero / big-ann-benchmarks](https://github.com/HingeZero/big-ann-benchmarks) | [BigANN Benchmarks](https://github.com/harsha-simhadri/big-ann-benchmarks) |
| [HingeZero / vibe](https://github.com/HingeZero/vibe) | [Vector Index Benchmark for Embeddings](https://github.com/vector-index-bench/vibe) |
| [HingeZero / precisionMemBench](https://github.com/HingeZero/precisionMemBench) | [PrecisionMemBench](https://github.com/tenurehq/precisionMemBench) |

For benchmark submissions, methods and current leaderboard positions, use the relevant framework's official validation process rather than treating a fork or a self-reported run as a confirmed leaderboard placement.

## 5. Repository directory

All public repositories currently listed on this account:

1. [HingeZero-](https://github.com/HingeZero/HingeZero-) — **you are here:** contents and project navigation.
2. [HingeZero-Core](https://github.com/HingeZero/HingeZero-Core) — mathematical reference and core experiments.
3. [HingeZero.py](https://github.com/HingeZero/HingeZero.py) — Python memory-bank implementation.
4. [HingeZero-1Bit](https://github.com/HingeZero/HingeZero-1Bit) — packed 1-bit memory and demo.
5. [HingeZero-1B-Memory](https://github.com/HingeZero/HingeZero-1B-Memory) — Witness, research benchmarks and offline desktop app.
6. [big-ann-benchmarks](https://github.com/HingeZero/big-ann-benchmarks) — forked benchmark framework.
7. [vibe](https://github.com/HingeZero/vibe) — forked vector-index benchmark framework.
8. [precisionMemBench](https://github.com/HingeZero/precisionMemBench) — forked memory benchmark framework.

**Visibility:** This is a directory of **public** HingeZero repositories. Private work is intentionally not disclosed or linked here.

## 6. Licensing, attribution and contact

HingeZero research and software: **David Duffy / HingeZero**. Each repository or component has its own licence or usage terms. In particular, the [offline desktop application has separate noncommercial/commercial terms](https://github.com/HingeZero/HingeZero-1B-Memory/blob/main/desktop/COMMERCIAL-LICENSING.md); do not assume that the licence of HingeZero Core applies to every project.

For technical questions or collaboration, consult the relevant repository's README, issues and contribution guidance.

*Directory prepared 3 November 2026. Links and repository visibility were checked when the contents page was created.*
