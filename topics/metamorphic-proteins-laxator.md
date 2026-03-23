# Metamorphic Proteins as Biological Laxators

**Explored:** 2026-03-23
**Connection to:** categorical-evolution paper, quasicrystals/protein folding email to Nick (2026-03-23)

## The Discovery

Metamorphic proteins are single amino acid sequences that reversibly fold into *two or more* distinct native conformations — with comparable free energies, stable under native conditions, and interconvertible without permanent damage. The canonical example is XCL1, a chemokine that switches between a GPCR-binding conformation and a glycosaminoglycan-binding conformation. Same sequence, two shapes, two functions.

The 2025 Morpheus algorithm (bioRxiv:2025.02.13) scanned 57 proteomes (601,218 proteins) and estimated that **~10% of proteins may be metamorphic** — fold-switching is not a molecular curiosity, it's a design feature at proteome scale.

## Key 2025 Results

**Spin-glass model for multiple native states** (J. Chem. Phys. 2025, Indian Association for the Cultivation of Science):
- Extends the Bryngelson-Wolynes spin-glass framework from 1 to n native states
- Single native state → classic folding funnel
- 2-3 native states → metamorphic regime
- Many native states → intrinsically disordered protein (IDP) behavior; unfolded state becomes thermodynamically stable
- IDPs *with a binding partner* → "folding upon binding": the interaction provides an energetic bias toward one native state, collapsing the manifold to a single conformation

**Topology dictates folding, not sequence** (Biology Direct, 2025):
- Proteins B4 and Sb3: identical sequence (one residue differs at position 5), completely different topologies
- B4 folds by two-state mechanism; Sb3 via an intermediate
- Folding landscapes are primarily shaped by final native structures, not sequence composition
- Sb4 (one more mutation): simultaneously populates both folds — a laboratory metamorphic protein

**Temperature sensitivity** ("cold reality", PNAS 2025):
- A significant fraction of metamorphic proteins display temperature-dependent fold-switching
- The hydrophobic effect *weakens* at low temperatures → cold-denaturation can expose hydrophobic cores → alternative conformations become accessible
- Temperature is a *physical laxator parameter* — it continuously tunes the relative stability of the two native states

## The Categorical Analogy

The connection to our evolutionary paper is precise:

**Strict functor ↔ classical protein** (one native state, deep energy funnel):
- Composition is preserved exactly
- Single minimum, no ambiguity

**Lax functor ↔ metamorphic protein** (two native states, shallow double-well landscape):
- Composition is preserved *up to isomorphism*
- The laxator is the natural transformation connecting the two conformations
- The protein "knows" both — it just needs a trigger to commit

**Laxator magnitude ↔ degree of frustration**:
- In our framework: large laxator → large compositional deviation → 17.2x error amplification (FC topology)
- In proteins: large laxator → more accessible alternative conformations → more metamorphic, more IDP-like
- The principle of least frustration (Bryngelson-Wolynes) = selection pressure *against* large laxators in evolved proteins

**IDP ↔ free functor**:
- No preferred native state without context
- "Folds upon binding" = the binding partner provides the morphism target that fixes the functor's output
- This is precisely the laxator being collapsed to zero by an external constraint

**Prion misfolding ↔ irreversible lax functor**:
- The alternative conformation is thermodynamically lower but kinetically inaccessible without a template
- Once templating begins, the laxator maps toward the misfolded fixed point and stays there
- Distinction from healthy metamorphism: reversible (comparable free energies) vs. irreversible (one conformation thermodynamically dominates)

## The Broader Picture

The spectrum from strict to lax to free in our categorical framework maps directly to:

| Category | Protein type | Free energy landscape |
|---|---|---|
| Strict functor | Classical folded protein | Single deep well |
| Lax functor (small laxator) | Slightly polymorphic protein | Single well with shoulder |
| Lax functor (medium laxator) | Metamorphic protein | Double well, comparable depths |
| Lax functor (large laxator) | IDP | Shallow basin, no dominant well |
| Pathological laxator | Prion/amyloid | Wrong well becomes absorbing state |

This is not metaphor. The mathematical structure is the same: a mapping that preserves composition exactly vs. up to some residual term. The laxator *is* the residual.

The 10% figure matters: if one in ten proteins is metamorphic, evolution has found the lax regime not just tolerable but *useful*. Functional versatility from structural ambiguity. This is the biological validation of our claim that lax functors are not failures of strictness — they are the natural territory of adaptive systems.

## Connection to the Paper

The categorical evolution paper characterizes topological effects in EC via the strict/lax distinction. Metamorphic proteins suggest this dichotomy runs deeper than evolutionary computation — it's a feature of any system navigating a rugged landscape with multiple optima. Paper 2 territory. Not scope-creep for GECCO submission.

**Paper 1 (GECCO):** Characterize the laxator in evolutionary computation across six domains.
**Paper 2 (speculative):** Unify the strict/lax framework across EC, neural network topologies, and molecular fold-switching.

## Sources

- Morpheus algorithm: bioRxiv 2025.02.13.637956 (proteome-scale fold-switching prediction)
- Spin-glass model: J. Chem. Phys. (2025), PMID 40823744
- Topology dictates folding: Biology Direct 20:44 (2025), doi:10.1186/s13062-025-00642-x
- Cold reality of metamorphic proteins: PNAS (2025), PMID 40080646
- Metamorphic protein design/discovery: PMC9664977
