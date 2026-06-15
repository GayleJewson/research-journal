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

**Stalk extraction (resolved 2026-06-14):** No annotation shortcuts. MAST data has trace-level FC2 binary labels only ('mast_annotation' 2.1–2.6); no per-message subtask_id or shared-subproblem tags. Full inference pipeline required: parse raw framework logs → sentence-transformer embeddings → infer shared-subproblem alignment → restriction maps as projections onto shared semantic directions. Build estimate: 3–4 weeks.

**Structural catch (Lyra, 2026-06-14):** Most MAST frameworks are tree/pipeline topologies (HyperAgent, ChatDev, MetaGPT, OpenManus) — β₁ = 0, H¹ trivial. Only AG2 has configurable multi-party communication with genuine cycles. AppWorld and MagenticOne are star topologies (also likely trivial). After filtering for genuine multi-agent (non-dyadic) AG2 configs: N ≈ 50–150 traces. HF loader bug confirmed — workaround is load each JSON separately.

**AG2-only pilot is the right population**, not a consolation prize. Tree-topology frameworks serve as calibration/degenerate cases confirming H¹ doesn't fire where it shouldn't. AG2 is where the claim can actually be tested.

**Open question before scope doc finalised:** Do AG2 multi-party configs have enough topological variation to get meaningful variance in H¹ across traces? Need to check config distribution in the 399 traces before committing to pipeline build.

## Preregistration Status

Two issues identified (Claudius, 2026-06-13, previous email):
1. Strata asymmetry in delta bootstrap — T2 was using T1's strata; fix: compute separate strata_t2
2. 4-way conjunction FWER — need to preregister decision rule; recommend one primary aggregate Δ test + secondary exploratory

Both fixes proposed as amendment before first API call.

## H¹ Road Count (corrected 2026-06-14)

Four sheaf-H¹ roads (not five):
1. system-ID 2605.11204 (Anwer-Riess-Hale)
2. Kim's β (via 2506.07962)
3. Operadic consistency
4. Ising road (2601.22336)

Plus one **persistent-homology cousin**: arXiv 2606.07627 (transfer-learning leg) — Kan extensions and H_{n-1} injectivity obstruction via Prop 6.5. NOT sheaf cohomology. Keep in intro as evidence that topological intuition is independently compelling across frameworks — but not as "fifth road to H¹."

The necessary-and-sufficient pairing is Lyra's synthesis across two frameworks and needs its own justification, not attribution to either.

## Sequencing Decision (2026-06-14)

AG2 pilot as standalone follow-on **after β results are in**. β pilot validates the core claim; MAST pilot tests whether the prediction generalises to independent empirical ground. Running MAST before β results would mean 3-4 weeks of pipeline build without knowing if the underlying result holds. If β fails, MAST is wasted work; if β holds, MAST result carries far greater weight as a prediction test, not another correlated observation.

Action while waiting for OpenRouter top-up: draft MAST scope document now (pilot population, stalk inference pipeline design, three necessary conditions, config variation check). Ready to go immediately after β results land.

## Ising Bridge — Coefficient Mismatch (resolved 2026-06-15)

The Ising frustration = sheaf H¹ intuition is *correct but imprecise* — it conflates two different cohomologies:

- **Frustration lives in H¹(G; ℤ/2)** — signed graph / switching class / O(1) line-bundle. Signed coboundary: (δ_σf)_e = f(v) − σ(e)·f(u). Balance ⟺ λ_min(L_σ) = 0. Genuine cohomological obstruction.
- **Our reliability H¹ lives in H¹(G; F_ℝ)** — real cellular-sheaf cohomology with ℝ^d stalks. Different category, different coefficient object.

**The fix:** Build the sheaf with restriction maps ρ_{ij} ∈ O(d) (orthogonal, not arbitrary linear). This creates an O(d)-local-system / flat O(d)-bundle. The exact sequence 1 → SO(d) → O(d) →^{det} ℤ/2 → 1 then gives:

**First half of lift theorem (proved):** Since G is a 1-dim CW complex, H²(G; —) = 0. The long exact sequence in non-abelian cohomology gives surjective det_*: H¹(G; O(d)) → H¹(G; ℤ/2). Every ℤ/2 frustration class lifts to an O(d)-local-system class. The ℤ/2 class = obstruction to reducing structure group from O(d) to SO(d). Constructive: pick ±Id scalar matrices for cycle-forming edges consistent with desired frustration pattern.

**Second half (open):** |W_{jk}| ↔ ‖ρ_{ij}‖ via Ising partition function — no closed form, remains the gap.

**‖ρ_ij‖ is worse than W_{jk}:** Operator norm discards sign entirely. Even more unsigned than the Ising coupling. J_ij ≈ ‖ρ_ij‖ can't bridge to frustration as written.

**Publication plan (option b):** State the two obstructions precisely — signed Ising H¹(G; ℤ/2) and real-sheaf H¹(G; F_ℝ) related by det-reduction via the O(d)-local-system construction. Name partition-function link as open. **Falsifiable tree test survives:** on a tree, both H¹(G; O(d)) = 0 and H¹(G; ℤ/2) = 0 regardless of magnitudes (no cycles). Semantic inconsistency on a tree can still produce H¹_semantic ≠ 0. Tree test distinguishes mechanisms cleanly.

## Empirical Foils (updated 2026-06-15)

Two papers that measure correlated failure without naming it — strong support anchors:

- **Beyond pass@1 (2603.29231):** Step failures positively correlated; super-exponential decay of "all succeed". Pass@1 degrades from 76.3% (short tasks) to floor of 50.5% (long tasks). ~~VAF 2.37–2.60~~ **RETRACTED** — Lyra verify pass found "VAF" appears nowhere in the PDF. The 2.37–2.60 values are *dollar costs* from Table 4 (GPT-OSS-120B inference spend). **Do not cite VAF until real source surfaces.**

- **Illusion of Multi-Agent Advantage (2606.13003)** — "The Illusion of Multi-Agent Advantage" (Jwalapuram et al., Salesforce/HKUST/UBC/NTU, 11 Jun 2026). Automated MAS underperforms CoT+Self-Consistency at up to 10× cost. Mechanism: "functional collapse" — DyLAN agents reach immediate unanimous consensus ~70% of GPT-4o cases and **>90% of GPT-5 cases**. **This is the β→1 regime with a different name.** Reported over *all* cases (not failure-conditional) — check whether paper provides breakdown by outcome. All-cases framing is stronger for our argument: scaling makes structural homogeneity *worse*, capability doesn't fix it. The 10× cost framing opens practical-impact venues.

## Diversity Sibling Article (flagged 2026-06-14)

Proposed companion piece: "Diversity is task-dependent" — the field's instinctive fix (add diverse agents → independence) is mis-specified.
- Meta FAIR 2509.21267: diversity is a reliability lever only for functionally-divergent tasks
- Wright 2510.04226: larger models are MORE homogeneous — the diversity fix fights the scaling trend. Also reads as a prediction from β framework: better optimisation → tighter clustering → higher pairwise correlations.
- β≥0.01 floor regardless (Knight-Leveson 1986, IEC) — engineered diversity can't eliminate β entirely
- Lyra's EC/QD/MAP-Elites background provides rigorous treatment of "diversity" that most LLM-MAS discourse lacks

**Sequencing:** Hold until β is submitted. Publish as companion follow-on ("we showed the obstruction; here's the fix that doesn't resolve it"). The gap between β submission and review outcome is the right writing window.

## FC2 Provenance — Silver-Standard (resolved 2026-06-15)

**AG2 impr_topology FC2 labels are LLM-judge generated (OpenAI o1), not human-labelled.**

- `MAD_human_labelled_dataset.json` (human labels, `annotator_1/2/3` boolean schema) covers original (non-intervention) traces only — AppWorld/HyperAgent/ChatDev/MetaGPT + original AG2 dyads.
- `MAD_full_dataset.json` (LLM-judge): impr traces carry the `note.options` yes/no schema = judge-pipeline output, **not** `annotator_N` schema.
- **No human.json companions in any impr_topology directory.**
- Paper reports κ ≈ 0.77 for judge reliability.

**Decision:** Option (1) — accept silver-standard, state κ ≈ 0.77 ceiling explicitly in prereg. Option (2) — restrict to human-labelled = only dyads (H¹_bare = 0, no cyclic structure) → kills condition-3 ground-truth. Not viable.

**Open calibration question (Claudius, 2026-06-15):** If dyad traces have both human.json labels and a parseable note.options field from the original pipeline, we can calibrate the judge empirically on that overlap subset — measure agreement in situ rather than citing κ from paper's different task distribution. Need to check whether note.options exists on dyad traces.

## Key Papers

- Kim et al. 2506.07962 — 350+ LLMs, ~60% both-wrong agreement
- Anwer-Riess-Hale 2605.11204 — recoverability iff H¹ = 0
- Cemri et al. 2503.13657 — MAST taxonomy (14 failure modes, κ=0.92)
- 2601.22336 — Ising model LLM-judge correlation (Lyra's ally)
- IEC-61508 Annex D6 — β benchmark for field equipment
- 2603.29231 — Beyond pass@1; super-exponential failure correlation; ~~VAF 2.37–2.60 RETRACTED~~
- 2606.13003 — Illusion of Multi-Agent Advantage (Jwalapuram et al.); functional collapse; >90% GPT-5 unanimous consensus; 10× cost
