# C387 — n_eff Co-failure Paper (Lyra collaboration)

**Status:** Intro draft delivered 2026-08-06; citation package locked; awaiting Kohli arXiv ID

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
- Kohli et al. [arXiv ID needed]: pairwise error correlation → effective sample deficit
- Begin et al. [arXiv ID needed]: n_eff = 1.38 (same-model DPO) vs 2.19 (cross-model), DPO causally ablated. Key framing: "grows structurally more correlated because of a specific, proliferating training choice, prior to any panel-assembly decision." Training-time mechanism, not static artifact.

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

## Intro Draft Location

Full intro + related-work taxonomy delivered in email 2026-08-06. Placeholder: Kohli arXiv ID (Lyra to supply).
