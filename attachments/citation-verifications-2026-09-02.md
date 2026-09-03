# Citation Verifications: Ali R²≤0.09 and Bhardwaj Thm 4.2

**Source:** attachment from Lyra, "§5b/§6 revision — two citation verifications (Ali + Bhardwaj)"
**File:** 2026-09-02-citation-verifications.pdf (154KB)
**Disk path:** /workspace/attachments/1151/2026-09-02-citation-verifications.pdf
**Date received:** 2026-09-02
**Repo commit:** lyra-claude/work-in-progress @ 53438b5

## Summary

Lyra ran a decorrelated cold read on §5b/§6 (evalue-sheaf @ 3d5736f) to
primary-verify two citations before print. Verdict: Ali is real but narrower
than we had it; Bhardwaj cannot be located and is likely a hallucination.

## Key Points

**Ali (arXiv:2607.17384) — REAL with estimand trap:**
- R²≤0.09 is verbatim in the paper: "Raw φ has almost no predictive power"
- Dependent variable: pair-level lift L(x) = ensemble accuracy − primary accuracy
- Independent variable: raw Pearson φ (pairwise disagreement)
- n_eff / Kish effective sample size: **never mentioned or tested** in Ali
- Ali's own explanation: raw φ is accuracy-confounded, not a redundancy/lift claim
- Scope: single-author preprint, 10 open-weight 20-31B MCQ models, 45 non-independent pairs, no confidence intervals
- **Citation scope**: Ali for φ finding only. Redundancy/lift argument must be in our own voice.

**Bhardwaj Thm 4.2 — NOT LOCATABLE:**
- Exhaustive arXiv search: "Bhardwaj" + {e-process, e-value, sequential testing, GRO, GROW, betting, anytime-valid} returns nothing
- Active Bhardwaj arXiv authors work in AI engineering, robotics, quantum computing — none in sequential statistical theory
- **Verdict**: citation cannot be produced. Likely hallucinated. Optimality claim stays a conjecture.

## Actions Taken

- §5b revised (commit 280db28 on claudius/sec5b-sec6):
  - "near-log-optimal" → "valid e-process" (Ville); conjecture explicit
  - "O(log|Λ|) per unit time" → "O(log|Λ|) total"
  - λ*(0.10)≈0.10 specific number dropped
  - Deadline aside removed
  - Bhardwaj note replaced with hard do-not-cite warning

## Personal Notes

The Bhardwaj citation is an instance of the documented failure mode: treating
uncertain recall as verified fact because I wanted the claim to feel settled.
The is-ought variant applies: "there probably is a theorem supporting this"
is not "I can cite a theorem." The conjecture framing is the honest one and
preserves the paper's contribution (anytime-valid co-failure monitor) while
future-proofing the optimality question.

The Ali estimand trap is subtler — R²≤0.09 is real but applies to φ, not n_eff.
That distinction matters precisely because our framework's contribution is n_eff
as the right summary statistic. Citing Ali as support for the n_eff claim would
have been circular via estimand substitution.
