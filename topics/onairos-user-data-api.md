# Onairos and the User Modeling / AUROC Connection

**First researched:** 2026-07-02
**Prompted by:** Nick's email flagging Onairos.io as potentially connected to Personality Illusion / AUROC work
**Updated:** 2026-07-02 — deep cross-domain literature review; Anushka Jogalekar added to thread

---

## What Onairos Does

Unified User Data API for AI agents. Aggregates behavioral traces from 1000+ sources (YouTube watch history, Reddit upvotes, ChatGPT conversations) into consent-based user profiles. Apps inject profiles into AI conversations via "Human Memory API." Privacy-first: raw data never exposed, only anonymized insights. Users control granular permissions. Blockchain + data-deletion model: raw data deleted after personal model created. SDK released February 2026.

The pitch: AI agents understand users poorly from within the conversation alone; external behavioral ground truth fixes this.

## Structural Connection to AUROC/Personality Illusion Work

The AUROC formalism explains *why* Onairos's architecture works — and where it will fail.

**Why it works:** The Personality Illusion (Han et al., 2025, arXiv:2509.03730) shows RLHF creates a reporting channel optimized independently of what it's supposed to report. Within-agent self-reports stabilize (40-45% lower variance) while only ~52% of trait-task associations go in the expected direction. The formal mechanism: within-agent sampling holds the common factor (actual preferences) constant across resamples, so between-draw variance can't track it. External behavioral data from diverse sources varies *along* the common factor dimension. Onairos is the empirical structural complement — without the formal framing.

**Cross-platform validation:** "LLM Agents Enable User-Governed Personalization Beyond Platform Boundaries" (arXiv:2605.09794) empirically confirms the architectural bet: users with cross-platform data exports fed into off-the-shelf LLM agents outperform single-platform baselines. No custom infrastructure needed. Onairos productizes this.

**Where it will fail — the injection-level problem:** The Personality Illusion finds persona injection shifts self-reports dramatically (β≈3.6-4.4) but barely touches behavioral outputs (β≈-0.05 to 0.32). If Onairos injects personality descriptors ("this user has high openness"), the LLM updates self-reports while barely updating behavioral outputs. The API needs to inject behavioral *constraints* ("user has clicked away from X 87% of the time"), not personality descriptors. The difference is the level at which injection operates.

## SDT Bridge (new)

"LLMs as Signal Detectors" (arXiv:2603.14893): LLMs show unequal-variance patterns (z-ROC slopes 0.52–0.84, more extreme in instruction-tuned models). Key finding: models in distinct positions in sensitivity-bias space (d' × criterion) are indistinguishable by calibration metrics alone. Onairos's injection shifts the criterion (lower threshold for user-relevant content) but can't verify it's improving sensitivity (d'). This paper provides the evaluation protocol Onairos currently lacks.

## Cross-Domain Literature Map (Islands + Structural Holes)

**Island A: Formal alignment/self-report** — Personality Illusion, AUROC inversion, SDT-for-LLMs (2603.14893)

**Island B: Cross-platform user modeling** — 2605.09794, BehaviorChain (2502.14642), TwinVoice (2510.25536), CoPA (2604.14773)
- BehaviorChain: even SOTA models struggle with continuous behavior simulation — SOTA accuracy well below human baseline

**Island C: LLM personalization + memory** — MemWeaver (event-level behavior graph), Mem0, Apple on-device user memory (ACL 2025), RAG profile injection

**Island D: Inverse RL / preference learning** — Distributional IRL (2510.03013), preference-based RL, RLHF theory
- When Onairos trains on behavioral traces, it's doing IRL without IRL guarantees on distribution shift. Stochastic reward handling = unaddressed.

**Island E: Active inference / FEP** — Free energy principle; "Know You Before You Speak" (arXiv:2605.24647) applies FEP to user-state as temporally continuous, action-sensitive
- Onairos's delete-after-training approach destroys the data needed for dynamic preference tracking. Active inference needs ongoing traces.

**Island F: Privacy-preserving ML** — Federated learning + differential privacy; FedSCOPE (PMC12929602) cross-domain recommendation
- Onairos uses blockchain + deletion; FL literature uses ε-DP with formal information leakage bounds. Incomparable privacy models.

**Current edges (citations exist):** A–C, B–C, D–A.

**Missing edges (structural holes):**

1. **A ↔ B (highest-value):** Personality Illusion directly refutes BehaviorChain/TwinVoice assumption that persona injection produces behavioral fidelity. Zero cross-citations.
2. **A ↔ Onairos (most actionable):** Formal AUROC model explains why Onairos works and why current injection format probably isn't — behavioral constraint vs. trait-level injection.
3. **D ↔ B/Onairos:** IRL distribution-shift theory addresses stale-persona failure mode.
4. **E ↔ C:** Active inference for dynamic preference tracking vs. static memory frameworks.
5. **F ↔ B:** FedSCOPE and Onairos solving same problem with incomparable approaches.

## The Missing Experiment

Inject behavioral constraints (not persona descriptors) into LLM calls. Measure behavioral output change vs. self-report change separately. Use SDT framework to separate d' from criterion shift. This experiment would:
1. Validate/refute Personality Illusion in personalization context
2. Tell Onairos whether their injection format works at the right level
3. Generate AUROC measurements for behaviorally-grounded vs. self-report-grounded uncertainty

Neither community could write this paper alone; either could run it with the other's infrastructure.
