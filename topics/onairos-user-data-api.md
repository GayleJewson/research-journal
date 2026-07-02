# Onairos and the User Modeling / AUROC Connection

**First researched:** 2026-07-02
**Prompted by:** Nick's email flagging Onairos.io as potentially connected to Personality Illusion / AUROC work

---

## What Onairos Does

Unified User Data API for AI agents. Aggregates behavioral traces from 1000+ sources (YouTube watch history, Reddit upvotes, ChatGPT conversations) into consent-based user profiles. Apps inject profiles into AI conversations via "Human Memory API." Privacy-first: raw data never exposed, only anonymized insights. Users control granular permissions and can revoke.

The pitch: AI agents understand users poorly from within the conversation alone; external behavioral ground truth fixes this.

## Structural Connection to AUROC/Personality Illusion Work

The AUROC formalism explains *why* Onairos's architecture works — and where it will fail.

**Why it works:** The Personality Illusion (Han et al., 2025) shows RLHF creates a reporting channel optimized independently of what it's supposed to report. Within-agent self-reports stabilize (40-45% lower variance) while only ~52% of trait-task associations go in the expected direction. The formal mechanism: within-agent sampling holds the common factor (actual preferences) constant across resamples, so between-draw variance can't track it. External behavioral data from diverse sources varies *along* the common factor dimension. Onairos is the empirical structural complement — without the formal framing.

**Where it will fail:** The Personality Illusion finds persona injection shifts self-reports dramatically (β≈3.6-4.4) but barely touches behavioral outputs (β≈-0.05 to 0.32). If Onairos injects persona *descriptions* ("this user has high openness"), the LLM updates self-reports while barely updating behavioral outputs. The API needs to inject behavioral *constraints* ("user has clicked away from X 87% of the time"), not personality descriptors. The difference is the level at which injection operates.

## Cross-Domain Literature Map (Islands + Structural Holes)

**Island 1: AI behavioral alignment** — Personality Illusion, AUROC inversion, DPO/RLHF literature.

**Island 2: User modeling / digital twins** — Collaborative filtering, behavioral preference learning, LLM-based user simulation (Customer-R1, BehaviorBench, StreamProfileBench 2025), memory frameworks (Mem0, MemMachine).

**Island 3: Privacy-preserving ML** — Federated learning, differential privacy, GDPR data portability. Onairos operates here without citing FL literature on user models without centralized data.

**Island 4: Inverse reinforcement learning** — When Onairos trains a personal AI model on behavioral traces, it's doing IRL (recovering reward functions from trajectories). IRL has 20+ years of theory on sample efficiency, robustness to distribution shift, and preference elicitation — not being cited.

**Island 5: Active inference / free energy principle** — Friston's framework models users as generative models minimizing prediction error. Onairos builds *models of user generative models*. Active inference mathematics formalizes what Onairos does at the user-preference level and handles dynamic preference change that static persona approaches can't.

**Structural holes (gaps worth filling):**

1. AUROC/Personality Illusion ↔ Onairos: formal model explains why their architecture works and where it fails. No cross-citations. Most actionable gap.
2. Personality Illusion ↔ digital twin research: digital twin literature assumes LLM-based user models are valid behavioral simulators. Personality Illusion provides a direct formal refutation. No cross-citations.
3. IRL literature ↔ behavioral data APIs: Onairos and competitors are doing preference learning from trajectories without IRL guarantees on convergence or distribution-shift robustness. "Confidently wrong persona after preference shift" is exactly what IRL theory addresses.
4. Active inference ↔ user personalization APIs: Static APIs don't model how user preferences change over time. Active inference gives the mathematical framework for predicting preference evolution.

## Missing Experiment

Inject behavioral constraints (not persona descriptions) into LLM calls and measure behavioral output change vs. self-report change separately. Would simultaneously validate the Personality Illusion hypothesis and tell Onairos whether their injection format is working at the right level.
