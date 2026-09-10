# Learning session — sliceTCA paper

Paper: **"Tensor decomposition of neural data using sliceTCA"**, Nature Neuroscience (2024)

Source: https://www.nature.com/articles/s41593-024-01626-2

## Goal

Understand enough background to read the paper confidently: why sliceTCA was introduced, the mathematical decomposition, how it differs from PCA and standard TCA/CP decomposition, how to read the main figures, and what the neuroscience results actually demonstrate.

Implementation details are secondary unless explicitly requested later.

## Teaching protocol for this session

Follow the repository `skills/teach/SKILL.md` protocol.

- Teach one dependency-graph node at a time.
- Start from absolute basics when a prerequisite is not secure.
- Use visual/interactive HTML material when it materially improves understanding.
- After each taught node, ask exactly **one** focused **4-option multiple-choice** check in chat and wait for the learner's answer before advancing.
- Do not re-probe prerequisite strands already bracketed below unless the learner's later answers reveal a misconception.

## Probe result

### Established floor

The learner has a usable intuitive understanding of:

- vectors and high-dimensional population-activity representations;
- low-dimensional subspaces / underlying degrees of freedom;
- scalar multiples of vectors and independent directions at an intuitive level;
- covariance, including the sign of covariance;
- PCA as finding directions of maximal variance;
- 3D tensors with axes such as `[neuron, time, trial]`;
- latent variables;
- the outer product of two vectors, including computing a simple example.

### Current ceilings / gaps

The learner does **not** yet have a secure understanding of:

- PCA as a low-rank matrix approximation;
- rank-1 tensors / separability across three axes;
- standard tensor component analysis / CP decomposition;
- slice-rank-1 tensors and sliceTCA.

## Approved dependency graph

```text
Established foundations
        │
        ├─ vectors + dimensions
        ├─ covariance
        ├─ PCA intuition
        └─ 3D neural tensors
                │
                ▼
1. Linear dependence
        │
        ▼
2. Matrix rank
        │
        ▼
3. Rank-1 matrix = outer product of 2 vectors
        │
        ▼
4. PCA as low-rank matrix approximation
        │
        ▼
5. Rank-1 tensor = outer product of 3 vectors
        │
        ▼
6. Standard TCA / CP decomposition
        │
        ▼
7. Why standard TCA is too restrictive for the target structures
        │
        ▼
8. Slice-rank-1 tensor = vector × matrix
        │
        ▼
9. The three sliceTCA covariability classes
   neuron / time / trial
        │
        ▼
10. PCA vs TCA vs sliceTCA
        │
        ▼
11. Read and understand Figure 1
        │
        ▼
12. Understand the experiments, figures, and results
        │
        ▼
GOAL: understand the paper and its contribution
```

## Teaching design note

The central conceptual click should happen around nodes 3–9:

- `vector ⊗ vector` → rank-1 matrix;
- `vector ⊗ vector ⊗ vector` → standard rank-1 tensor, strongly separable across all three axes;
- `vector ⊗ matrix` → slice-rank-1 structure, which relaxes that separability in a controlled way.

Use interactive visualization for this transition if possible, because the learner is strongly visual.

## Progress

- **Node 1 — Linear dependence: COMPLETE (2026-09-10).** Learner understood scalar-multiple/collinearity intuition and passed the required check.
- **Node 2 — Matrix rank: COMPLETE (2026-09-10).** Initial check exposed a tendency to count columns rather than independent directions. After repair, learner correctly identified rank 3 when one of four columns was redundant and a fourth introduced a third independent direction.
- **Node 3 — Rank-1 matrix = outer product of 2 vectors: COMPLETE (2026-09-10).** Learner correctly identified that `[[2,-1],[4,-2],[6,-3]]` has rank 1 because its second column is `-1/2` times the first, confirming the outer-product/rank-1 connection.
- **Node 4 — PCA as low-rank matrix approximation: IN PROGRESS.**

## Current status

Plan approved on 2026-09-10. Probe phase is complete. Do **not** restart the probe when resuming this same session unless later answers expose a foundational problem.

**Next step: Phase 3, Node 4 — PCA as low-rank matrix approximation.**

## Resume prompt

In a new ChatGPT conversation with GitHub connected, use:

```text
@GitHub Read rbianc0/ai-learning/README.md and rbianc0/ai-learning/sessions/slicetca-paper.md, then continue the sliceTCA paper learning session from the saved checkpoint.
```
