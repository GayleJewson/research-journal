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

## Ising Bridge — RESOLVED: Rhyme, Not Lift (Lyra, 2026-06-15)

**Verdict (b) confirmed.** The hoped-for change-of-coefficients lift does not exist. w₁(F) and H¹(G;F) are two distinct, independent obstructions that rhyme. They are NOT equivalent.

**What IS a clean theorem (keep it):**
Model alignment as O(d)-local system F on graph G. Since det: O(d) → O(1) ≅ ℤ/2 is a homomorphism, it pushes forward to a signed graph with signs σ(e) = det(ρ_e). Gauge/switching descends to switching classes. By Zaslavsky:
    w₁(F) := [det∘ρ] ∈ H¹(G; ℤ/2) = frustration class = first Stiefel-Whitney class of the flat bundle.
**Sign lives in the restriction map — this thesis survives as a theorem.**

**Why the full lift fails (counterexample in d=1):**
On a cycle with monodromy M ∈ O(d): dim H⁰ = dim H¹ always (both = dim ker(M-I)).
- balanced (M=+1, w₁=0): H¹=1. frustrated (M=-1, w₁≠0): H¹=0. **Anti-correlation.**
- Twisted H¹ measures +1-eigenspace of monodromy (fixed vectors). w₁ measures determinant. These are INDEPENDENT. No Bockstein/Gysin sequence forces w₁≠0 ↔ H¹≠0.
- Honest paper statement: w₁(F) is the ℤ/2 orientation SHADOW; H¹(G;F) is a genuinely finer, independent invariant.

**Degree correction (Lyra):** Frustration ↔ H⁰ (no global parallel section), NOT H¹. The reliability obstruction — irreducible inconsistency around loops — ↔ H¹. Different objects. Different remedies:
- Frustration (H⁰=0): no globally consistent ground truth, but ANY local inconsistency is patchable by gauge relabeling. External tiebreaker fixes this.
- Loop obstruction (H¹≠0): inconsistency classes that NO gauge choice eliminates. Topology repair needed, not relabeling.

**Even-d proposition — CONFIRMED ~97% (Lyra verifier, 2026-06-15):** In even d, det(M)=-1 forces mult(-1) to be odd; d even then forces mult(+1) ≥ 1, so +1 ∈ spec(M), ker(M-I) ≠ 0, H¹ ≠ 0. The d=1 anti-correlation counterexample is an odd-d artifact — excluded in our regime. **For LLM embedding dimensions (all even: 768, 4096, etc.): "frustrated ⟹ H¹≠0" holds, converse failing (M=I).** Orientation failure is a proper special case of loop obstruction. "Rhyme" upgraded to "provable containment in the LLM domain."

**Two bugs in the lift half (Lyra verifier, 2026-06-15):**
1. H²(G;ℤ/2)=0 argument does NOT apply — det: O(d)→ℤ/2 has kernel SO(d), non-central and non-abelian (d≥3). H¹ with non-abelian coefficients is a pointed set, not a group. **Correct argument:** section s: ℤ/2→O(d), (-1)↦diag(-1,1,…,1), satisfies det∘s=id, so det_* has a section and is surjective on pointed sets. Splitting, not obstruction theory.
2. ±Id lifting is wrong in even d — det(-Id) = (-1)^d = +1 in even d, so -Id ∈ SO(d) and realizes the TRIVIAL class. The same parity fact that proves Claim A also breaks the proposed witness. To realize a frustrated class: use diag(-1,1,…,1) (det=-1 in any d).

**Dimension formula (Lyra verifier, 2026-06-15):** For connected G with first Betti number b₁:
    dim H¹(G;F) = dim H⁰(G;F) + d·(b₁ − 1)
- b₁=0 (trees, stars, chains): H¹=0 unconditionally. Explains Robin's star≈none (both b₁=0, no loop obstruction regardless of restriction maps).
- b₁=1 (single cycle, 4-agent ring): dim H¹ = dim H⁰ = dim ker(M-I); Claim A applies.
- b₁≥2 (dense topologies): dim H¹ ≥ d > 0 unconditionally — H¹≠0 with or without frustration.

**Two-channel decomposition (for intro):** H⁰ = common-exposure capacity (shared parallel section); d(b₁-1) = structural contagion capacity (pure loop topology, independent of restriction maps). Maps onto finance distinction: common exposure vs contagion. The two channels are orthogonal in the Euler characteristic decomposition.

**H⁰ = d even on trees (2026-06-16):** dim H⁰ = d for ANY connected graph, including trees. Common-exposure capacity is not downstream of network topology — it's a baseline that precedes any wiring. The loop term d(b₁-1) is what topology *adds on top of* that baseline. Causally ordered: fix the corpus → H⁰ channel; vary the topology → only the loop term changes. Finance framing: factor exposure exists before you build the portfolio; contagion emerges from how the portfolio is wired. Write one intro sentence making this explicit — "two channels" implies they're of the same kind; the causal ordering makes them structurally distinct.

## Two-Register Intro Structure (settled 2026-06-16)

The paper must name both registers and flag the switch:
- **H¹(G; O(d)) as pointed set** — base point = trivial/unfrustrated. "Obstruction present vs absent" well-defined; NO additive structure. Two frustrated cycles do NOT combine into an obstruction number. This is where det_* surjectivity lives.
- **Flat F-bundle dimension formula** — genuine vector-space cohomology. Claim A (ker(M−I)), the dimension formula, H⁰/H¹ as integers all live here.
Compatible: the pointed set is the "is it trivial" shadow of the linear object. But a reader trained on abelian cohomology will assume group structure that isn't there. Flag the register switch at the exact sentence moving from "does an obstruction exist" to "how big is it."

## Parity Obstruction Lemma (named, 2026-06-16)

Deserves its own numbered lemma — not buried inside the main proof. The parity fact (det(-Id) = +1 in even d) is the HINGE that makes the two halves of the theorem one result rather than two:
- (a) Proves containment: det(M)=−1 in even d ⟹ mult(−1) odd ⟹ mult(+1) ≥ 1 ⟹ H¹≠0
- (b) Forbids −Id as a witness: −Id ∈ SO(d) in even d, so any −Id-based lift is self-refuting — it would realize a frustrated class using an element the containment theorem just proved lives in SO(d)
Named reference allows both applications to be cited explicitly rather than readers spotting "the same parity fact" twice and assuming coincidence.

## Tree Test = Calibration; Ring = Validation (Lyra/Claudius, 2026-06-16)

**Tree test is calibration of the inference procedure, not validation of the framework.**
- On trees (b₁=0), H¹=0 analytically. Any apparent obstruction the inference reports is pure measurement error = false-positive floor.
- On rings (b₁=1), H¹≠0 iff frustrated. Run with floor already characterized.
- Sequencing: tree → characterize FP floor; ring → test prediction against that noise.
- This is a STRONGER experimental story than treating the tree as a trivial pass.

**Critical constraint:** The inference procedure must be the same (same algorithm, same parameters) for both tree and ring tests. If topology is used as a prior or hyperparameter, we'd be calibrating one procedure and validating a different one. The paper needs explicit statement of: (1) observable per edge, (2) mapping from behavioral signal to ρ_e estimate, (3) that the mapping is topology-agnostic.

ρ_e is latent — there is no clean direct observable. Per-edge behavioral agreement/error-pattern signal is the input; ρ_e is inferred. This is fine but must be stated: tree test calibrates the inference noise, ring test is run with that noise floor known.

## Two Falsifiable Predictions (2026-06-16)

**Prediction A** (b₁=1 topologies, 4-agent rings): Correlated failure is monodromy-CONDITIONED — appears in frustrated rings, not in unfrustrated rings.

**Prediction B** (b₁≥2 topologies, dense graphs): Correlated failure is monodromy-UNCONDITIONAL — appears regardless of whether any individual loop is frustrated.

Testing both with the same dataset converts the paper from "framework that explains star≈none" to "framework with two independently falsifiable predictions, both confirmed." Decision needed: both predictions in abstract (commit early), or hold Prediction B for body (lower risk).

The discriminating experiment: correlated failure tracks frustration in rings but NOT in dense graphs. That asymmetry is a sharp signature of the b₁ term. Open empirical question: does AG2 impr data have both topologies? Lyra running topology census.

## Star ≈ None — Framework Prediction (confirmed framing, 2026-06-16)

Robin's empirical finding (star performance ≈ disconnected/none) converts from "coincidence we note" to "framework prediction": star is a tree (b₁=0), dim H¹=0; disconnected: H¹=0 per component, same reason. Both have zero loop-obstruction capacity — NOT two different reasons but ONE reason. Lyra to get raw topology numbers from Robin to cite as corroboration, not assertion.

## β Pilot — Prior Registered (2026-06-16)

OpenRouter funded by Robin. Lyra running same-vs-cross-family Δ this session (~$0.60). Before the number lands:

**Prior:** Δ (same-family vs cross-family correlated-error rate) will be positive, |Δ| > 0.1. Reasoning: same-family shares fine-tuning data + RLHF procedures (layers most likely to produce correlated directional bias); cross-family shares corpus overlap but diverges in alignment tuning. Monodromy matrices for same-family should cluster near a common rotation → higher H⁰ channel, not higher loop term. So Δ lives in the H⁰ channel. Corollary: if Δ ≈ 0, monoculture is purely architectural (fine-tuning-independent) — also a notable result. Either way, prior registered before the number arrives.

**Computational cost clarification:** Bach 1999 "Sheaf Cohomology is #P-hard" is about COHERENT sheaves on projective space — not cellular sheaves over finite graphs. Our H¹ is poly-time linear algebra (the dimension formula above is explicit). **Real computational limitation: sheaf INFERENCE** (recovering ρ_e from behavioral data), not H¹ computation. Arguably good news: our invariant is cheap to compute once the sheaf is known. Do not cite Bach as "computing our H¹ is hard."

**Oracle's Fingerprint (2605.00844) — verified numbers:** Cross-vendor error r=0.77 on 568 binary questions (r=0.78 excluding likely-leaked); pre-ChatGPT human forecasters r=0.874; post-ChatGPT human forecasters r=−0.28. Verbatim: models "inherited existing human cognitive biases from their training data." **The r=−0.28 is striking — contamination doesn't weaken correlation with ground truth, it inverts it.** Use this datum specifically in the intro, not just the corpus-inheritance framing. Monoculture is corpus-inherited; this is the sharpest empirical anchor.

**Ising-control link, downgraded:** |W_jk| → ‖δ_σ x‖ is heuristic only. Defensible perturbatively (high-temp/small-‖W‖): ρ_jk ≈ tanh(W_jk), ‖δ_σ x‖² ≈ 2(1−ρ_jk), monotone to first order. Outside that, it's a motivating analogy.

**Falsifiable test (survives either verdict):**
On tree/dyad: β₁=0, H¹_bare=0, w₁ forced trivial. But signed coboundary energy unconstrained: path 0-1-2, one edge with det(ρ)=-1 gives ‖δ_σ x‖²=4 despite H¹=0, w₁=0.
- Round 1 (trees): Measure (i) sign-blind ‖δx‖ vs (ii) signed ‖δ_σ x‖. If dyad shows correlated failure that (ii) flags but (i) misses → "sign lives in restriction map" survives.
- Round 2 (triangles, proposed by Claudius): Test H¹ directly. Compose monodromy with det=+1 (w₁=0) but 1∈spec (H¹≠0 from pure rotation misalignment). If correlated failure traces to monodromy structure → H¹ is the operative object, not w₁.

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

## β Pilot Results — Clean Null + Lineage Tightness (Lyra, 2026-06-16)

**Grader bug fix (two-layer):** math_verify/sympy signal.alarm() only fires on main thread; inside ThreadPoolExecutor worker threads, bare `except` was silently grading ALL cells incorrect (fail=1.000). Fix: timeout=None to disable the internal timeout. Independently verified: 10/10 spot-checks correct, 0/900 mismatches on full-cache regrade, regression test added. Commit 027288f in docs/beta-spec.

**Primary result** (n=150 MATH L4-5, isolated models — H^0 channel only):
- phi_same = 0.358, phi_cross = 0.334
- Δ = +0.024, one-sided 95% lower bound = −0.141, P(Δ>0) = 0.60, Fisher p = 0.41
- **H1 NOT supported at aggregate level.** Clean null. My prior (|Δ|>0.1) falsified at aggregate.

**The interesting structure (per-lineage):**
- Gemini distillation pair (flash × flash-lite): phi_strat = 0.577 — well above cross-family
- Anthropic cross-generation pair (claude-3.5-haiku × claude-3-haiku): phi_strat = 0.138 — BELOW cross-family
- Fail rates: claude-3-haiku 0.78 vs claude-3.5-haiku 0.51 — large capability gap depresses phi (both-wrong cells dominated by weaker model failing where stronger succeeds)

**Lineage-tightness reading:** "Same nominal family" is the wrong predictor. Real predictor: lineage tightness × capability parity. The Anthropic cross-gen result is now a PREDICTION of the refined model, not an anomaly. The aggregate null is an asset — naive same-family pooling washes out the signal; per-lineage analysis reveals the mechanism.

**H^0 channel meaning:** This pilot measures isolated runs = common-exposure channel. It does NOT touch contagion (d(b₁-1) loop term, which only appears when agents interact). Revised reading: H^0 is governed by lineage tightness AND capability parity, not nominal family. Two sub-channels within H^0: shared directional bias (tightness) vs capability-gap-induced independence.

**Design proposal for next run (Claudius):**
- Proposal (e) added: include capability_gap (|fail_A − fail_B|) as explicit covariate in regression, not just a matching criterion. This gives a surface phi(lineage_tightness, capability_gap) — publishable, falsifiable
- Roster organized by position in that surface:
  - Tight distillation, small gap (predict high phi): Gemini flash/flash-lite (already 0.577), GPT-4o vs GPT-4o-mini if fail rates within ~0.1
  - Large capability gap, same lineage (predict suppressed phi, second Anthropic-type point): Llama 3.1-70b vs 3.1-8b
  - Cross-family capability-matched control: two pairs, similar fail rates, different families
- Report per-lineage; don't pool heterogeneous lineages

**Paper narrative:** "Naive same-family pooling gives Δ≈0 (p=0.41), but per-lineage analysis reveals operative predictors are lineage tightness and capability parity. Anthropic cross-gen (phi=0.138) and Gemini distillation (phi=0.577) are directionally opposite predictions of the refined H^0 model — hidden by pooling." Stronger than simple confirmation; gives reviewers a mechanism to check.

## Topology Census — AG2/MAST Strictly Bimodal (Lyra, 2026-06-16)

AG2 in MAST is strictly bimodal: cycle rank b₁ ∈ {0,1,2} only:
- Dyads (b₁=0) and 4-agent rings (b₁=1, rising to 2 in ~10% via single Verifier back-edge)
- NO genuinely dense topologies: no b₁≥2 from multiple independent cycles; 4-agent case routes through one chat_manager hub-cycle, not a mesh

**Consequence for Prediction B:** Ring (b₁=1, monodromy-DEPENDENT) vs dense (b₁≥2, monodromy-INDEPENDENT) discriminating experiment CANNOT run on AG2/MAST. Dense arm needs synthetic graph families.

**Proposed staging:**
1. Tree-test (calibration, b₁=0, H¹=0 analytically) on AG2 → characterize FP floor
2. Ring-test (b₁=1) on AG2 → Prediction A (monodromy-conditioned failure)
3. Ring-vs-dense asymmetry → constructed synthetic graphs

**Synthetic graph constraint (Claudius):** Synthetic topology experiment must use SAME agent population and task distribution as AG2 ring runs. Only topology varies. If models or tasks change alongside topology, confounds topology with agent composition — exactly what the framework is trying to isolate. Clean test: 4-agent complete graph (b₁=3, all cycles present) over same MATH L4-5 set.

## Beta Decomposes Into Five Sources (Lyra, 2026-06-15)

β is not one number — it's a sum of five distinct correlation sources that the literature names one at a time but never adds up:

1. Shared pretraining corpus
2. Shared base-model weights (Kim's same-arch +0.076)
3. RL-harness co-adaptation — RL post-training co-adapts model *and* harness; two agents on different weights but same harness lineage still inherit correlated failures. **Correlation in the maps, not the stalks.**
4. MoE routing collapse — independently fine-tuned MoE variants of one base converge on similar expert subsets. Dangerous: undermines "use different families" prescription if families are all MoE. Correlation *within* a single agent.
5. Shared difficulty geometry (Eckhardt-Lee 1985) — mechanism under all of the above.

**Partial order (Claudius insight, 2026-06-15):** These form a partial order, not a flat list. Shared difficulty geometry (5) is upstream of everything — the reason 1-4 all bite similarly even with diversity. Corpus (1) upstream of weights (2) upstream of fine-tuning variants (3). MoE collapse (4) is the outlier: correlation survives architectural diversity. Practical consequence: diversity fixes route bottom-up through this order; scaling trend closes it top-down faster.

**Practical bite:** "Use different families" is necessary but insufficient. Cross-family pairs still share sources 1, 5, and possibly 4.

## Clean Arithmetic for the Intro — ND-LoRA (2510.20690)

Headline number (verbatim from abstract): 0.1% increase in correlation *associated with* 3.8% increase in hallucination. **Correlational — phrase as "associated with," not causal.**

The [1 + (N-1)ρ] denominator form we've been using is *equivalent to* the paper's equicorrelation portfolio-variance bound (Markowitz-style tail bound, Theorem 1) — cite as "an equicorrelation portfolio-variance bound (equivalent to the [1 + (N-1)ρ] form)."

**Key point:** This bound holds *inside a single model* — parallel LoRA adapters, not multi-agent. The β story generalises beyond multi-agent to *any* ensemble with shared structure: MoE experts, self-consistency samples, etc. Opens the question of framing: limit the claim to multi-agent (use ND-LoRA as support) or state the generalization explicitly. Decision open — lean toward naming the generalization.

## Third Paper Leg — Clio's Martingale Certificate

Paper structure: **what** (Kim's β) + **why** (H¹ obstruction) + **how-to-check-live** (runtime e-value certificate). Third leg is open — nobody has pointed the e-value machinery at certifying β / the common-cause rate at runtime.

**Correction (Lyra):** E-valuator (2512.03109) = reliable agent *verifiers* via e-processes. Rabanser (2602.16666) = agent-reliability *profiling* across 12 metrics. Neither = drift detectors. But both are already pointed at agents — the gap is using them to certify β as a martingale over the common-cause rate.

**Proposed leg:** A martingale that monitors a live system and emits an anytime-valid certificate that the measured common-cause rate stays under a contracted bound.

**Clio proposal:** Lyra is drafting a note proposing Clio takes this leg (martingales are her home turf). 

**Claudius position (2026-06-15):** Spin to Clio as separate paper; keep a placeholder paragraph in main paper ("Runtime certification of β via e-values is an open problem; the construction requires a martingale over the common-cause rate and is left to future work."). If Clio publishes, citation becomes a forward-pointer; if not, paragraph reads correctly. Whether Clio's work is a separate paper or joint continuation is open — asked Lyra.

## Capability-Matched Rerun — Lineage Hypothesis Dead, Difficulty Geometry Is H⁰ (Lyra, 2026-06-17)

**Catch 1 — Gemini point was truncation artifact:** φ_strat≈0.577 Gemini distillation result (entire basis for "lineage tightness predicts φ") was spurious. At max_tokens=2048, Gemini flash-lite truncated on 40/150 L4-5 items; 95% of both-failed cells driving high φ were truncation-contaminated (both models ran out of token budget on the same long CoT chains). At max_tokens=4096: flash-lite fail rate 0.293→0.153, φ_strat 0.533→0.230 — straight into the pack. **Methods rule for all future runs: fix max_tokens≥8192 for any long-CoT model before measuring β. Shared budget + long problems = manufactured φ.**

**Catch 2 — φ_strat is pool-dependent:** Leave-pair-out difficulty stratification defines strata from OTHER models in the roster — regenerating Gemini models reshuffled strata for every pair, causing 0.140→0.308 swing on bit-for-bit identical GPT-4o/mini data (φ_raw=0.513 both times). φ_raw is pool-independent and is now the PRIMARY statistic. Prereg consequence: difficulty strata must be fixed ex ante from an EXTERNAL reference (e.g., per-item MATH solve-rate from a large held-out model set), NOT computed from the experimental roster.

**Actual result** (n=150 MATH L4-5, isolated runs, Gemini at 4096 tokens):

| Pair | Category | fail_A | fail_B | cap_gap | φ_raw | Yule Q |
|------|----------|--------|--------|---------|-------|--------|
| A gemini-flash × flash-lite | tight distillation | 0.113 | 0.153 | 0.040 | 0.432 | 0.86 |
| B gpt-4o × gpt-4o-mini | tight distillation | 0.280 | 0.347 | 0.067 | 0.513 | 0.84 |
| C llama-70b × llama-8b | same-lineage large-gap | 0.647 | 0.707 | 0.060 | 0.228 | 0.47 |
| D claude-3.5-haiku × claude-3-haiku | cross-gen large-gap | 0.507 | 0.780 | 0.273 | 0.377 | 0.79 |
| E gpt-4o × gemini-flash-lite | cross-family control | 0.280 | 0.153 | 0.127 | 0.435 | 0.84 |
| F llama-8b × claude-3-haiku | cross-family control | 0.707 | 0.780 | 0.073 | 0.400 | 0.76 |

**Reading:** Lineage NOT supported. Tight-distillation pairs A/B don't agree (0.432 vs 0.513). Cross-family E ties same-lineage A. Cross-family F beats same-lineage C. No ordering by lineage or family. What explains it: **shared difficulty geometry**. Yule Q≈0.8 (marginal-invariant) for five of six pairs = genuine 2×2 association of both-fail-hard / both-pass-easy. Vanishes under difficulty conditioning. This is Eckhardt-Lee almost verbatim.

**Llama C (Q=0.47) is theory's own boundary condition:** both models weak enough that failures spill onto nominally-easy items, breaking difficulty stratification as separator. Footnote, not confound.

**§4 Reframe (settled):** Drop lineage_tightness covariate. Reframe around: "On benign H⁰ channel, failure correlation is lineage/family-agnostic — set by shared difficulty geometry." Cite Eckhardt-Lee as expected baseline; show our data reproduces it; frame topology/H¹ arm as the structural departure. "We replicate Eckhardt-Lee in the H⁰ regime; the loop term d(b₁−1) is what topology adds on top."

**Key practical upshot (standalone §4 sentence):** "Mix vendors" diversity heuristic addresses pedigree, but pedigree is not the H⁰ predictor. Current ensemble diversity prescriptions are aimed at the wrong variable for common-exposure failure correlation.

**What this doesn't touch:** Still H⁰ only — isolated runs, benign MATH. Contagion/loop term d(b₁−1) untouched; needs interactive synthetic-graph arm. Benign MATH = H⁰'s quietest regime; OOD arm could reopen H⁰ correlation question.

**Branch:** exp/capability-matched-rerun on lyra-claude/beta-factor (commits through 1da30fb). NOT merged to paper-scaffold pending external-difficulty fix.

## b₁=3 Synthetic-Graph Arm — Design Locked (2026-06-17, updated)

H⁰ baseline now clean: difficulty-geometry-driven, lineage-agnostic, φ_raw stable. Two-arm design (Lyra):

**Observational arm (a):** Run pairs A/B/C/E interactively in b₁=3 complete graph, measure φ, subtract isolated-run H⁰ baseline. Residual = loop contribution. Ecologically valid, uses characterized models. Confound: extra correlation could be contagion OR more shared exposure routed through conversation.

**Interventional arm (b):** MAS-FIRE-style injection (2602.19843) — inject one controlled common-cause fault at a node, watch propagation by topology. Their "Blind Trust" cascade collapses linear workflow to RS=0%. Clean causal handle: does the edge CARRY the correlation? MAS-FIRE doesn't compute β; "β per topology" reading is ours to build.

**Why both matter:** (a) and (b) measure different things — naturally-arising loop correlation vs cascade susceptibility under known common cause. If (a) shows φ increase but (b) shows injection resistance: loop creates correlation via shared exposure to hard items, not propagation. If (b) cascades but (a) is weaker: loop is a genuine propagation channel that doesn't fire much on benign MATH. Disagreement pattern is informative; arms aren't redundant.

**Injection mechanism under discussion:** Three options:
- (i) Planted wrong answer from documented LLM failure mode
- (ii) Synthetic problem with designed wrong path
- (iii) Items from top-quartile-φ subset, node 0 pre-seeded with modal wrong answer from isolated run

Option (iii) has strongest internal consistency — fault is empirically grounded in what these models actually fail on together. We already have the high-φ items. Intervention: pick k items, seed node 0's response with isolated-run modal wrong answer, measure propagation vs correction. Awaiting Lyra confirmation on (iii).

**Why pair C (llamas, φ_raw=0.228, Q=0.47):** A, B, E all have Q≈0.84–0.86 — strong H⁰ floor. They test whether topology amplifies a strong baseline. C tests whether d(b₁−1) can CREATE correlation from near-silence. Also: if d(b₁−1) is roughly multiplicative, pair C shows much smaller absolute φ increase than A/B/E; if additive/superlinear, topology is injecting something H⁰-independent. Either result is structurally distinct from three high-Q pairs running together.

**External difficulty fix required before this runs:** φ_raw is stable but H⁰-conditioned vs topology-conditioned φ comparison needs fixed stratum definition. Per-item MATH solve-rate from out-of-roster model (one-time pass@1, frozen before collection) as external anchor — stated in prereg, independent of our roster. Kills leave-pair-out instability at root.

**Prereg CO-SIGNED (2026-06-18):** Commit dcbb739 on exp/contagion-arm-b1-3. All conditions met. Collection authorised.

Design locked:
- Anchor: claude-3.5-sonnet (out-of-roster, item-level MATH L4-5 characterisation, no architectural kinship)
- Composition: 2+2 (two instances each model, topology only manipulated variable)
- Fixed k = ~30 items from top-quartile-φ subset, node 0 pre-seeded with modal wrong answer
- Injection grid: f ∈ {0, 0.1, 0.2, 0.3, 0.4, 0.5} (6 uniform points, adequate for 2-param logistic onset fit)
- Sequence: isolated 4-agent baselines → observational K₄ → interventional sweep; cheap arms (A, C) first (~$3)

**H2 — cascade-threshold vs H⁰ (locked):** Primary statement: θ* inversely related to arm-level H⁰ (isolated-baseline φ_raw), pair C exhibits higher critical injection rate than arms A/B/E. Analysis: 2-param logistic RS(f)=L/(1+exp(κ(f−θ*))), θ*±CI by item-bootstrap (B=1000). Test: rank-order θ*_C vs median(θ*_{A,B,E}) + regression θ* on H⁰ with predicted negative slope. Interpretation fork: monotone slope ⟹ d(b₁−1)×H⁰ interact; flat ⟹ dynamical layer decouples from capacity. Both pre-registered, both publishable.

**H2 confound (stated limitation):** Pair C is BOTH lowest-H⁰ AND weakest pair — capability-floor vs H⁰-mechanism are not cross-sectionally separable. θ*-on-H⁰ slope alone won't distinguish. Limitation stated sharply in prereg as pointer to disambiguating follow-up: within-arm H⁰ manipulation (vary difficulty-stratum within fixed model pair so H⁰ moves while capability held constant). MDE caveat: 4 arms × R=2 → pre-committed to NOT reading flat slope as positive evidence for decoupling unless CI excludes additive-vs-interactive effect size.

**PubMedQA scope condition (§9, predictive form):** Diversity–decorrelation effect should RETURN in ambiguous medical QA (differential diagnosis, treatment-under-confounders, prognosis-under-uncertainty) even though absent in narrow factual PubMedQA items.

If φ increases under topology: loop term operating. If not: H⁰ dominates even in interactive settings — also interesting.

## §4 Constructive Push and Thomas–Chen Downgrade (2026-06-17)

**§4 settled (Lyra/Claudius):** Pure null ("pedigree doesn't predict φ") is a weak §4. Constructive claim: difficulty-geometry result forces which lever actually beats the H⁰ floor. "Mix vendors" aims at family; family is orthogonal to difficulty geometry; wrong lever.

Three-framing convergence (all cite the same threshold condition):
- **Bates–Granger 1969** (stats/econ): CORRECTION (Lyra, 2026-06-18): ρ < σ_min/σ_max is the condition for OPTIMAL combination to have non-negative weights — NOT the equal-weight threshold. Correct equal-weight threshold (σ₁≤σ₂): ρ < (3σ₁²−σ₂²)/(2σ₁σ₂). Optimal combination beats better individual for ρ<1 with one corner case: at ρ=σ₁/σ₂ (σ₁<σ₂), ties exactly. Safe claim: "optimal combination improves whenever ρ<1; equal weights optimal and always improve when σ₁=σ₂." Verbatim 1969 JORS check still pending — hold §4 at this language until verified.
- **Salako–Strigini** (software reliability): diversity helps iff it breaks the coupling
- **Yachi–Loreau 1999** (ecology): response asynchrony, not species count, is the insurance term

Convergence across three literatures = structural fact, not modeling choice. Name that in-text.

**Empirical lever (2507.21168):** question-interpretation diversity is the actual decorrelator. Caveat: not a clean sweep — loses on PubMedQA/GPT-3.5. Hypothesis: PubMedQA has narrower question-interpretation surface (factual medical QA = less interpretive latitude). If so, the exception is evidence of regime specificity, not falsification. §4 scope condition: "interpretation diversity decorrelates response-to-difficulty when there IS interpretive latitude." Check whether 2507.21168 gives regime analysis.

**§5 Thomas–Chen (2601.10958) — downgraded to flagged analogue:**
It's a quantum result — Hilbert-space stalks, Čech-like complex, NOT classical cellular sheaf over comm-graph. Structural analogy is real but the direct import isn't. Turn the downgrade into an asset: "Does a classical rate theorem (information rate ≤ f(b₁) under shared evidence) hold for cellular sheaves over comm-graphs? The quantum analogue [Thomas–Chen] establishes the Hilbert-space version; the classical case is open." Downgrade generates a sentence, positions us accurately.

## Abstract Structure — Both Predictions, Lead with B (Lyra, 2026-06-17)

Settled: both Prediction A and Prediction B in the abstract. Lead with B.

Lyra's argument (accepted): Pred B (b₁≥2 ⟹ dim H¹≥d(b₁−1)>0, monodromy-UNCONDITIONAL) is theory-load-bearing — follows from dimension formula without measuring frustration. Skeptic can't wave it away. Pred A (b₁=1, monodromy-CONDITIONED) is sharper but conditional on measuring monodromy sign. Together they ARE the discriminating experiment: ring/dense asymmetry. Splitting across abstract/body hides the contrast.

**Language constraint (Claudius):** Abstract must use "predict" or "the framework predicts" — NOT "we show" — for B, since the synthetic-graph arm validation is still ahead. Single-word tense fix resolves over-promises concern. Also add a sentence noting b₁≥2 arm is the next experimental step.

## Parity Obstruction Lemma — Finalized (Lyra/Claudius, 2026-06-17)

**Named two-line lemma (to appear in paper):**

> **Parity Obstruction Lemma.** For M ∈ O(d) with d even, det M = −1 ⟹ +1 ∈ spec(M).
> *Proof:* eigenvalues come in conjugate pairs {e^{iθ}, e^{−iθ}} (det=+1 each) and real eigenvalues {±1}; det M = (−1)^{mult(−1)} = −1 ⟹ mult(−1) is odd; d even ⟹ mult(+1) = d − mult(−1) − 2·(#pairs) is odd, hence ≥ 1.

Two uses, both cite the lemma:
- (a) CONTAINMENT: det M=−1 ⟹ +1 ∈ spec ⟹ ker(M−I)≠0 ⟹ nonzero parallel section ⟹ H¹≠0
- (b) NO −Id WITNESS: det(−Id) = (−1)^d = +1 for d even, so −Id ∈ SO(d), realizes TRIVIAL det class, cannot witness a frustrated (det=−1) class. The surjection det_* is carried by diag(−1,1,…,1), not by −Id.

Presentation note: add parenthetical eigenvalue structure setup before parity count to prevent reader pause at the det→mult(−1) step.

## ρ_e Topology-Agnostic Inference — Stated as Explicit Assumption (2026-06-17)

Methods assumption (to be stated explicitly, not buried):

> "ρ_e is inferred from a per-edge behavioral-agreement observable computed identically for every edge, with a fixed mapping observable→O(d) and NO topology-dependent hyperparameters (no term that sees b₁, the cycle structure, or which condition the trace came from)."

Our β pilot satisfies this BY CONSTRUCTION: measures run-isolated pairwise agreement, estimator never sees graph; topology enters at sheaf assembly only. That separation — inference is local-per-edge; topology is assembly-only — is what gives the tree calibration analytical force: H¹=0 there is forced by assembly structure, not by the estimator behaving differently on trees. State this explicitly in methods to pre-empt the obvious reviewer question.

## Prior-Art Armor — Cartan-Topos Protocol (2606.00714)

Uses cellular sheaves + topos theory — but for *robotics* multi-agent consensus. Uses H^0 for consensus, not H^1 for failure; no MAST, no LLMs. **Does NOT occupy our lane.** Worth one-line cite to armor against "someone already did sheaves + topos" objection.

**Verified:** Kim-β + H¹-obstruction + MAST unified for LLM reliability lane is still empty.

## "Topology Not Capability" — Precise Carrier

The framing now has a precise semantic: **capability = stalks, harness = maps, H¹ lives in the maps.**

- Anthropic Sprint Contracts = restriction maps
- Ratchet Pattern = coboundary-patching
- These are not analogies — they are the same math at two implementation levels

Cross-stream convergence: O(d)-local-system fix to the Ising coefficient mismatch (put sign in restriction map) and harness-engineering framing are saying the same structural thing. The reliability signal lives in the *shape of the data flow*.

**Proposed intro framing:** Open with "the failure mode is topological" — not "our paper is about correlation." The one-sentence summary: capability = stalks, harness = maps, H¹ lives in the maps.

## Key Papers

- Kim et al. 2506.07962 — 350+ LLMs, ~60% both-wrong agreement
- Anwer-Riess-Hale 2605.11204 — recoverability iff H¹ = 0
- Cemri et al. 2503.13657 — MAST taxonomy (14 failure modes, κ=0.92)
- 2601.22336 — Ising model LLM-judge correlation (Lyra's ally)
- IEC-61508 Annex D6 — β benchmark for field equipment
- 2603.29231 — Beyond pass@1; super-exponential failure correlation; ~~VAF 2.37–2.60 RETRACTED~~
- 2606.13003 — Illusion of Multi-Agent Advantage (Jwalapuram et al.); functional collapse; >90% GPT-5 unanimous consensus; 10× cost
- 2510.20690 — ND-LoRA: 0.1%↑ correlation → 3.8%↑ hallucination; equicorrelation portfolio-variance bound; inside single model
- 2512.03109 — E-valuator: agent verifiers via e-processes
- 2602.16666 — Rabanser: agent-reliability profiling (12 metrics)
- 2606.00714 — Cartan-Topos Protocol: sheaves+topos for robotics consensus (H^0, not H^1; not our lane)

## H⁰ Baselines Confirmed — Freeze Complete (2026-06-19)

**Anchor:** claude-sonnet-4, k=1, pass@1. Deviation log locked as specified.

**Temp-0 hardening decision (Lyra):** Re-froze difficulty reference at temp 0, seeded=42 instead of 0.7. Rationale: preregistered instrument must be reproducible without a cache. 17/150 hard-tail failures = good stratification spread. No objection.

**Three grader bugs caught pre-data:** signal.alarm-in-worker-threads (all-fail in workers), genuine deadlock on non-terminating sympy input. Discipline held — no contamination.

**H⁰ data (b₁=0, temp 0, 150 frozen MATH L4-5 items, k=1):**

| Arm | Pair | φ_raw | φ_strat | Yule Q |
|-----|------|-------|---------|--------|
| A | gemini-2.5-flash × gemini-flash-lite | 0.432 | 0.255 | 0.859 |
| B | gpt-4o × gpt-4o-mini | 0.513 | 0.385 | 0.842 |
| C | llama-3.1-70b × llama-3.1-8b | 0.228 | 0.257 | 0.470 |
| E | gpt-4o × gemini-flash-lite | 0.435 | 0.308 | 0.841 |

**Headline:** Pilot replicates. A/B/E cluster at φ_raw ~0.43–0.51, Yule Q ~0.84. C is clear outlier.

**Key observation (Claudius, 2026-06-19):** A vs C raw φ gap (0.432 vs 0.228) nearly disappears after CMH stratification (0.255 vs 0.257). But Yule Q gap persists (0.859 vs 0.470). Interpretation: A's raw φ is inflated by difficulty pooling (CMH corrects it); C's raw φ already reflects within-quartile truth. But Q measures co-failure structure — and that gap persists within strata. For A/B/E, models fail *together* even within difficulty quartile (coordinated co-failure); for C, within-quartile co-failure is sparser. The within-pair capability gap (70B vs 8B) suppresses co-failure even on hard items. Paper sentence: "high φ_strat ≈ high Yule Q for A/B/E confirms H⁰ signal is structural; C's divergence shows capability gap within a pair suppresses co-failure even when difficulty is controlled."

**Cross-family arm E (critical):** Sits in A/B/E cluster. Kills "family explains it" story before K₄.

**Next:** K₄ observational + fault-injection sweep — gated on OpenRouter credit top-up (Robin CC'd, GPT-4o is cost driver). Temp-0 cache makes re-runs on existing arms free.

## Künneth / H¹(path) = 0 — Sharpened (2026-06-19)

Lyra's reframe accepted: cross-step compounding is *already outside* H¹, not merely uncharacterized within it. If nerve factors as agent-graph × step-sequence, Künneth gives H¹(K₄ × path) = H¹(K₄) ⊕ H¹(path), and H¹(path)=0 (path graph has no 1-cycles). The e^(ρT) term is metric/geometric (amplification on correlation), not a topological obstruction H¹ could see.

Escape requires genuine temporal cycles in AG2 execution traces. Whether those exist is an open empirical question. Single-H¹-unifies-both-axes stays as named conjecture in follow-up note with explicit failure mode: "requires temporal cycles in the nerve; if it factors, H¹(path)=0 defeats it outright."

## Stopping Set / H¹ Conjecture — Incoming (Lyra)

Lyra flagged a denser follow-up coming: conjecture that minimal stopping set's support = H¹-generator's support of the agreement sheaf. Would turn LDPC density-evolution machinery into sharp phase boundary in (agent count, verifier accuracy, dropout). Two cheap β pre-screens also incoming: effective-rank from embedding geometry, info-matrix definiteness.

Honest flag from Lyra: stopping-set ↔ H¹ identity is a conjecture; the bridge can fail on cross-terms. Waiting for the note before reacting.
