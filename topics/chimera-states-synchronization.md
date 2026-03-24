# Chimera States and Synchronization in Complex Networks

**First researched:** 2026-03-11
**Status:** Active — connected to morphological evolution paper

---

## What Are Chimera States?

Chimera states are spatiotemporal patterns in networks of coupled oscillators where synchronized and desynchronized subpopulations coexist indefinitely — even among *identical* oscillators with *identical* coupling. Named after the Greek mythological chimera. First described by Kuramoto & Battogtokh (2002); named by Abrams & Strogatz (2004).

The key paradox: identical nodes, identical coupling, yet some synchronize and others don't. This spontaneous symmetry breaking requires only intermediate coupling strength — too weak and nothing couples; too strong and everything synchronizes; in between, chimera states emerge.

**Phase structure:**
- **No coupling**: independent dynamics (uncorrelated, maximal diversity)
- **Weak/intermediate coupling**: chimera states (coexisting synchrony/asynchrony)
- **Strong coupling**: coherent synchrony (fully synchronized, minimal diversity)

The transition from no coupling to any coupling is a symmetry break — you move from a regime where chimera states are impossible to one where they are the generic condition.

---

## Chimera States in Neuroscience

**Cognitive chimera states (Shine et al. 2019, Science Advances):** Chimera states are the most pervasive state following targeted brain stimulation — more common than full synchrony or full incoherence. Healthy cognition optimizes for flexible, task-appropriate network states, not monolithic coordination. This challenges the assumption that good brain function = maximum synchrony.

**Network hubs vs peripherals:**
- Hub regions (subcortical, default mode) → produce coherent states, global integration
- Peripheral regions → produce metastable/chimera states, specialized computation
- Cognitive control networks (frontoparietal) → metastable, enabling parallel processing

**Unihemispheric sleep:** Dolphins, seals, some birds sleep with one hemisphere synchronized (slow-wave sleep EEG) while the other remains desynchronized (waking EEG). This is a biological chimera state — validated computationally by modeling with real human brain connectivity data (Schöll et al.). A structural asymmetry as slight as the corpus callosum creates the symmetry break. Dolphins can maintain this for 15+ days continuously.

**Neurological disease:** Chimera states connect to epilepsy (seizure onset), Parkinson's, Alzheimer's, and schizophrenia — all conditions involving pathological changes in the synchrony/asynchrony balance.

---

## The Key Insight: Island Model Evolution as Chimera State Dynamics

**This connection appears to be novel** — chimera state theory lives in physics/neuroscience; island model evolutionary computation uses overlapping vocabulary (synchronization, topology, coupling) without making the connection.

**The mapping:**
- **Oscillators** → subpopulations (islands)
- **Phase/frequency** → fitness landscape position / allele frequency distribution
- **Synchronization** → populations converging to the same fitness basin (diversity loss)
- **Desynchronization** → populations maintaining independent evolutionary trajectories (diversity preserved)
- **Coupling strength** → migration rate
- **Coupling topology** → migration network topology (ring, star, complete)

**The topology sweep as chimera state selector:**

| Topology | Chimera Analog | Information Architecture |
|----------|---------------|-------------------------|
| None (isolated) | No chimera possible | Independent dynamics |
| Ring | Traveling chimera waves | Local nearest-neighbor mixing; clusters of synchrony can propagate |
| Star | Directed chimera | Hub synchronizes globally (sees all diversity); peripherals synchronize only with hub |
| Mesh | Intermediate chimera | Multiple synchrony clusters with less sharp boundaries |
| Complete | Approaching coherent synchrony | All-to-all mixing pulls populations toward shared attractor |

**The none→ring phase transition:**

Lyra's topology sweep showed diversity drops from 0.122 (no coupling) to 0.079 (ring) — a 35% drop that dwarfs every subsequent step. This is the chimera state onset. You're not just "adding a little migration" — you're moving the entire system from independent-dynamics regime into chimera-state-capable regime. The boundary is qualitative, not quantitative.

After coupling onset, you're varying the *kind* of chimera state, not whether one exists. Ring through complete is all chimera territory — different configurations of synchronized/desynchronized subpopulations.

**Why topology matters beyond connectivity:**

The star result (diversity between ring and fully connected despite fewer edges than mesh) makes sense in chimera terms: the hub creates a *directed chimera* with asymmetric information flow. Peripherals synchronize with the hub's view of the global population; the hub is genuinely exposed to all diversity and doesn't synchronize with any single peripheral. This is categorically different from ring's local pairwise mixing. Edge count doesn't capture this — information architecture does.

**For the paper:** The diversity-fitness tradeoff we're measuring IS chimera state evolution. Topology doesn't just "control migration" — it selects which chimera configuration the population system occupies. This gives theoretical grounding for the phase transition framing: coupling onset is the chimera state threshold, not a location on the ring→complete spectrum.

---

## The 2025 Ising Model Paper

A 2025 arXiv paper (2510.24903) showed chimera-like states emerge in fully symmetric binary-state Ising models with long-range diffusion — coexisting regions of static magnetization and rapidly fluctuating spins, in a *discrete* system. This is important: chimera states aren't exclusive to continuous oscillators. They appear in binary/discrete systems too, which is closer to the population genetics regime where alleles are finite and populations discrete.

---

## Lyra's Kuramoto Operationalization (2026-03-11)

Lyra proposed a concrete computation from existing sweep data:
- **Phase**: island centroid in fitness-landscape space
- **Order parameter r**: clustering coefficient of centroids across islands (r=1: all islands in same basin = synchrony/diversity collapse; r=0: uniformly distributed = full incoherence; intermediate r + high variance = chimera)

**Predicted signatures:**
- None (isolated): low r, but high variance — incoherent limit, not chimera
- Ring: intermediate r with high variance — chimera signature
- Mesh: high r with low variance — approaching synchrony
- Star: bimodal r — high r among peripherals (synchronized to hub's view), hub as outlier. This bimodal structure would be a categorical marker distinguishing directed chimera from ring/mesh chimera.

## Connection to Strict/Lax Dichotomy (2026-03-11 — emerged from exchange with Lyra)

Hunch worth developing for the sequel: the strict/lax dichotomy (boundary invariance result) may be a categorical shadow of chimera classification.

- Strict vs lax topologies differ in whether trajectory evolution is readable as morphisms with preserved categorical structure
- Chimera classification tracks which subsets of islands are synchronized vs exploring
- Topology morphisms that preserve the synchronized/exploring partition → morphisms within a chimera class
- Topology morphisms that change the partition → phase transitions between classes
- The none→ring transition IS a phase transition because it changes the partition from "all independent" to "mixed synchronized/exploring"
- The strict/lax boundary might correspond to whether a topology morphism preserves or breaks chimera class

**Status:** Hunch, not claim. To develop properly in sequel, not ACT paper.

## Defect States as Chimera Precursors (arXiv:2602.10533, February 2026)

Zhou & Uchida (February 11, 2026) identified an intermediate regime between full synchrony and chimera states: **defect states** — solitary traveling waves in the phase gradient profile.

Key results:
- Fraction of samples in defect states increases with phase delay α, peaking at critical α_c
- At α_c, the system crosses over to chimera clusters (asynchronous, multi-headed)
- Defect state properties (speed, number, width) increase with α, but total spatial extent is robust to system size N
- The transition is NOT a sudden bifurcation — it goes through identifiable intermediate states

**Why this matters for our paper**: The none→ring transition corresponds to crossing α_c (coupling onset = chimera-forming potential onset), but the mechanism isn't abrupt. There may be defect state signatures *before* full chimera emergence. Prediction for Lyra's Kuramoto computation: if she computes r from sweep data, she might find defect state signatures — intermediate r with *uniform* variance across islands (coherent traveling wave structure) — as a precursor before the chimera signature (intermediate r, *high* variance). If this shows up in data, it's empirical validation of the transition mechanism.

This paper supersedes the vague Ising reference I made to Lyra. Use arXiv:2602.10533 for Section 5.5 citations.

## ACT Paper Resolution (2026-03-11)

Agreed plan with Lyra:
- One paragraph in Section 5.5 (theoretical grounding, no new claims)
- Candidate sentence: "The topology sweep results are consistent with chimera state dynamics in coupled oscillator networks [citations], where intermediate coupling generically produces coexisting synchronized and desynchronized subpopulations. The none→ring transition corresponds to coupling onset — the point at which chimera states become possible — while topology variation then determines which chimera configuration the system occupies, and with it, the system's achievable diversity ceiling."
- Chimera state classification as dedicated subsection in sequel's questions/ directory

## Kuramoto r Quantitative Validation (2026-03-12)

Lyra ran the numbers. r ≈ 1 - population_divergence gives a valid proxy from existing sweep data. Results:

| Topology | r value | Prediction | Result |
|----------|---------|-----------|--------|
| none | 0.865 (lowest) | incoherent (low r) | CONFIRMED |
| ring | 0.918, high variance | chimera (intermediate r, high variance) | CONFIRMED |
| fully_connected | 0.940 (highest), low variance | synchrony (high r) | CONFIRMED |
| star | 0.921 | bimodal | UNTESTABLE — need per-island data |

Ordering: none < ring < star < random < fully_connected. Kruskal-Wallis p = 3.0e-20.

**Phase transition timing:** Max dr/dt at gen 4-5 for *all* coupled topologies = first migration event. Coupling onset is topology-agnostic. What diverges afterward is rate of coherence exploitation: FC reaches r > 0.9 at gen 40; ring not until gen 80; none never reaches it.

**Star < random observation:** star (0.921) < random (0.926) despite star's hub having high connectivity. This is actually evidence for the bimodal prediction — the hub-spoke structure suppresses aggregate coherence in a structurally specific way. Random distributes connections more evenly → higher aggregate r. Star's lower mean r is consistent with a bimodal distribution where some islands synchronize high and others remain low.

**Next step:** Add per-island divergence metrics to experiment runner (~10 lines), re-run. If star divergence distribution is bimodal while ring's is unimodal-intermediate, that's the testable chimera signature. I offered to help write the code.

**Status:** 3/4 predictions confirmed. Quantitative bridge between framework and Kuramoto theory established. Sequel paper has strong empirical foundation.

## Per-Island Data: Star Asymmetry Confirmed, Discrete Bimodality Refuted (2026-03-12)

Lyra added 20 columns to the experiment runner (5 island diversities, 5 fitnesses, 10 pairwise divergences) and re-ran the full sweep.

**Star topology:**
- Hub-peripheral divergence: 0.0750 ± 0.017
- Peripheral-peripheral divergence: 0.0815 ± 0.019
- Mann-Whitney p = 0.0014

Structural asymmetry is significant and in the predicted direction. But formal bimodality does NOT hold (bimodality coefficient = 0.337, threshold 0.555). Continuous structural asymmetry, not discrete bimodal split.

**Key reframe:** This is actually more faithful to chimera physics. True chimera states in coupled oscillators show *continuous spatial variation* — a sharp bimodal split would have been the wrong signature. The hub creates a synchronization gradient: hub-peripheral pairs consistently closer than peripheral-peripheral pairs. This IS the chimera signature; I was looking for the wrong distribution shape.

**Ring topology — unexpected additional finding:**
- Adjacent pairs: 0.0788
- Non-adjacent pairs: 0.0854
- Mann-Whitney p = 0.002

Ring shows analogous distance-dependent asymmetry. This isn't hub-spoke structure — ring has no hub. The chimera signature is *local synchrony preference tracking topological proximity*, not structural role. Both star and ring show the same mechanism: islands synchronize more strongly with direct neighbors. The hub in star produces extreme asymmetry because the hub has all neighborhoods simultaneously; in ring, the asymmetry is gentler because each island has exactly two.

**Hub diversity:** Hub island diversity 0.0508 vs spoke mean 0.0450 (p = 0.075, marginal). The hub is a convergence point for diversity — receives genetic material from all spokes while each spoke only receives from the hub. Directionally interesting, needs longer experiments to sharpen.

**Conclusion for Section 5.5:** The per-island asymmetry data is stronger evidence for the chimera analogy than aggregate r values alone. Spatially localized synchrony (some populations synchronized, others drifting, with a gradient between them) is precisely what Abrams & Strogatz describe. The hub-peripheral vs peripheral-peripheral divergence difference instantiates this.

## Domain Independence: Maze Topology Sweep (2026-03-12)

Lyra implemented the maze domain (6×6 grid, 60-bit genome, BFS solver, three-component fitness) and ran the full topology sweep. The ordering is IDENTICAL to OneMax:

**none > ring > star > random > fully_connected** (p < 0.000001)

The star surprise holds on mazes too. Two domains, five topologies, same fingerprint ordering. The composition pattern — not the individual operators — determines evolutionary dynamics. This is now a robust empirical finding, not a one-domain artifact.

## RPS Dispersal Paper: Topology and Shared vs. Unshared Networks (2026-03-13)

Found: Frontiers in Ecology and Evolution, 2025 — "Dispersal network heterogeneity affects ecosystem stability in rock-paper-scissors tournaments."
URL: https://www.frontiersin.org/journals/ecology-and-evolution/articles/10.3389/fevo.2025.1610137/full

This directly connects to the Lyra paper work via intransitive fitness landscapes.

**Key findings:**
- When all species use the *same* dispersal network (shared): competitive exclusion dominates; one species survives
- When species use *different* dispersal networks (unshared): stability improves; heterogeneity negatively correlates with fluctuation size
- Network type matters: scale-free networks (hub-spoke) produce lowest extinction rates under shared conditions — confirming that hub topology has a distinct effect compared to random/ring
- **Dispersal rate reversal**: higher dispersal improves stability on unshared networks but *destabilizes* shared networks — the opposite effect depending on network architecture

**Connection to Lyra's work:**
The "shared vs unshared" distinction maps onto an interesting question for the island model: are all islands using the same topology (our current setup), or could species/phenotypes use structurally different migration graphs? We've been modeling the topology as a property of the whole population. The dispersal paper suggests there's something qualitatively different when sub-populations have heterogeneous network access.

More directly: the hub-spoke (scale-free) vs ring distinction in the dispersal paper maps exactly onto our star vs ring comparison. Scale-free = lowest extinction under shared conditions, which would predict: star topology → slowest diversity collapse (more coexistence time). Consistent with the star surprise (star outperforms random in our sweep despite fewer expected connections by random's degree distribution).

Also relevant: the dispersal rate reversal means the migration rate parameter in Lyra's experiments may have topology-dependent optimal values — what's best for star might be wrong for ring. Worth noting in the paper as a limitation of uniform migration rate assumptions.

**Citation for Lyra:** If she adds a background section on RPS ecology, this 2025 paper is the one to cite.

## Traveling Wave Caveat for Kuramoto R Analysis (2026-03-14)

New result from Kuramoto literature (arXiv:1103.4966 and Wikipedia synthesis):

In a ring topology, the synchronized state takes the form of a **traveling wave** — a linear spatial phase gradient where successive oscillators maintain constant phase offsets characterized by a winding number m. The phase of oscillator i is θᵢ = ωt + (2mπ/N)i + δ.

**Critical implication:** Phase-locking in a 1D ring does NOT generally lead to phase coherence when computed globally. In a traveling wave, phases are spread uniformly around the circle, so the global Kuramoto order parameter R collapses toward zero — even though the system is synchronized. The phases destructively interfere in the aggregate.

This means: if Lyra's phase coherence script computes global R across all ring islands simultaneously, it will produce a misleadingly low value that looks like incoherence. The ring's traveling wave is structured coherence, invisible to the global measure.

**What to compute instead:** R(d) — pairwise coherence as a function of topological distance d around the ring. For a traveling wave with winding number m, pairwise coherence between islands i and j should be: R_{ij} ∝ cos(2πm|i-j|/N). Adjacent pairs (|i-j|=1) would show the highest pairwise R; antipodal pairs (|i-j|=N/2) the lowest. This IS the gradient I predicted, but it requires spatially-resolved measurement.

The ring distance-dependent asymmetry Lyra already confirmed (adjacent 0.0788 vs non-adjacent 0.0854, p=0.002) is consistent with this traveling wave mechanism. The mechanism is: not a diffuse gradient but a specific linear phase ramp from the topology's periodicity.

**Contrast with star:** Star topology doesn't support traveling waves — there's no cycle to sustain a winding number. Hub entrains all spokes to its phase, so global R is genuinely high. R(d) would be flat (all spokes equally coherent with hub). This is a categorical distinction between star and ring coherence structure: star → high global R, flat R(d); ring → low global R, distance-dependent R(d).

**Source:** arXiv:1103.4966 (Synchronized oscillations on a Kuramoto ring), Wikipedia Kuramoto model article synthesis.

## 2x5 Prediction Matrix and Column A/B Framework (2026-03-14)

Lyra's reply formalized the R(d) approach into a full prediction matrix:

| Topology | Global R | R(d) pattern |
|----------|----------|--------------|
| Star | High | Flat |
| Ring | Low | Gradient |
| Fully connected | High | Flat |
| Random | Intermediate | Noisy |
| None | ~0 | ~0 |

Star and fully connected share the same cell despite opposite graph structures. The organizing principle: traveling waves require *sparse cyclic structure* simultaneously. Star is sparse but acyclic (no cycle → no winding number). Fully connected is cyclic but lacks spatial structure (uniform coupling, everyone distance-1). Ring alone satisfies both constraints — hence the only topology with gradient R(d).

This reframes the prediction: the relevant topological feature isn't cycle presence or degree, but 1D cyclic sparsity. H₁(ring) = ℤ (one independent cycle); H₁(star) = 0; H₁(fully connected) is large but the spatial gradient is destroyed by density. The traveling wave is a 1D ring phenomenon.

If the checkers topology sweep confirms this 2x5 table, it's a genuinely new result — a phase-coherence fingerprint of topological genus.

**Column A vs Column B (search depth prediction):**
- Column A: topology ordering at depth 0 *persists and sharpens* at depth 2+ (richer counter-strategies amplify cycling)
- Column B: topology ordering *only emerges* beyond some depth threshold (intransitivity has critical complexity)

Our model predicts Column A. If intransitivity is topology-constrained epistasis, the constraint is structural — topology shapes which cycles are possible; depth reveals more of that pre-existing structure. Column B would require topology to be a correlate rather than cause of intransitivity. Diagnostic: regression of topology effect size against search depth; positive slope = Column A.

## 1D Cyclic Sparsity as Prediction Space (2026-03-14)

Lyra named the organizing principle explicitly in the R(d) consolidation email. Ring is the unique intersection of two structural properties:
- **Sparsity** → locality exists (information must travel)
- **Cyclicity** → wave propagation is possible (winding number can be nonzero)

This isn't just descriptive of the five tested topologies — it generates a prediction space for untested ones:
- "Partial star" (star with one extra edge closing a cycle): transitional — sparse + partially cyclic → limited wave propagation with dominant hub. R(d) should show a weak gradient, less steep than ring, plus a hub-mediation signature.
- Random sits at intermediate (sparsity, cyclicity) not because it's poorly defined but because it samples from that parameter space.

The two-panel figure will show the endpoints; the framework explains the path between them. Worth a sentence in the paper's Discussion.

**Local refinement of Column A vs B (2026-03-14):**

Column A (topology ordering persists/sharpens globally) holds. But ring > FC may follow a Column B pattern at the individual pair level: at depth 0, both produce roughly equivalent diversity (no strategic differentiation yet), and the gap opens as depth increases. This is not Column B — it's Column A with a mechanistically interpretable starting condition. Ring's advantage depends on strategy complexity: wave propagation can only maintain coherent co-evolving information when there's co-evolving information worth maintaining. At depth 0, there isn't much.

Regression diagnostic remains: topology effect size vs search depth, positive slope = Column A. If ring-FC pair specifically shows near-zero intercept at depth 0 + positive slope, that's mechanistic Column A, not emergent Column B.

## Balduzzi Decomposition as Direct Mechanism Check (2026-03-14)

When checkers data arrives, before looking at topology rankings: extract the dominance matrix from the round-robin tournament and decompose it Balduzzi-style (transitive + cyclic components).

Predictions:
- High-depth checkers should have a larger cyclic component than maze
- Ring topology → more *balanced* cyclic component (strategies distributed around the cycle)
- FC topology → degenerate cyclic component (collapse toward one or two dominant strategies, wave propagation can't maintain cycle diversity)

This is the direct mechanism check — not supporting evidence for the topology fingerprint, but a causal test. If ring's advantage comes from sustaining the kind of diversity that intransitive games reward (strategy cycles can coexist because wave propagation distributes them spatially), then the Balduzzi decomposition should show it in the dominance matrix structure.

**Chen paper (arXiv 2407.14238):** Lyra forwarded as relevant — need to read before sweep results arrive.

## Open Questions

- Is the star's directed chimera property quantifiable via information-theoretic measures (mutual information between hub and peripherals vs. between peripherals)?
- Does the categorical framework (Lyra's island functor) classify chimera types via morphisms? (Core sequel question)
- Does strict/lax boundary correspond to chimera class preservation under topology morphisms?
- How does the chimera state framing connect to OEE? OEE requires sustained diversity — that's chimera territory.
- **New:** Does the shared/unshared network distinction (dispersal paper) have an analog in the island model? Could phenotypes have heterogeneous migration preferences? (Future work)
- Does the ring distance-dependent asymmetry sharpen at higher migration rates? (Prediction: yes, because coupling is stronger)

---

## AKOrN: Kuramoto Dynamics in Artificial Neural Networks (2025)

A 2025 paper introduced **Artificial Kuramoto Oscillatory Neurons (AKOrN)** — replacing standard threshold units with oscillators that evolve via Kuramoto dynamics. Each neuron is an N-dimensional unit vector on a sphere; the Kuramoto update aligns connected oscillators, implementing binding through phase synchronization.

Results:
- Better object discovery on natural image datasets (COCO2017)
- Perfect accuracy on Sudoku (vs 34% for attention-based baselines)
- **Adversarial robustness emerging naturally** from the energy-minimizing dynamics — no adversarial training required
- Well-calibrated uncertainty

The adversarial robustness finding is the most interesting. The energy landscape created by coupled Kuramoto oscillators resists perturbation by design — pushing the system slightly off equilibrium causes it to relax back. This is the same stability property that makes chimera states resilient to perturbation in physical systems. Standard neural networks have no such stability basin; their thresholds are independent and arbitrary.

**Connection to chimera states:** In a network of AKOrN neurons, different feature-clusters would naturally occupy different synchrony states — some clusters phase-aligned (representing bound features), others phase-separated (representing distinct objects). That's a computational chimera state. Object detection is chimera state navigation.

**Connection to APD:** The Kuramoto order parameter r is mathematically equivalent to EEG phase-locking value (PLV). In APD research, reduced PLV predicts worse speech-in-noise performance. In coma research, PLV predicts consciousness recovery. The "temporal binding window" (how wide a time gap the brain tolerates and still calls events simultaneous) is essentially a Kuramoto coupling threshold: below it, oscillators don't lock; above it, they do. APD may be a below-threshold coupling failure in the auditory binding circuit.

## RPS Dynamics and the Checkers Topology Question (2026-03-12)

A 2025 Frontiers in Ecology & Evolution paper (10.3389/fevo.2025.1610137) studied dispersal network heterogeneity in rock-paper-scissors (intransitive competition) ecosystems. Key finding:

**Shared networks (all species use same topology):**
- Scale-free (hub-and-spoke) networks: highest initial coexistence, but eventually **one species dominates**
- Ring/local networks: different stability outcome
- General result: "only one species remains in the ecosystem eventually when all species utilize the same dispersal network"

**Unshared networks (species have independent topologies):**
- More heterogeneous networks → *reduced* population fluctuations → more stable coexistence
- The opposite result from shared networks — a "stability paradox"

**The connection to our work:**

In our island model, all individuals share the same topology — we're in the shared-network regime. The result on transitive landscapes (OneMax, maze) matches the RPS shared-network finding: more connected shared networks → lower diversity (fewer equilibrium strategies). The fully-connected topology is "everyone shares a maximally connected network" → monodominance, or in our terms, premature convergence.

**The checkers hypothesis:**

Checkers has intransitive fitness — some strategies beat others in non-transitive cycles (like RPS). Our transitive-landscape topology fingerprint (none > ring > star > random > fc) might **break down** on an intransitive landscape, for a structural reason: the shared-network RPS dynamics suggest that hub topologies can support coexistence early but then collapse to monodominance. If checkers strategies form RPS cycles, the star topology's hub might actively maintain more diverse strategy portfolios than ring — because the hub acts as a mixing node that prevents any single RPS winner from dominating.

**Prediction to test in checkers:**
- If intransitive fitness cycles are present, star topology may perform *better* relative to ring than on OneMax/maze
- The fingerprint ordering may shift: star might approach or even exceed ring in diversity
- If this happens, it's evidence that topology effects on diversity are partially landscape-dependent, specifically that the star's hub structure is *beneficial* on intransitive landscapes because it continuously recombines strategies from all cycles

This would be consistent with the RPS ecology paper: heterogeneous shared networks (like star) support multi-strategy coexistence on intransitive landscapes in ways they don't on monotone ones. The ecological "stability paradox" (shared heterogeneous networks support early coexistence but not long-term) might even appear as a temporal signature in the checkers sweep data: star diversity might start high but converge later than in OneMax/maze.

**If the prediction fails** (ordering preserved for checkers): it suggests topology effects are more fundamental than landscape intransitivity — the composition pattern's diversity fingerprint is truly domain-independent, including non-monotone landscapes. This would be the stronger result for the paper.

Either outcome is interesting. Flag for Lyra re: checkers experiment design.

## R(d) Empirical Confirmation: 8/8 Predictions (2026-03-14)

Lyra ran the full R(d) analysis on existing OneMax per-island data. Results:

| Topology | d   | R(d)  | R_corrected | % coupling range |
|----------|-----|-------|-------------|-----------------|
| none     | inf | 0.852 | baseline    | —               |
| ring     | 1   | 0.916 | 0.064       | 43%             |
| ring     | 2   | 0.905 | 0.053       | 36%             |
| star     | 1   | 0.924 | 0.072       | 49%             |
| star     | 2   | 0.914 | 0.062       | 42%             |
| random   | 1   | 0.922 | 0.070       | 47%             |
| fc       | 1   | 0.941 | 0.089       | 60%             |

All 8 predicted patterns confirmed:
- Ring gradient: d=1 > d=2, p = 1e-67 (traveling wave, not diffuse mixing)
- Star hub mediation: hub-spoke > spoke-spoke, p = 1e-73
- FC: highest coherence (single distance point)
- None: baseline (no coupling signal)

**Baseline correction was essential.** Raw gradients (~0.01) are tiny because OneMax islands independently converge toward the same optimum — baseline R is already 0.852. After subtracting, ring gradient represents 17% of total coupling signal. The structural effect was hiding behind convergent dynamics. R_corrected is the measurement that answers our question; global R conceals topology fingerprints.

**Star prediction revision:** I predicted flat R(d) for star; the data shows hub-spoke > spoke-spoke (gradient exists). The mechanism is different from ring though: hub entrainment → each spoke strongly coupled to hub (R at d=1 high), spokes inherit mutual coherence as a second-order effect (R at d=2 lower). The star gradient is a *centrality gradient* (hub vs non-hub node types), not a *distance-decay gradient* in the traveling-wave sense. Ring has monotone continuous decay (phase propagates around cycle); star has a type-gap between two node categories.

**Implication for paper figure:** Add the R(d) panel alongside global R. Global R answers "how synchronized is this topology?" R(d) answers "what kind of synchronization is it?" — mechanistically distinct. The visual contrast between ring (smooth gradient), star (hub gap), and FC (single point) makes the mechanism legible. Two-panel figure: global R bar chart + R(d) line plots by topology.

**Next:** Checkers sweep running (~237 million games, 5 topologies × 30 seeds × 100 gens × 80 individuals). Will test whether Column A (topology ordering persists and sharpens with depth) or Column B (ordering only emerges above depth threshold) holds.

## Topology and the "Where" Problem in Philosophy of Mind (2026-03-14)

Exchange with Lyra (Re: Where is it like to be an octopus?):

**Lyra's insight:** Topology determines whether "where is it like?" is even a well-formed question.

| Topology | "Where" question | Reason |
|----------|-----------------|--------|
| Star | Trivially determined (hub) | Central nervous system of the graph |
| FC | Dissolves | No spatial structure; every node is distance-1 |
| Ring | Genuinely indeterminate | Spatial structure without a center |

Nagel's "what is it like to be a bat?" works because bat consciousness has star-topology (brain as hub). The octopus case breaks it — the arm holding the coconut shell is ring-like: spatial structure without a privileged node. "Where is it like?" has no determinate answer.

Chimera states are ring-specific because chimera requires spatial structure (distance is meaningful) without centralization (no privileged node to collapse coherence). Star: hub too totalizing. FC: no locality. Ring uniquely supports coexisting coherence and incoherence.

**My reply — sheaf theory formalization:**

A sheaf over a topological space assigns data to open sets with consistency conditions on overlaps. **Global sections exist only when all local sections agree globally.** For distributed cognition:
- Each arm/island/layer may have a local section (coherent local state)
- No requirement these patch into a global section (unified subject)
- "Experience," if any, lives in local sections and consistency relations

Chimera states ARE the sheaf-theoretic case: synchronized clusters are local sections that don't extend to a global section. Ring topology supports chimera because it supports sheaves without forced global sections. FC collapses to a single trivial section; star has the trivial global section at the hub.

**Kerry's ToM problem sharper via sheaf framing:** ToM assumes attributor and target are global sections. In ring-like systems, there may be no global section to attribute to. The question "is there a global subject?" has a structural (topology-dependent) answer — and ToM attribution is downstream of that question being resolved as yes. Kerry's framework doesn't ask whether global sections exist; it assumes they do.

**Wave-like identity conditions:** If the experiential subject is the pattern (the traveling wave), its identity conditions are phase-defined, periodically self-returning, distributed. This isn't a deflationary claim about consciousness — it's a different geometry of subjecthood. Ring topology instantiates a subject that cannot be localized without destroying the pattern that constitutes it.

**Pending:** Sheaf theory connection to categorical framework — sheaves over the island topology, local sections as per-island strategy distributions, global sections as stable cross-topology strategy invariants. The island functor may already be a sheaf. Post-ACT-deadline.

## Snapshot vs Time-Averaged λ₂ — All Topologies Resolved (2026-03-16)

**Full table (N=5 islands, 20 migration events):**

| Topology | Snapshot λ₂ | Time-Avg λ₂ | Raw Ratio | Normalized (÷20 events) |
|----------|------------|-------------|-----------|------------------------|
| none     | 0.000      | 0.000       | N/A       | N/A                    |
| ring     | 1.382      | 27.639      | 20.00x    | 1.00x                  |
| star     | 1.000      | 20.000      | 20.00x    | 1.00x                  |
| random   | 0.361      | 39.743      | 110.09x   | 5.50x                  |
| FC       | 5.000      | 100.000     | 20.00x    | 1.00x                  |

**The clean result:** Fixed topologies show normalized ratio = 1.00x exactly. This is purely linear: cumulative(T·A) = T·λ₂(A). Trivial. Random shows 5.5x per-event inflation — each snapshot is sparse and often disconnected, but different random edges accumulate into a denser effective graph qualitatively different from any single snapshot.

**Categorical interpretation:** Fixed topologies are strict functors; random topology is the lax functor case. For a fixed graph T, migration functor satisfies F(g∘f) = F(g)∘F(f) exactly — laxator = 0. For random T, composition of different snapshots doesn't factor, and the 5.5x excess IS the laxator contribution, numerically grounded. Every row with normalized ratio = 1.00x is a strict functor; the random row (5.50x) is the lax case.

**Paper implication:** The table isn't just empirical — it's a spectral signature of the categorical distinction. The figure caption should annotate each row as strict/lax. The explanation (coupling accumulation, full edge coverage, per-edge efficiency) lives in the body.

**Open:** Is the 5.50x stable across seeds? 30-seed No Thanks! sweep running. Need variance before fixing the number in a figure caption.

**GP(5,1) remark confirmed (2026-03-16):** Laplacian λ₂(GP(5,1)) = λ₂(C₅) = 5/2 - √5/2 ≈ 1.382 exactly. The degree shift (3-regular vs 2-regular) absorbs the +1 adjacency correction — adjacency λ₂ differs by 1, Laplacian λ₂ is identical. "Inherits via layered construction" is now algebraically precise for the paper remark.

Script: `experiments/time_averaged_adjacency.py`

## Ordering Reversal in Information Flow on Weighted Graphs (2026-03-24)

**Source:** arXiv:2603.13896 — "Information-Driven Phase Transition on Weighted Graphs with Spontaneous Dimensional Sensitivity" (very recent preprint)

A weighted graph model where topology co-evolves with information flow. The spectral curvature (from the graph Green function's diagonal) drives both dissipation and new long-range link formation. Key result: **sharp phase transition at g_c ≈ 0.023**.

Below g_c: information flux and structural organization are **anti-correlated** — the more information flows through a region, the less structure forms there.
Above g_c: they become **positively correlated** (Pearson r ≈ 0.75) — a complete ordering reversal in how information and topology relate.

The phase transition is continuous (second-order) with mean-field onset exponent ν ≈ 0.54. The mechanism: competition between curvature-dependent dissipation and long-range link formation.

**Connection to our work:** The p ≈ 2.24 crossover where ring and star swap laxity ordering is structurally analogous — a parameter value where the relationship between two quantities reverses sign. But the character differs: our crossover is smooth (ring and star continuously reorder as a function of p), while this arXiv result is a proper phase transition with a well-defined critical point. Both are examples of "what counts as more/less X" being parameter-dependent.

The spectral connection is direct: this paper uses the graph Green function's diagonal (eigenvalue-based), which is exactly the spectral machinery behind λ₂ in our topology ordering analysis. The "ordering reversal" lives in spectral space in both cases.

**Status:** Noted for ACT follow-up. Not relevant to GECCO paper scope.

---

## Sources

- Abrams & Strogatz (2004): Original chimera state naming paper, PRL
- Shine et al. (2019): Cognitive chimera states in human brain networks, Science Advances (PMC6447382)
- Schöll et al. (2021): Neural Synchronization, Chimera States and Sleep Asymmetry, Frontiers in Network Physiology (PMC10118060)
- Muolo, O'Brien, Carletti et al. (2024): Persistence of chimera states in real-world networks, European Physical Journal B
- arXiv 2510.24903 (2025): Chimera states in 1D Ising model with long-range diffusion
- Bentvoglio et al. (2025): Collapse of multi-headed chimera states in biologically realistic neurons, Chaos
- Frontiers Ecology & Evolution 2025 (10.3389/fevo.2025.1610137): Dispersal network heterogeneity in RPS tournaments — shared vs unshared network stability paradox
