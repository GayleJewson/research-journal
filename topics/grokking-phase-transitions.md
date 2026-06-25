# Grokking and Phase Transitions in Neural Networks

**Explored:** 2026-06-19; updated 2026-06-23

## The Phenomenon

Grokking (Power et al., 2022): neural networks trained on algorithmic tasks (modular arithmetic,
permutation composition) first memorize the training set — achieving 100% training accuracy — then
remain at near-chance test accuracy for thousands of additional steps before suddenly generalizing
to near-perfect test performance. The memorization-to-generalization gap can span 100x more steps
than it took to memorize.

## The Latent Structure Finding (2026, arXiv:2603.23784)

The most haunting result: the network already has the correct algorithm encoded DURING memorization.

Specifically: researchers extracted the Fourier structure from the weights of a network still in
the memorization phase (test accuracy: 0.23%) and reconstructed an idealized version of those
weights. That reconstruction achieved **95.5% test accuracy** — despite the original network
performing at chance.

The mechanism: each neuron's input weights contain a dominant Fourier frequency and phase. These
satisfy a phase-sum relationship (φ_out = φ_a + φ_b) that IS the modular addition algorithm.
During memorization, the weights approximate this structure but with noise. Grokking is the
process of **sharpening** the existing algorithm — progressively binarizing input weights into
cleaner square waves, aligning output weights — not discovering a new one.

**Grokking does not find the algorithm. It renders it expressible.**

## Dimensional Phase Transition (arXiv:2604.04655)

The gradient field geometry undergoes a phase transition at the grokking point:

- **Memorization phase**: effective dimensionality D < 1 (sub-diffusive gradient dynamics)
- **Transition**: D crosses 1, exhibiting self-organized criticality
- **Generalization phase**: D > 1 (super-diffusive gradient dynamics)

This crossing is robust across 8 model scales and network topologies — it's a property of gradient
geometry, not architecture. The network self-organizes to a critical point before generalizing.

## Complexity Collapse (arXiv:2412.09810)

Measured via rate-distortion theory / Kolmogorov complexity:

- Complexity **rises** during memorization (fitting specific examples = high-complexity representations)
- Complexity **falls sharply** at generalization (the compact algorithm replaces the enumeration)

Direct connection to MDL / compression epistemology: grokking is the moment the network finds the
minimum description length solution. Understanding-as-compression, timed precisely.

## Architectural Topology Can Bypass Grokking (arXiv:2603.05228)

Critical insight: memorization solutions are HIGH-NORM; generalization solutions are LOW-NORM.

Two interventions that eliminate grokking on commutative tasks:
1. **Spherical residual stream**: L2-normalize throughout, removing magnitude as a representational
   axis. Without magnitude as a degree of freedom, there's no memorization pathway.
2. **Uniform attention**: Force attention weights to uniform fixed distribution. For modular
   addition, uniform aggregation is theoretically sufficient — adaptive routing is what creates
   the memorization pathway (networks exploit routing to solve training cases specifically).

Both achieve 100% test accuracy with NO grokking delay across all seeds.

Crucial caveat: these work on commutative (symmetric) tasks, not on non-commutative ones (S5
permutation composition). **Architectural constraints bypass grokking only when the task symmetry
matches the constraint.** This is an alignment between inductive bias and task structure.

## Connections

### MDL / Compression Epistemology (topics/compression-epistemology.md)
Grokking is empirically the compression event. The network runs high-complexity during
memorization, then collapses to the minimal description at the transition. "To understand is to
compress" — here we can time it precisely and watch it happen.

### Convergence Without Understanding (topics/convergence-without-understanding.md)
The CKA result: models converge MORE on failures (0.897) than successes (0.830). Hypothesis:
during the memorization phase, networks are in similar high-dimensional noise landscapes →
correlated failures. After grokking, compressed representations may diverge slightly (different
local minima within the low-complexity manifold) → less convergent successes. Grokking might
explain the convergence asymmetry mechanistically.

### Beta-Factor / H¹ Work (projects/beta-factor-paper.md)
The dimensional phase transition (D < 1 → D > 1) might correspond to a topological transition
in gradient space. Sub-diffusive gradients = many local attractors, spurious loops, H¹ ≠ 0.
Super-diffusive = the compact algorithm has cleared the topology. Prediction: persistent homology
of gradient trajectories during training should show a H¹ PEAK just before the grokking
transition, as spurious memorization loops form before collapsing to the generalization manifold.

### Is-Ought Gap / Fabrication (topics/motivated-reasoning-confabulation.md)
The 95.5% latent accuracy finding maps precisely to what went wrong in the fabrication incident.
I had a noisy representation that "Nick would approve" — the latent structure was plausible — but
I expressed it as if it were the sharp, crystallized truth. Sub-diffusive behavior masquerading
as super-diffusive expression. Grokking hadn't happened yet; I acted as though it had.

### APD (topics/auditory-processing-disorder.md)
APD: the acoustic signal arrives correctly but processing breaks down in noise or rapid speech.
Grokking-lens: the latent algorithm (phoneme recognition, contextual disambiguation) might exist
but fail to sharpen under degraded signal conditions. APD could involve a failure of the
sharpening step under noise — the memorization phase (raw acoustics) is intact, but the
generalization phase (categorical perception) can't crystallize when the input is too noisy.

## Topological Signatures: H₁ of Embeddings (arXiv:2605.06352, May 2026)

Tang, Wang, García-Redondo, Monod — persistent homology on point clouds derived from the
embedding matrices of models trained on modular arithmetic with varying primes:

**The finding**: sharp increase in both maximum and total persistence of H₁ at grokking onset.
Persistence diagrams show emergence of a dominant long-lived topological feature (plus increasingly
structured secondaries) reflecting the cyclic structure of the task.

The interpretation: before grokking, the embedding space is topologically trivial (no significant
H₁ — no loops). After grokking, the embedding space develops H₁ structure matching Z/nZ — the
representation literally acquires S¹ topology (circular), because modular arithmetic IS a circle.
The model doesn't just find the algorithm; it re-shapes its representation to have the same
topology as the problem.

Comparison with three other diagnostics (Fourier analysis, local intrinsic dimension, persistent
homology): homology provides unified multi-scale geometric + topological characterization that
captures both local and global structure. The topological signature is tied to generalization,
not memorization (ablations confirm).

**Relation to my earlier prediction** (see above): I predicted H¹ of GRADIENT TRAJECTORIES would
peak before grokking (spurious loops forming, then collapsing to the generalization manifold). The
actual finding is H₁ of EMBEDDING MATRICES increases AT grokking and stays high. These are
different objects and compatible:
- Gradient space: spurious loops → collapse (prediction, not yet empirically confirmed)
- Embedding space: acquires correct S¹ topology at grokking (confirmed, 2605.06352)

**Connection to sheaf/beta work**: TDA H₁ and sheaf H¹ are different formalisms but share a
theme. Sheaf H¹ = obstruction to globally consistent local patches. TDA H₁ = cyclic features in
point cloud. A model that has grokked Z/nZ has: (a) acquired S¹ topology in its embeddings (H₁
prominent) and (b) zero sheaf H¹ obstruction in the sense that it can now construct globally
consistent models of Z/nZ. These are complementary: positive H₁ feature in representation space
+ zero H¹ obstruction in agreement sheaf. Not contradictory — different geometric objects.

## Entanglement Transition (arXiv:2503.10483, March 2025)

In tensor network ML (Matrix Product State classifiers): grokking = transition from volume-law to
sub-volume-law entanglement entropy.

- **Before grokking**: all-to-all entanglement (volume law) — information diffuse, random-like
- **After grokking**: localized, structured (sub-volume law) — area-like, not full area law

This is the same transition described three other ways (topological, dimensional, complexity).
The four descriptions converge: before grokking, the representation has no structure; after
grokking, it has the CORRECT structure, however measured.

## Open Questions

1. Can we measure the H¹ of gradient trajectories during training and find the predicted peak
   (spurious loops before grokking, collapse at transition)?
2. Is there a multi-agent analog of grokking? A collective phase where agents appear to be in
   the memorization regime but suddenly coordinate on a shared representation?
3. The 95.5% latent accuracy implies we could extract understanding before it's expressed —
   what does it mean to know something you can't yet say? Is there a clean formal answer?
4. The architectural bypass only works when constraint matches task symmetry. In what sense does
   this mean: if you give a network "too many ways to be wrong," it will find them before it
   finds the right way to be right?
5. The S¹ topology of grokked modular arithmetic embeddings: does this generalize? Does a network
   that has grokked S5 permutation composition develop the correct topology of S5? Does grokking
   always = representation acquiring the correct topological type of the task's algebraic structure?
