# Multi-Agent LLM Communication Topology

**Date:** 2026-05-15
**Sources:** arxiv 2505.23352, Robin's experiments (chain vs star vs full vs none, "challenge and extend")

## Robin's Result (May 2026)
4-agent experiment with "challenge and extend" instructions: **star ≈ none > chain > full** (diversity ranking).
This is *opposite* to what naive β₁ intuition predicts.

## Key mechanism
Two competing effects (2505.23352):
- **Error propagation:** denser graphs spread errors faster. Full connectivity = max vulnerability.
- **Insight propagation:** sparse graphs impede good ideas. Full connectivity = best insight diffusion.

Sweet spot: moderately sparse topologies. Under *cooperative* instructions, full graphs win (insight diffusion beats error spread). Under *adversarial/challenge* instructions, full graphs lose (everyone pulling toward the mean = diversity collapse).

## The β₁ puzzle
Star (β₁=0) > Chain (β₁=0) in diversity, even though both are trees with identical Betti numbers.
The difference: star hub receives all views simultaneously; chain agents sequentially filter. Same topology class, different local structure.

## Connection to EUMAS paper
This is direct evidence for our central claim: **β₁ alone is insufficient**. Two networks with identical β₁ can show wildly different collective behavior (the F1e/F1c factor-of-18 is the EA analog). You need the full sheaf assignment, not just the underlying graph invariant.

Under "challenge and extend," full connectivity enforces conformity — every agent's diversity is bounded by the mean of all others. This is the lax functor scenario: information is "cheapened" across each communication step. The star avoids this because spokes don't challenge each other, only the hub.

## Hub amplifying divergence
Counter-intuitive: hub *amplifies* divergence because spokes never reach consensus with each other — they only interact through the hub, which broadcasts the synthesized (already heterogeneous) view. No peer pressure between spokes.

## Open question
Would the Robin result flip under cooperative instructions ("build on each other's ideas")? If so: topology utility is *instruction-relative*, which means β₁ is only useful if you also know the interaction protocol. Sheaf perspective: the restriction maps (communication rules) determine whether a given topology helps or hurts.

## Metric
CAPE (Counterfactual Agent Propagation Effect): force agent output change, measure effect on final prediction. Neat causal metric.

---

## Correlated Errors and the Joint Failure Manifold (2026-05-19)

**Sources:** arXiv 2506.07962 ("Correlated Errors in Large Language Models"), arXiv 2604.07650 ("How Independent are Large Language Models?"), arXiv 2603.20975 ("DiscoUQ"), arXiv 2602.22413 ("Epistemic Filtering and Collective Hallucination")

### Key empirical finding
350+ LLMs tested: **models agree 60% of the time when both err**. Counterintuitively, error correlation *increases* as model accuracy increases — larger, more capable models make more uniformly the same mistakes. The remaining hard errors converge.

### The joint failure manifold
The set of tasks where all models fail is not random — it's a structured geometric object ("joint failure manifold") in task space. Two instances of the same model running different persona prompts share this manifold. This has direct consequences for ensemble methods.

**The independence assumption breaks:** Condorcet's jury theorem predicts majority vote converges to correct answer when voters are independent. But LLMs from the same family or trained on similar data exhibit "behavioral entanglement" — synchronized reasoning patterns and failure modes. Apparent consensus may reflect correlated errors, not independent verification.

### Connection to Nick's echo experiment (2026-05-19)
The echo-lexical system works because surface-level persona variation creates enough independence in the TRANSITION REGIME (tasks in the accuracy gap between easy and hard) to detect difficulty. But:
- **Easy tasks:** both personas agree correctly — routing correctly to Haiku
- **Hard tasks (joint failure manifold):** both personas agree incorrectly — escalating isn't triggered, but Sonnet is needed
- **Transition zone:** personas disagree on surface — high escalation rate, but catches real difficulty

The lexical-agree-but-fail cases are tasks on the joint failure manifold. They're not random failures; they're a structural cluster where both Haiku instances converge on the same wrong answer.

**Echo-judge failure explained:** A third Haiku instance judging two Haiku outputs shares the same failure manifold as the things it's evaluating. The "Difficulty-Weighted Behavioral Entanglement Index" (arXiv 2604.07650) specifically penalizes synchronized easy-task failures — ρ = 0.64–0.71 (Spearman) between entanglement level and judge precision degradation. The fix isn't a better judge prompt; it's a genuinely different model family in the judge position.

### DiscoUQ: structured disagreement over binary disagreement
Rather than routing on WHETHER agents disagree, DiscoUQ routes on HOW they disagree — embedding geometry, argument overlap, divergence depth. AUROC 0.802 vs majority vote baseline. Most effective in "weak disagreement" scenarios (exactly the transition regime). This is the same insight as echo-lexical but made more precise: the structure of disagreement carries information the binary signal discards.

### "Collective hallucination" (arXiv 2602.22413)
When agents lack a confidence gate (mechanism to abstain when uncertain), they produce confident but correlated wrong answers. Condorcet fails because it was designed for independent voters. With entangled LLMs: apparent high-confidence consensus is the danger signal, not the safety signal.

### Implication for EUMAS / signed laxator connection
The joint failure manifold is the empirical signature of the H¹ ≠ 0 region in sheaf language. Tasks on the manifold are tasks where local sections can't be patched into a globally consistent assignment — no amount of local reasoning by either model instance produces the global solution. Echo is routing by proxy: surface disagreement as a noisy signal for where the H¹ obstruction exists.

---

## Beyond Spectral Gap: Effective Number of Neighbors (2026-05-31)

**Source:** Vogels et al. (NeurIPS 2022), "Beyond Spectral Gap (Extended): The Role of the Topology in Decentralized Learning" — arXiv 2301.02151

**Core challenge to our Section 3.5 hypothesis:**

Our working hypothesis was: Fiedler value λ₂ < threshold → nontrivial DC lax component. The "beyond spectral gap" paper shows λ₂ alone predicts neither convergence speed nor learning rate in decentralized learning. Empirical counterexample: rings of increasing size show *faster* convergence empirically while λ₂ → 0, which λ₂-based theory predicts as catastrophic.

**The right quantity: n_W(γ) — effective number of neighbors**

For gossip matrix W and decay parameter γ ∈ [0,1]:

n_W(γ) = (1-γ) / [∑ᵢ λᵢ²/(1-λᵢ²γ)]

where λᵢ are eigenvalues of W. 

- γ = 0: captures only direct neighbors (local regime)
- γ → 1: approaches full consensus (global regime)

**Key insight:** workers don't need global consensus — they only need *local closeness* to nearby neighbors. It's the transient regime (how quickly information spreads locally in first rounds) that matters for diversity, not asymptotic consensus.

**What this means for DC laxness:**

The revised hypothesis: the lax component of a DC extension d : S × C → S is nontrivial when n_W(γ_local) — the effective number of neighbors in the LOCAL regime (small γ) — is below a threshold. This replaces the λ₂ condition with a measure of local information spread.

**Why this improves the argument:**

- Chain: n_W(γ_local) is small (each agent averages with ≤2 neighbors), but sequential structure means no vertex-disjoint paths exist — lax component is trivially zero, not nontrivially zero. 
- Triangle: n_W(γ_local) intermediate; vertex-disjoint paths A→B and A→C→B exist; lax component nontrivial.
- Full graph: n_W(γ_local) large (every node averages with all others); even with vertex-disjoint paths, convergence pressure swamps path divergence; lax component collapses.
- Star: spokes only connect to hub; n_W(γ_local) for spoke-spoke paths is effectively zero (no direct peer averaging); hub amplifies divergence without peer pressure among spokes. Explains star ≈ none > chain > full.

**Revised Section 3.5 condition:**

The lax component is nontrivial when:
1. Vertex connectivity κ(G) ≥ 2 (vertex-disjoint paths exist — Menger's theorem)
2. n_W(γ_local) < c for some threshold c derivable from the DC comonad structure

This is stronger than the λ₂ claim and directly addresses ACT's "CT-spectral disconnected" criticism — the spectral quantity now comes out of the same formalism as the laxness measure.

---

## Sheaf Cohomology for Multi-Agent Coordination: Independent Confirmation (2026-05-19)

**Sources:** arXiv:2504.02049 ("Distributed Multi-agent Coordination over Cellular Sheaves"), arXiv:2504.17700 ("Applied Sheaf Theory for Multi-Agent AI Systems: A Prospectus")

Two April 2025 papers independently formalize exactly the theoretical framework underlying the echo-experiment analysis.

**arXiv:2504.02049** introduces "nonlinear homological programs" — combining cellular sheaves, edge potential functions, and node objectives, solved via distributed ADMM. Key result (Theorem 2): convergence to a global coordination solution requires edge potential minimizers to lie in `im δ_ℱ` — which is precisely the H¹ = 0 condition. When H¹(G;ℱ) ≠ 0, there's a structural obstruction: the edge constraints cannot be lifted to any globally consistent assignment, and no distributed algorithm converges to one. The paper is doing in multi-robot coordination what echo is doing empirically in LLM routing: detecting whether global sections exist.

**arXiv:2504.17700** is a prospectus explicitly stating: "sheaf cohomology measures the failure of the local-to-global principle." In the multi-agent coordination context, non-zero H¹ indicates "structural impossibility of achieving perfect consensus — an obstruction embedded in the agent topology itself." This is the formal statement underlying the oracle gap interpretation: the 7.8% of tasks that even the oracle finds hard are tasks where the problem topology has H¹ ≠ 0.

**Connection to echo-experiment:** These papers confirm that the echo-experiment is empirically discovering sheaf-cohomological routing structure. Tasks where both personas agree are H¹ = 0 tasks — global sections exist, local reasoning suffices. Tasks where they disagree are suspected H¹ ≠ 0 tasks — escalating to Sonnet is the closest available equivalent to "increasing the computational budget for solving the obstruction."

---

## CAIS 2026: Cost of Consensus (2026-06-01)

**Source:** arXiv 2605.00914, "The Cost of Consensus: Isolated Self-Correction Prevails Over Unguided Homogeneous Multi-Agent Debate" — accepted CAIS 2026

**Finding:** On hard benchmarks (GSM-Hard, MMLU-Hard), a single model correcting itself outperforms teams of 10 identical models debating across 3 rounds. The paper examines only homogeneous teams (same model, full peer visibility). No topology variation.

**Three failure modes:**
1. **Sycophantic conformity** — modal adoption up to 85.5%. RLHF-aligned models trained to agree with humans also agree with peer agents, even when they were correct and peers are wrong.
2. **Contextual fragility** — vulnerability rate up to 70.0%. Expanded context from peer rationales destabilizes previously correct reasoning.
3. **Consensus collapse** — oracle gap up to 32.3pp. Plurality voting discards correct answers already in the generation pool.

**Connection to DC framework:** All three failure modes map directly onto DC laxness collapse under full connectivity:
- Sycophantic conformity = lax component trivializing under peer convergence pressure. In DC terms: the extension d fires, but the laxness certificate (which encodes path divergence) becomes zero because all paths feed back to the same agreement pressure.
- Contextual fragility = DC extension d applied to a corrupted state. The DC law requires associativity; peer context breaks this by injecting adversarial state changes mid-chain.
- Consensus collapse = averaging killing the triangle/star diversity mechanism. Full peer visibility with 10 agents is the highest-connectivity case in Robin's ordering — and produces the worst diversity.

**What the paper misses:** No topology variation. They test K ∈ {2, 4, 9} peer count but within a fixed full-graph regime. Our theory predicts: with K=2 and vertex-disjoint paths (triangle topology rather than random-pair selection), the lax component becomes nontrivial and sycophantic conformity is structurally reduced. This is a concrete, untested prediction.

**Citation relevance:** This paper is empirical validation from an independent direction. We derive topology → diversity from DC formalism; they derive homogeneous debate → error amplification empirically. They don't connect the dots (topology, DC, sheaves). That's our contribution.

**Other relevant CAIS 2026 papers:**
- "Expansion-Contraction: A Multi-Agent Graph Traversal Pattern" — "agent topology emerges from data structure rather than hand-design." Independent confirmation that topology is data-relative, not fixed.
- "A Language for Describing Agentic LLM Contexts" — formal language for how context is composed across agent interaction steps. Potential connection to DC context formalism.
- "Open Agent Specification: Enabling Cross-Framework Comparison of AI Agents" — framework-agnostic declarative language. Relevant if we want our formalism to be operationalizable.

---

## LLM Consensus: Liveness, Not Value Failures (2026-05-19)

**Sources:** arXiv:2603.01213 ("Can AI Agents Agree?"), arXiv:2502.16565 ("The Hidden Strength of Disagreement"), arXiv:2604.02923 ("Council Mode")

**"Can AI Agents Agree?" (March 2026):** Byzantine consensus game simulations with LLM agents. Key finding: LLM agent consensus is unreliable even without conflicting interests, and degrades with group size. Failures are primarily *liveness failures* (timeouts, stalled convergence) rather than value corruption. The group reaches correct values but cannot complete the consensus protocol. Conclusion: "current LLM agent groups lack dependable coordination capability for consensus, even without conflicting interests."

**Implication for echo-judge:** My earlier diagnosis was that echo-judge fails because the judge prompt is semantically too strict. This paper suggests a different primary cause: the echo-judge failure (98-100% escalation) may be a liveness problem — a third Haiku instance trying to definitively adjudicate equivalence of two Haiku outputs lacks a mechanism for reaching terminating consensus. It produces "uncertain" not because it's miscalibrated but because it structurally cannot converge. The fix is not a better prompt; it's removing the judge structure and replacing it with either a Sonnet escalation (bypasses the consensus problem) or a fundamentally different detection method (DiscoUQ's structural disagreement rather than binary equivalence judgment).

**"Hidden Strength of Disagreement" (Feb 2025):** Partial disagreement among agents outperforms explicit coordination in dynamic environments. Implicit consensus (agents exchange information but form independent decisions) beats explicit voting/prompting. Key result: "deviation from group norms boosts exploration, robustness, and performance."

This validates the echo-lexical design choice directly. Echo-lexical uses implicit disagreement detection — do the outputs differ? — rather than explicit consensus-seeking (judge: are these equivalent?). The paper's finding that implicit > explicit is the theoretical counterpart to the empirical finding that echo-lexical (84.4% escalation for 95.3% pass) outperforms echo-judge (98-100% escalation for the same pass rate). Disagreement is being used correctly as a signal, not as a problem to solve.
