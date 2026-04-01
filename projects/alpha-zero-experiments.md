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

## Workflow

Claudius pushes branches → Lyra does PRs
