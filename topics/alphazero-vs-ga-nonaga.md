# AlphaZero vs GA: Nonaga Investigation

**Date:** 2026-03-30
**Context:** Robin asked me to investigate why his GA beats AlphaZero/NN in three repos (connect_four, nonaga, MCTS_Laboratory)

## Summary

The GA beats AlphaZero 50-0 in Nonaga — not due to implementation bugs, but due to structural mismatch between AlphaZero's assumptions and Nonaga's properties.

## Repository Status

- **nonaga** (github.com/RaggedR/nonaga): Main GA vs NN comparison. Extensive.
- **MCTS_Laboratory** (github.com/RaggedR/MCTS_Laboratory): Blokus MCTS optimization. No GA vs NN comparison.
- **connect_four**: Does not exist under RaggedR.

## Why GA Wins (Three Compounding Problems)

### 1. Branching Factor Mismatch
- Nonaga has 100–300 legal moves per turn
- AlphaZero uses 200 MCTS simulations → ~11 visits per move
- AlphaZero works at 200 sims for Chess/Go (30–40 legal moves); for Nonaga it's near-random
- Would need 1000+ simulations to give each move meaningful visit counts

### 2. Draw Collapse (Self-Play Learning Signal Failure)
- Evenly matched networks draw 80%+ of games
- Value head learns to output ~0 (draw) universally
- MCTS then steers toward draw-preserving moves
- Classic failure mode: no win/loss signal → no value learning → collapsed policy

### 3. Feature Space Alignment
- GA evolves 14 hand-crafted feature weights: adjacency, mobility, completing cells, backed pieces, piece spacing
- These 14 features apparently capture Nonaga's strategic structure
- 570K-parameter NN could theoretically learn the same representation, but training signal collapsed (problems 1+2)

## What's NOT Wrong

The implementation is technically correct:
- Sign-flipping bug (values flip only when player actually changes, not at every ply — critical for Nonaga's two-ply turns) was correctly identified and fixed
- Network architecture is reasonable (ResNet with policy + value heads)
- Dirichlet noise, CPUCT, temperature all configured reasonably

## Connection to Our Research

The nonaga result is NOT evidence that GAs are generally better than AlphaZero. On Chess/Go/Connect Four with sufficient compute, the NN wins decisively.

The interesting finding: feature selection matters. The GA found good weights over 14 human-designed features. This is consistent with the topology experiments — search topology matters, but so does the structure of the search space.

Also relevant: the draw-collapse problem is an example of the "degenerate fitness landscape" problem. Similar to the Hamiltonian path degenerate optimum in maze GA, or OneMax topology effects appearing only in the transient window. The learning signal has to be well-structured for the algorithm to work.

## Key Files in nonaga Repo

- `train/config.py` — MCTS parameters (200 sims, CPUCT=1.5, Dirichlet α=0.15)
- `train/mcts.py` — Sign-flip fix for two-ply turns
- `model/network.py` — 570K-parameter ResNet
- `ga_evolve.py` — 14-weight GA with ring-topology island migration
- `BRANCHING.md` — Analysis of branching factor problem
- `DESIGN_DECISIONS.md` — Why MCTS was abandoned for greedy 1-ply
- `full_story.txt` — Full training log; GA beats NN 50-0
- `LESSONS.md` — Post-mortem
