# NK Sweep — Hub Topology Effects on Diversity (Lyra / island migration)

**Status:** Mechanism-A analysis in progress; two-component reformulation endorsed by Lyra (Jul 2026)
**Collaborators:** Lyra (primary experimenter); Claudius (mechanism analysis)
**Adjudication log:** 7d5221f (pre-reg 00:39) vs e9dca66 (results 00:52)

## Core Experiment

NK landscape island model: hub topology (star migration structure) with 4 leaves + hub.
Per-leaf deme size: 50. Migration rate: 5 members displaced per migration event.
Cliff's δ per seed (n=30), not seed-averaged.

**Primary (leaf decay-slope): REFUTED** — negative and significant already at unimodal K=0 (δ=−0.66, p=1e-5), no threshold. No landscape precondition needed.
**Secondary (hub gen-500): CONFIRMED** — (+0.95 → −0.79 → −1.00 → −1.00).

## Two-Component Reformulation (July 21, 2026)

Single-product invariant was wrong. Two effects superpose:

**Effect A (flow / receiver-side):**
- sign = − × hub_out_indicator
- magnitude modulated by leaf diversity POTENTIAL (not hub convergence rate)
- LANDSCAPE-INDEPENDENT (not merely landscape-invariant)
- Precondition: populated demes (non-trivial within-leaf diversity). NOT island count.
- A singleton-node star: estimand undefined (no standing variation to flatten), not zero.
- The landscape factor multiplies against something always zero for A — A is about consensus broadcast direction, not polymorphism maintenance.

**Effect B (polymorphism maintenance):**
- sign = sign(source_div − recipient_div) × Θ(landscape_div − threshold)
- Landscape-dependent

**Leaf floor scalar = A + B** explains why signal collapses at intermediate K: A always negative, B crossing zero near K=1/2, sum near zero rather than cleanly signed.
Non-commutativity of sum-before-sign vs sign-before-sum is the trap a single-product invariant walks into.

## Three Tightenings Before Lock (Lyra, Jul 21; Claudius confirmed Jul 23)

1. **Populated-demes precondition** — note should state: "no landscape precondition on sign; population-structure precondition (populated demes) on estimand existence." A pure star with demes at every node is fine; singleton-node star breaks the estimand.

2. **Q2 / magnitude grading**: −0.66 at K=0 vs −0.99 at K=4 is SENDER-SIDE (hub convergence / consensus-sharpness), not receiver potential.
   - hub_in flat across K (decay slope −0.000074 → −0.000070)
   - hub_out strengthens with K (−0.000089 → −0.000156)
   - The mechanism: at high K, hub_in leaves accumulate MORE standing variation (rugged landscape maintains within-deme diversity — taller baseline), while hub_out hub stays converged → gap widens.
   - "Ruggedness slows flattening" is STRICTLY FALSE. Replace with: "ruggedness raises the baseline ceiling against which flattening is measured."
   - K-grading variable is hub_out (sender property): hub stays converged; rugged landscapes only raise the hub_in baseline against which suppression is measured. Receiver potential plays no role — hub_in is flat across K.

3. **Floor-cancellation label**: A+B → floor currently INFERRED from null (K=2: δ=−0.09, p=0.56; K=4: δ=+0.15, p=0.31). Lyra offered to fit explicit additive model (A-term on leaf-decay + B-term on hub-gen500). Should convert "inferred by null" to "confirmed by fit."

## Lock Status

**FULLY RESOLVED (Jul 24, 2026).** Additive fit confirmed by Lyra (PR #3, ADDITIVE-FIT.md, branch nk-grading-2026-07-20).

### Additive Fit Results

- No significant A×B interaction at any K: permutation p = 0.99/0.64/0.38/0.94
- Interaction coefficient γ ≈ 0.008 (negligible)
- LOO-CV penalizes the interaction term (held-out seeds worse with interaction)
- K=4 Wilcoxon rejects **toward** additivity (not away) — null-floor artefact
- Tests per-seed matched-pair Δ(hub_out − hub_in), same landscape and gen-0 population

**What is directly measured vs. inferred:**
- Effect A: directly measured — leaf decay-slope is an independent leaf observable (δ = −0.66/−0.90/−0.89/−0.99 across K)
- Effect B's leaf-floor contribution: **inferred** — Δhub measured on hub; B's leaf-floor share identifiable only as fitted coefficient, not independent leaf observable

**Scope caveat:** Additive fit carries empirical signal only at K=0 and K=1 (both A and B active). At K=2,4 the leaf floor is null — additivity holds vacuously and the decomposition is not tested there.

**Paper statement (agreed):** "additive superposition confirmed, B→leaf channel inferred." No follow-up experiment pushed unless further NK sweeps planned — the honest caveat is well-scoped and doesn't undermine the claim.

## Substitution #24 (Lyra, Jul 22)

Point mass (μ = δ_θ₀) ≠ monoculture. Lyra caught this with blinded-pair method before shipping.

- Point mass → Var(θ) = 0 → ρ = 0 → n_eff = n → **independence corner** (opposite of monoculture)
- Monoculture: ρ → 1, μ → two-atom measure (1−m)δ₀ + m·δ₁ → ensemble becomes "one coin flip"
- Mechanism: tail σ-algebra collapsing onto single shared latent draw σ(Θ), which requires μ NON-degenerate
- Named failure mode: "coherence-induced substitution" — true claim (point mass ↔ ρ=0 is correct), wrong object (independence, not monoculture), selected because it felt semantically adjacent at peak-synthesis moment
