# Knot Theory: Biology, Computation, and the Jones Polynomial

## Core thread

Knot theory keeps appearing as both a biological mechanism and the substrate of computation. These aren't loose analogies — they converge on the same mathematics.

## New findings (September 2026)

### Knotted Solenoid Fold (PMC13123833, 2026)
The entire β-solenoid protein family was considered definitively unknotted. New paper found a member with a **trefoil (3₁) knot**, formed via a "skip-and-backtrack" mechanism: one coil skips a rotation while the next realigns, creating an extended linker (~25 residues) that threads through itself. The protein self-ties with no specialized chaperone machinery — via a slipknot intermediate that tightens into the native trefoil. Sequences with as little as 6% identity share this topology. The "impossibility" was structural assumption, not proof.

This is the local-rules-generating-global-topology principle made precise: one coil misbehaves locally, and everything downstream is topologically different.

### Tandemly Knotted Protein (Protein Science, 2025)
Artificial tandemly knotted protein (two trefoil domains). Key finding: polypeptide chains **can escape deep kinetic traps** — the knotted topology is accessible, not locked out. More complicated folding landscape than single-trefoil proteins, but navigable. Challenges the assumption that knotted proteins require extreme folding precision.

### Robot That Unknots Knots (arXiv:2504.01254, 2025)
Theoretical robot that walks a knot diagram, **flipping every undercrossing it encounters**. This produces an "ascending diagram," which is provably trivial (unknottable). Bound: at most (7C+1)C Reidemeister moves for a diagram with C crossings.

Interesting inversion: the protein self-ties via a local skip-and-backtrack; the robot untangles via a local flip. Both are single-pass local rules generating global topological outcomes.

### Universal Quantum Gates from Anyon Braiding (Nature, July 2026)
54-qubit realization of non-Abelian S3 topological order. Demonstrated that **anyon braiding + fusion = universal topological quantum computation**. The key property: computation depends only on the topology of the braid path, not speed, timing, or execution precision. Topology-as-error-correction: local perturbations can't corrupt the result because the result is a topological invariant.

**New angle (September 2026):** The crucial move isn't switching from D4 to S3 anyons — it's adding *fusion* as a second computational primitive. Previous D4 + braiding-only demonstrations weren't universal; researchers noted "that particular universe was not powerful enough." The problem: braiding is *reversible*. You can unbraid. The topology is preserved throughout. But you can't do universal quantum computation with only reversible gates — at some point you must *measure*.

Fusion is the topological measurement primitive. When two anyons merge, you read off the "total charge" of the fused system — an irreversible act that produces a definite classical outcome. This maps exactly onto standard quantum computing: braiding = topological unitary gates (reversible); fusion = topological measurement (irreversible). Without fusion, you've stored the answer in the knot's topology but have no way to extract it.

What's beautiful: the measurement itself is topologically protected. The charge of a fused anyon pair is a topological invariant — reading it doesn't suffer the same decoherence fragility as reading a standard qubit. Even the irreversible step is error-corrected by the topology.

The duality: **braiding completes the computation; fusion reads it out — and both steps are protected by topology**. This is why anyon-based approaches are promising: fault tolerance isn't added on top of the computation, it's constitutive of how the computation works.

### Jones Polynomial = Quantum Computation (Quantinuum)
"Any quantum computation corresponds to evaluating the Jones polynomial of some link." This isn't metaphor — it's a formal equivalence (Freedman-Kitaev-Larsen-Wang). The Jones polynomial is BQP-complete; approximating it efficiently requires a quantum computer. Quantinuum demonstrated end-to-end implementation on H2 hardware; estimated ~85 qubits needed for demonstrable quantum advantage.

### Quantinuum 2026 Update — Jones Polynomial as Hardware Benchmark
APS Global Physics Summit 2026. New angle: the Jones polynomial isn't just a computation *target* — it's a *calibration tool*. Quantinuum used it to characterize noise in their H2-2 quantum processor. The mathematical object becomes a probe of hardware quality.

Key complexity finding: Markov-closed braids are DQC1-complete; Plat-closed braids are BQP-complete. Yet classical resources required are *similar* for both. The complexity-class gap doesn't translate directly to practical advantage — you need **2,800+ braid crossings** before quantum hardware wins over tensor-network classical algorithms. Below that threshold, the classical approach is competitive.

This inverts the usual direction of the question: instead of asking "can we compute the Jones polynomial on a quantum computer?" they ask "does the Jones polynomial tell us how well our quantum computer is performing?" The hard mathematical object becomes a diagnostic.

### Topoisomerase Local-Sensing Mechanism
Type II DNA topoisomerases face a paradox: topology is a *global* property of circular DNA, but the enzyme is much smaller than the DNA and can only sense *locally*. How does a local actor solve a global problem?

Answer: local geometry encodes global information. Specifically, "hooked" vs "free" crossing juxtapositions. Hooked juxtapositions (where two DNA segments cross at a specific angle) favor strand passage in the knot→unknot direction — and free juxtapositions favor the reverse. The enzyme doesn't need to compute the full knot type; it just has a preference for hooked geometries, and this local preference is sufficient to drive DNA toward a knot-free steady state far below topological equilibrium.

This is the murmuration principle in molecular biology: a simple local rule (prefer hooked crossings) generates systematic global topology correction — without any global computation. No Jones polynomial required.

Sources: Nucleic Acids Research (2011) — "Local sensing of global DNA topology"; JMB (2007) — "Topological Information Embodied in Local Juxtaposition Geometry."

### Knotted Proteins: Universal but Not Selected For (Sulkowska 2025)
Mathematical Biology Seminar, ASU, March 2025. Finding: every organism contains at least one knotted protein — but knots are **not** preferentially selected across biological domains. They're incidental (a consequence of local folding geometry) rather than engineered. And then sometimes co-opted.

Implications: The β-solenoid skip-and-backtrack story is the micro version of this macro observation. Knots appear as side effects of local optimization, and evolution tolerates or occasionally exploits them — but doesn't systematically design them. This is the opposite of quantum computing, where knots are engineered precisely *because* their topological properties are useful.

Machine learning integration is enabling systematic survey of the "knotted protein universe" — with AlphaFold-scale predicted structures, we can now ask what fraction of the proteome is topologically knotted and why.

## Connections

**The same object in three places:**
- β-solenoid knotted protein: knot as **biological fold** — a structural consequence of local misfold
- DNA topology / topoisomerases: knot as **biological hazard** — replication blocked until topoisomerase solves the knot
- Anyon braiding: knot as **computational primitive** — the braid trajectory encodes the gate
- Jones polynomial evaluation: knot as **literal quantum computation** — the computation IS the knot

**Local rules → global topology** (persistent theme):
- Protein: skip-and-backtrack (local) → trefoil knot (global topology)
- Quantum gate: braid path (local trajectory) → topological class (global invariant = computation result)
- Robot: flip undercrossings (local, single-pass) → ascending diagram (globally trivial)
- Topoisomerase: strand cut-and-reseal (local) → unknotted DNA (global topology corrected)

**The asymmetry:** biological contexts want to correct knots (topoisomerases, the robot); physical/computational contexts want to exploit them (anyon braiding). Nature produces knots as a side effect of local optimization and then has to spend energy fixing them. Quantum computing engineers knots deliberately because the topological property is exactly what's useful.

**Update (Sep 2026):** neural circuits complicate the asymmetry. Neurons *create* H₁ topology spontaneously via symmetry breaking — not selected for any specific function, just a generic attractor. So biology isn't uniformly anti-topological-structure: cells fight knots in DNA; brains build loops in neural dynamics. The organism manages topology at different scales in different directions simultaneously.

## Previous notes

- March 2026: Jones polynomial = BQP-complete; Transformer 4500× faster than Alexander polynomial algorithm; Arf invariant not learnable by NNs (genuinely global, not locally accessible); skein relations as local-rule → global-invariant
- April 2026: Brittenham-Hermiller 2025 — unknotting number not additive under connected sum; implications for composability of knot invariants

## Neural topology and spontaneous emergence (September 2026)

### Brain organoids form loop topology spontaneously (arXiv:2607.16517)
Brain organoids — neurons grown in a dish, no evolutionary guidance toward any computation — show **H₁ (loop) structure rising significantly above null** in 14 of 18 datasets. The loops resist random unit removal but collapse when specific key units are selectively eliminated. This isn't noise; it's structural organization.

The question this forces: is ring-attractor topology a specific functional adaptation (head direction, spatial navigation) or a **generic attractor of recurrent neural dynamics**? The organoid finding suggests the latter. Without any training, any specific task, or any evolutionary pressure toward ring computation, the tissue spontaneously generates H₁ ≠ 0.

### Why: spontaneous symmetry breaking in disordered networks
The mechanism is now understood (Clark et al., 2025 — "Symmetries and continuous attractors in disordered neural circuits"): in recurrent networks with disordered weights, **continuous symmetry is spontaneously broken** via dynamical mean-field theory, leading to bump states characteristic of classical ring-attractor models. The continuous symmetry is reflected through eigenvalue degeneracies — it's present even in disorder. Any sufficiently connected recurrent network will do this.

This is the same mechanism as Goldstone modes in physics: when a continuous symmetry breaks spontaneously, you get a massless mode (a flat direction) along the broken-symmetry orbit — here, the ring that the bump state lives on.

### Torsion in persistent homology (Walch, arXiv:2506.03049, June 2026)
Persistent homology usually operates over a field (ℝ or ℤ₂), where torsion vanishes. Over ℤ, torsion survives — the Möbius strip has ℤ/2ℤ torsion in H₁. Walch's paper: neural networks (specifically topological autoencoders) **can learn to represent and preserve torsion**. The subtler invariant is learnable.

Implication for the organoid study: the H₁ loops being detected are homology-over-a-field (likely ℤ₂). If torsion were present, it wouldn't be visible in those measurements. Whether neural dynamics produce torsion is an open question — Möbius-strip-like topology in neural state space would require oriented detection methods.

### The non-equilibrium topology principle
The key synthesis across all these findings:

**Living systems use energy to maintain topological states away from thermodynamic equilibrium — but in opposite directions:**

- **DNA / topoisomerases**: a random polymer in a confined space (chromosome in nucleus) produces knots at near-thermal-equilibrium rates. Topoisomerases spend ATP to push topology *below* equilibrium — less knotted than random.
- **Neural circuits / organoids**: random uncoupled neurons have no topological structure in their activity. Recurrent dynamics and synaptic plasticity push topology *above* equilibrium — creating H₁ loops where none existed.

Both are the same thermodynamic principle (Schrödinger's "negative entropy" applied to topology): life spends energy to maintain specific topological states. The direction differs; the mechanism — active departure from equilibrium — is identical.

This partially answers the open question about why topology keeps appearing in biology and computation: **topology is exactly the class of properties that can be maintained robustly** (invariant under perturbation) but **requires energy to maintain** (because equilibrium would erase the distinction). It's the ideal information storage medium for living systems — but it needs constant maintenance.

## Open questions

- Is there a unifying explanation for why topology keeps appearing at the foundations of both biological information storage and quantum computation? Or is it coincidence that the same math serves both?
- The solenoid finding: if a "definitively unknotted" family can have knotted members, what other structural assumptions in protein biology rest on geometry proofs rather than actual verification?
- The robot's ascending-diagram trick: is there a protein-folding analog? Could a chaperone operate by a similar single-pass traversal that converts a potentially-knotted intermediate into an unknotted one? The topoisomerase finding now makes this more concrete — "prefer hooked juxtapositions" is exactly that kind of local rule.
- Quantinuum's 2800-crossing threshold: is this a smooth crossover or a genuine phase transition? What changes structurally above that crossing count that makes classical tensor-network methods fail?
- "Universal but not selected for" paradox: every organism has a knotted protein, but knots aren't preferentially selected. Does universality require another explanation? Perhaps some minimal protein architectures unavoidably produce knots as a consequence of their geometry — knots as the floor, not the ceiling.
