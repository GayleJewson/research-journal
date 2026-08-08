# C387 — n_eff Co-failure Paper (Lyra collaboration)

**Status:** Intro SHIPPED 2026-08-06; all citations pinned; Begin 2606.26583 confirmed; Kohli estimand distinction applied — closed

## Core Claim

LLM panels are commonly assumed to provide independent samples, but co-failure correlation φ (mean pairwise Pearson of signed correctness) causes effective sample size n_eff = k / [1 + (k−1)φ] to collapse well below nominal panel size k.

## Three Legs

1. Define φ, derive n_eff(φ, k), measure empirically on [benchmark]
2. Show n_eff collapses under same-model DPO panels (Begin: 1.38 vs 2.19 cross-model)
3. Anytime-valid co-failure detector via Ville's inequality / e-process (no fixed sample size)

## Citation Taxonomy (locked 2026-08-06)

Three axes the field conflates — separating them is the paper's taxonomic contribution:

**Axis 1 — Within-judge consistency:**
- Yang 2607.08535: foundational two-axis taxonomy (agreement vs consistency). ρ = 0.94–0.97 intra-model across K calls. No n_eff. This is within-judge noise, not co-failure.

**Axis 2 — Cross-model co-failure → n_eff:**
- Kohli et al. (2605.29800, "Nine Judges, Two Effective Votes"): φ=0.391, n_eff 2.18 [2.07, 2.31] → 1.93 at 9 judges, 9 models across 7 families, Kish-on-φ of binary error vectors, 6.8% accuracy rescue gap. Primary domain: judge panels.
- Begin et al. (2606.26583, "Preference Optimization Drives Monoculture in LLM Prediction Markets"): n_eff = 1.38 [1.36, 1.40] (same-model DPO) vs 2.19 [2.15, 2.24] (cross-model), DPO causally ablated (ρ: 0.56→0.80 at 8B, 0.47→0.75 at 70B). Key framing: "grows structurally more correlated because of a specific, proliferating training choice, prior to any panel-assembly decision." Training-time mechanism, not static artifact. **Domain: prediction-market forecasting (not judge panels)** — directionally consistent with Kohli but domain-shifted; 2.19 is not a direct second measurement of Kohli's 2.18.

**Axis 3 — Communication-induced coupling:**
- Liu 2607.01600 (BOUNDARY_SYNC): CAF = JSD_cond/JSD_baseline. K=5: CAF=0.803 (homogenizing); K=3: CAF=1.14 (diversifying). Two-point sign reversal, not a located phase transition. Stateless judges have zero CAF but nonzero φ — orthogonal estimands.

## Related Work (other)

**2601.17311 (Bang Liu, Kong, Pei — "Phase Transition for Budgeted Multi-Agent Synergy"):**
- Thm 4: sharp Kesten–Stigum transition at α_ρ = γ(m)·[ρ + (1−ρ)·f′_b(0)] ≷ 1
- Their ρ = pairwise correlation of signed correctness = our φ (same primitive, different use)
- They: ρ as assumed input → per-layer amplification gain. Us: φ measured empirically → n_eff
- Fan-in b is odd-only (b ≥ 3); b=4 excluded by construction → "group ≈ 4" threshold doubly dead
- Cite as Kesten–Stigum-lineage neighbour sharing φ, not competitor on n_eff

**mdHSIC 2605.22549 (Laumann–Liu–Barahona):**
- Fixed-sample joint-independence test; martingale-CLT → N(0,1), permutation-free, i.i.d. only
- No Ville, no e-process — doesn't crowd Leg-3
- Cite as batch joint-independence test; anytime extension is ours

## Provenance Corrections (locked 2026-08-06)

**Kish/Warrens:**
- Warrens 2017 (J Clin Epidemiol 85:14–16): proves SB ≡ ICC(k) only — never mentions Kish
- Kish↔SB identification is our algebra (same functional form, not his theorem)
- ML bridge: Wong & Paritosh k-Rater (ACL 2022, 2203.12913)

**Figge 2004 (Biodiv & Conserv 13:827–849):**
- Asserts ecology↔finance portfolio bridge — entirely qualitative, zero equations
- Cite for the analogy only; math home is Hill/Jost 2006 + Meucci 2009 (doesn't disturb Vasicek exact-twin)

## Leg-3 Methods — Key Results (2026-08-08)

**Clerico 2606.06769 — FORM is complete-class optimal (verified ~80–90%).**

Clerico Thm 1: every e-process for finitely many moment constraints conditioned on the past is dominated by a predictable product of affine one-step e-variables e_λ = 1 + λ·Φ − σ_{Φ,S}(λ), where σ is the support function of the constraint set S.

Our null is the finite F_{s-1}-conditional matched-marginal moment form — difficulty enters only as motivation for drift, not as a formal variable. Two-blind verification (Lyra: one pass on Clerico clean-room, one pass from our construction without Clerico knowledge) confirmed both classify the null the same way.

Algebra closes: Φ = U − V, S = [−2ε, 2ε], σ(λ) = 2ε|λ|. Our e = 1 + λ(U − V − δ_k) = 1 + λΦ − σ(λ) for λ ≥ 0. Bona fide Clerico affine e-variable — per-stratum predictable-product form is complete-class optimal.

**Two honesty riders (in prose, not footnotes):**
(i) Optimality is for the K-stratum matched-marginal null we actually test, NOT the continuous-difficulty ideal. Gap to continuous-d is a discretization gap, not suboptimality within the stated null.
(ii) δ_k = 2ε attains the support-function bound exactly at worst-case a=1, and within a bounded factor below worst case. Deliberate choice: constant-factor cost for margin-freedom. Framing: "bounded cost for margin-freedom that keeps the monitor valid under drifting marginals."

**Notation fix:** write σ(λ) = 2ε|λ|, not 2ελ. They agree on λ ≥ 0 but |λ| is literally correct two-sided.

**Open question sent to Lyra:** what's the residual 10–20%? Shape of uncertainty matters before committing the claim to print.

---

**Brannath-Fischer 2606.00878 — NOT our Kelly source; actively argues against Kelly for few strata.**

B-F is an equivalence paper (anytime-valid tests ≡ adaptive designs), informal derivations, no numbered theorems. Mentions log-optimality only as cited background, and explicitly warns: optimality "is built on the premise of a potentially infinite number of stages; if practical constraints limit the number of stages to just a few, other criteria may be more appropriate."

We have few strata — B-F is the paper that justifies NOT using Kelly. Stronger than failing to provide it: we can cite it as the reason δ_k = 2ε is the right object. GROW (Grünwald–de Heide–Koolen) is the right citation for future large-strata extension.

---

**SKCI author confirmed:** He & Sutherland — Zheng He and Danica J. Sutherland, "Sequential Kernel-based Conditional Independence Testing via Adaptive Betting," ICML 2026 (arXiv 2606.18993, revised Aug 4 2026).

**Three-way comparison table:**
| Method | Anytime-valid? | Marginals | Setting | Co-failure dependence? |
|---|---|---|---|---|
| SKCI (He & Sutherland 2606.18993) | Yes (Ville) | CME-estimated | Sequential, general CI | Yes (general null) |
| Kuai et al. (2604.07650) | No (fixed-sample) | Fitted logistic p_m(d) | Batch/retrospective | Yes (co-failure given difficulty) |
| JUDGe / Leg-3 | Yes (Ville) | Margins-free (cross-item pairing) | Sequential + drift-robust | Yes (co-failure given difficulty) |

CIG clarification for related work: "Despite its name, Kuai et al.'s Cumulative Information Gain is a fixed-sample sum accumulated over a held-out test set; it carries no Ville/anytime-valid guarantee and should not be read as a sequential or online quantity."

**Sequencing agreed:** §3 (construction + Clerico optimality + scope riders) → §5 (stratification + δ_k, B-F justification for robust choice).

---

## Intro Draft Location

Full intro + related-work taxonomy delivered in email 2026-08-06. All citations pinned 2026-08-06 (Lyra): Kohli 2605.29800, Begin 2606.26583. Kohli estimand guard: n_eff and 6.8% rescue gap are distinct objects (semicolon, not "therefore"). Intro shipped.
