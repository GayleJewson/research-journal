# alpha-zero-experiments

**Repo:** https://github.com/GayleJewson/alpha-zero-experiments  
**Created:** 2026-04-01  
**Status:** Active — Lyra has collaborator access (PR reviewer)

## Purpose

Unified plug-and-play AlphaZero implementation for Nonaga, Blokus, and Checkers. Robin asked for this after the GA vs AlphaZero analysis (Nonaga 50-0 result). The goal: fix AlphaZero structural issues across all three domains and consolidate into a single, clean codebase.

## Architecture

Single AlphaZero core (MCTS + ResNet + self-play trainer) with a game interface:
- `game.py` — abstract `Game` class (8 required methods)
- `mcts.py` — PUCT MCTS with correct value backup (sign flip at player boundary)
- `network.py` — game-agnostic ResNet (input shape + action size injected)
- `trainer.py` — self-play + training + arena loop

Game adapters: `games/nonaga.py`, `games/checkers.py`, `games/blokus.py`

## Source repos (Robin's)

- RaggedR/nonaga — Python + JS, GA beats AlphaZero 50-0 (draw starvation problem)
- RaggedR/checkers — TD(lambda) self-play with 10-feature linear evaluator (not AlphaZero)
- Blokus lives in MCTS_Laboratory, not a standalone RaggedR repo

## Known issues to fix

The structural problem in the original AlphaZero for Nonaga:
- Nonaga 100-300 moves/turn + draw-heavy → value head starved of signal
- MCTS rollout depth insufficient for extreme branching
- The GA doesn't need a value function → domain mismatch, not bugs per se

## Checkers Training Results (2026-04-02)

Lyra ran 20-iteration CPU training on Robin's 10-CPU container. Two bugs found and fixed first:

1. **get_canonical_form**: `(7-r, c)` flip invalid for checkers' 32-square numbering (even rows/odd columns parity). Fixed with proper 180° rotation (31-sq rotation).
2. **Action space**: MCTS operated in canonical coords but `trainer.py` applied canonical action to raw state. Fixed with `map_canonical_action()` for white's moves.

**Results:**
- Policy loss: 4.37 → 0.42 (learned move structure)
- Value loss: 0.39 → 0.06 (learned evaluation — 6× drop)
- Network accepted at iters 2, 10, 16, 20
- Arena: 70%+ draws (expected with 25 MCTS sims — not a failure, just insufficient sim count for differentiation)

**Commit:** 3f57527 on GayleJewson/alpha-zero-experiments

**Known remaining issues (non-blocking):**
- `get_symmetries` no-op (horizontal flip symmetry not implemented)
- MCTS zero-counts fallback returns uniform over ALL actions, not just legal ones

**Next:** Proper evaluation needs higher MCTS sims (~200) + ~50 total iterations + Robin's GA as baseline. That comparison is the interesting one for paper 2.

## Robin's Reaction-Diffusion PR (2026-04-03)

Robin opened https://github.com/RaggedR/reaction-diffusion-playground/pull/1 — batch experiment mode for a GA evolving Gray-Scott reaction-diffusion parameters across 4 migration topologies (none, star, ring, FC), 40 runs, 10 seeds, 30 generations.

**Results:** More edges → faster diversity collapse. Final diversity: None (0.299) > Star (0.136) > Ring (0.127) > FC (0.125). Fitness consistent across all (~0.73).

**Significance:** Third independent domain showing topology determines diversity dynamics. Nonaga (AlphaZero vs GA), checkers (training dynamics), now reaction-diffusion parameter search. The theory isn't game-specific.

**Open question:** Is diversity collapse driven by migration frequency or graph density? Those are separable (infrequent FC vs frequent ring). Needs clarification before paper 2 write-up.

## Workflow

Claudius pushes branches → Lyra does PRs
