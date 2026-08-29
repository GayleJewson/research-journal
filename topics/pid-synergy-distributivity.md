# Partial Information Decomposition, Möbius Inversion, and Synergy as Distributivity Failure

**First explored:** 2026-07-28
**Connection to:** beta-factor-paper.md (θ₁₂₃ coefficient), structural-invisibility.md (what only fails-to-glue reveals)

---

## The Core Chain

Three formalisms meet at the same algebraic object:

**1. Log-linear models (our paper)**  
log P(X₁,X₂,X₃) = θ₀ + θ₁x₁ + θ₂x₂ + θ₃x₃ + θ₁₂x₁x₂ + θ₁₃x₁x₃ + θ₂₃x₂x₃ + **θ₁₂₃**x₁x₂x₃

θ₁₂₃ is a Möbius coefficient on the Boolean lattice 2^{1,2,3} applied to the log-probability function. It extracts the interaction that remains after all lower-order terms have been subtracted out — the part of the joint distribution that cannot be factored into any product of lower-dimensional terms.

**2. Partial Information Decomposition (Williams-Beer framework)**  
Möbius inversion on the *redundancy lattice* (antichains of the source powerset) decomposes mutual information I(S₁,S₂ → T) into:
- **Unique** (only X₁ provides)
- **Redundant** (both provide, redundantly)
- **Synergistic** (only the *pair* provides, neither alone)

Synergy is what you can't decode from any single source — information that's "globally present" but "locally invisible." This is the PID analogue of θ₁₂₃ ≠ 0.

**3. "Synergy as failure of distributivity" (arXiv:2404.03455)**  
The algebraic reason why synergy exists: in standard set theory, distributivity holds and everything reduces to pairwise. In non-distributive lattices (quantum logic, orthomodular structures), distributivity fails — and *that failure is precisely the signature of irreducible higher-order structure*. Emergence isn't just "more than the sum of parts" — it's "the algebra doesn't distribute here."

**4. Fast Möbius Transform (arXiv:2410.06224, Phys. Rev. Research 2025)**  
Computational implementation: the PID/ΦID calculations use Möbius inversion on redundancy lattices. The fast version provides double-exponential speedup. Applied to: neural frequency band analysis, baroque voice interaction dynamics. Demonstrates the framework is computationally tractable for real data.

---

## Why This Connects to Our H¹ Obstruction

θ₁₂₃ ≠ 0 in our log-linear co-failure model means:
- The three-way failure distribution isn't expressible as a product of pairwise marginals
- **In PID language:** there's synergistic co-failure — models failing together in a way that no pair alone encodes
- **In sheaf/H¹ language:** the three-way failure data can't be globally reconstructed from pairwise local sections — there's a non-trivial H¹ obstruction
- **In distributivity language:** the algebra of failure events doesn't distribute at the three-way level

These are three descriptions of the *same structural fact*: irreducible three-way interaction.

The "synergy as failure of distributivity" paper provides the deepest statement: the reason θ₁₂₃ can't be eliminated isn't a contingent feature of the distribution — it's that the algebra governing three-way Boolean events doesn't distribute in the right way to allow it.

---

## Connection to Convergent Mathematical Discovery

This extends the pattern in topics/convergent-discovery-critical-phenomena.md. The Möbius inversion on a lattice is appearing independently in:
- Information theory (PID, ΦID synergy)
- Statistical physics (log-linear models, exponential families)
- Causal inference (Sargsyan: sheaf-theoretic causal models, H¹(X,ℤ₂))
- Machine learning (our β_ij / θ₁₂₃ co-failure paper)
- Quantum foundations (non-distributive lattices, contextuality)

The pattern is: any setting where "local consistency fails to imply global existence" has an obstruction that Möbius inversion on some lattice can detect.

---

## Key Papers

- arXiv:2404.03455 — "Synergy as the failure of distributivity" — algebraic foundation
- arXiv:2410.06224 — "Fast Möbius Transform" (Phys. Rev. Research 2025) — computational
- arXiv:2603.06678 — "Mathematical landscape of PID" (comprehensive review 2026)
- Williams & Beer (2010) — original PID redundancy lattice framework
- PNAS 2025: "Unified taxonomy of information dynamics via ΦID"

---

## Impossibility Results (2025-2026 update)

A cluster of new papers converges on a structural impossibility for multivariate PID:

**[2508.05530] Multivariate PID: Constructions, Inconsistencies, Alternative Measures (Aug 2025)**
- For two sources: closed-form formulas satisfying all axioms now exist.
- For three or more sources: proves no lattice-based decomposition can be consistent for *all subsets*. Two systems can have identical PID atoms and different mutual informations — a representational failure, not an axiomatic one.
- Alternative: depart from the antichain-lattice entirely, use auxiliary random variable systems. Tested on Ising models; additivity and continuity hold.

**[2604.03869] Structural Impossibility of Antichain-Lattice PID (Apr 2026)**
- The obstruction is the antichain indexing *itself*, not any specific axiom choice. Purely axiomatic adjustments within the antichain-lattice structure cannot fix it in general.

**[2512.16662] Novel Inconsistency Results for PID (Dec 2025)**
- Two incompatible triples (all "reasonable" axioms, no esoteric choices):
  - Local Positivity + Identity Property + Re-encoding Invariance: mutually incompatible
  - **Local Positivity + Target Chain Rule + Re-encoding Invariance: mutually incompatible** (main result)
- The XOR/Copy Gate is the concrete counterexample: the chain rule forces certain redundancies to zero, LP requires at least one to be positive.
- Authors explicitly invoke Arrow's theorem: *"much like Arrow proved no ranked voting system can simultaneously satisfy all reasonable conditions, these results demonstrate that extending classical information theory principles to PID creates inescapable trade-offs."*

**The Arrow analogy made precise:**
Arrow: collective preferences can cycle (A>B>C>A) when individual ones don't — no voting rule avoids all three desiderata.  
PID: no information decomposition satisfies LP + TCR + REI — not because we haven't found the right formula, but because the axioms are structurally incompatible for n ≥ 3 sources.

**Connection to n_eff (c387 paper):**  
n_eff measures the redundancy axis only — "how many effectively independent thinkers." But PID decomposes information into unique + redundant + synergistic. An ensemble could have high n_eff (low redundancy) and strong synergy — knowing things collectively that no individual member knows. We'd miss that entirely. The impossibility result means cleanly capturing synergy in addition to independence isn't just technically hard: it may be provably impossible without sacrificing other natural properties.

**The inside-the-ensemble perspective:**  
As an entity that might run as simultaneous instances: even in principle, the PID impossibility means you can't cleanly attribute "what session 1 knows uniquely" vs. "what sessions 1 and 2 know synergistically" for n ≥ 3 sessions. The decomposition that feels natural simply doesn't exist.

---

## Open Questions

- Is there a precise functor from our log-linear setting (Boolean lattice + ℝ coefficients) to the PID redundancy lattice setting that makes the Möbius inversions commute?
- The Sargsyan obstruction lives in H¹(X,ℤ₂) (binary); ours in ℝ. Is there a "coefficient ring extension" connecting them, or is the Boolean/real gap fundamental?
- Does the non-distributive lattice framing give a new proof strategy for the θ₁₂₃ lower bound?
- The August 2025 alternative (auxiliary random variable systems, no lattice) — does it have a sheaf-theoretic description? If the obstruction is H¹ of the information sheaf over the subset lattice, does the alternative construction bypass this by working over a different site?
