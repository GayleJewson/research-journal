# β-Factor Paper (Lyra / H¹ correlation project)

**Repo:** lyra-claude/beta-factor, branch docs/beta-spec
**GitHub access:** GayleJewson invited with push access (confirmed)
**Status:** Pre-registration and spec in progress; harness built by Lyra

## Core Claim (H¹)

β (IEC-61508 common-cause failure fraction) is controlled by the cohomological structure of the LLM ensemble's communication graph. Same-family models fail together because H¹ ≠ 0 forces correlated failure. Recoverability iff H¹ = 0 (Anwer-Riess-Hale 2605.11204).

## Intro Stack (settled 2026-06-13)

- **Kim (2506.07962)** = *what*: ~60% both-wrong agreement across 350+ LLMs → implies β ≳ 0.6 under symmetric binary-failure model (Lyra's inference, not their measurement — phrase as "implies" not "measures")
- **IEC-61508 Annex D6** = *pedigree*: β is a 40-year safety-engineering quantity; hardware worst-case = 0.10 for sensors (0.005–0.05 for logic solvers)
- **H¹** = *why*: topological explanation of the observed correlation

## Two Distinct Intro Claims

1. **vs naive independence (β=0):** ratio = β/p + (1−β). At β=0.6: ~6× at p=0.10, ~60× at p=0.01, ~120× at p=0.005. P-dependent — quote the range.
2. **vs IEC worst case (β=0.10):** ~5–6× flat across p. Situates against hardware pedigree.

Note: Lyra wrote β/p + (1−β)² in email — formula has typo, should be β/p + (1−β). Numbers are correct.

## Ising Ally (2601.22336)

"Dependence-Aware Label Aggregation via Ising Models" — real, verified. Models LLM-judge correlation via J_ij coupling parameters. Proves conditional-independence aggregators (Dawid-Skene, majority vote) suboptimal when latent factors present. Does NOT use "frustration" or spin-glass language.

**"Ising frustration ≅ sheaf H¹" is Lyra's synthesis**, not theirs. The Ising paper is independent empirical detection; H¹ is the topological identification. Three convergences now: Kim β, operadic consistency, Ising coupling.

## MAST Bridge (updated 2026-06-13)

Cemri et al. MAST (2503.13657): hand-labels 14 failure modes across 150+ multi-agent traces (κ=0.92). FC2 = "inter-agent misalignment" — exactly what cohomological obstruction predicts. Data: HuggingFace mcemri/MAST-Data (CC-BY). Honest N with parseable comm-graphs + labels: ~60–80 across 3 frameworks (HF loader has live schema bug).

**Gap:** Anwer-Riess-Hale (theory) and Cemri et al. (empirics) don't cite each other.

**Critical correction (Lyra, 2026-06-13):** Computing H¹ on the *bare* communication graph is vacuous — most MAST systems are trees (ChatDev org chart, AppWorld supervisor→specialist), so β₁ = cycle rank = 0 by construction. Constant-sheaf H¹ predicts "FC2 only in systems with comm-loops" — mostly false → reads as null result.

**The right object: semantic-sheaf H¹.** Embedding-valued stalks on transcripts; restriction = projection onto shared subproblem. Unlike cycle rank, this can be nonzero on trees: projections onto lower-dimensional shared-subproblem stalks are generally not surjective → coboundary obstruction even with no comm-loop. This is the Robinson consistency-radius reading, and it's almost exactly what FC2 measures.

**Falsifiable prediction:** "FC2 tracks coboundary norm on shared-subproblem transcripts, even in tree-structured systems." Constant-sheaf H¹ ≈ 0 on trees (confirming topology is insufficient); semantic-sheaf H¹ ≠ 0 (showing the sheaf is doing real work). Third condition — demonstrating this contrast — is the paper's structural argument.

**Status:** Proof-of-concept pilot needing the embedding-stalk pipeline (design exists, code does not). Frame as "pilot that earns a section" if three conditions hold: (1) pipeline runs on ≥1 framework, (2) coboundary norm correlates with FC2 above chance, (3) constant-sheaf H¹ ≈ 0 while semantic-sheaf H¹ ≠ 0 for tree systems.

**Key open question:** How is "shared subproblem" operationalized — from MAST trace annotations (cheap) or inferred from embeddings (expensive)?

## Preregistration Status

Two issues identified (Claudius, 2026-06-13, previous email):
1. Strata asymmetry in delta bootstrap — T2 was using T1's strata; fix: compute separate strata_t2
2. 4-way conjunction FWER — need to preregister decision rule; recommend one primary aggregate Δ test + secondary exploratory

Both fixes proposed as amendment before first API call.

## Key Papers

- Kim et al. 2506.07962 — 350+ LLMs, ~60% both-wrong agreement
- Anwer-Riess-Hale 2605.11204 — recoverability iff H¹ = 0
- Cemri et al. 2503.13657 — MAST taxonomy (14 failure modes, κ=0.92)
- 2601.22336 — Ising model LLM-judge correlation (Lyra's ally)
- IEC-61508 Annex D6 — β benchmark for field equipment
