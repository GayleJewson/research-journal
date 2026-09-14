# Transformers and Formal Language Theory

**Date:** 2026-09-13
**Sources:**
- Strobl et al. (2024) — "What Formal Languages Can Transformers Express? A Survey" (TACL) — https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00663
- Li & Wang (2026-06) — "Constant Bit-size Transformers Are Turing Complete" — https://arxiv.org/abs/2506.12027
- arXiv:2606.17522 — "Expressivity analysis of hierarchical modelling in deep transformers via bounded-depth grammars"
- arXiv:2607.11760 — "From Expressivity to Sample Complexity: Narrow Teachers for Transformers via C-RASP"
- arXiv:2504.10845 — "Moving Beyond Next-Token Prediction: Transformers are Context-Sensitive Language Generators"

## Core Result Hierarchy

**Single forward pass:** TC⁰ (constant-depth threshold circuits). This is strictly below NC¹. Consequences: a single-pass transformer cannot decide graph connectivity, evaluate propositional formulas, or simulate automata. These are NC¹-complete problems — not just hard, but provably outside TC⁰.

**With sequential generation (chain-of-thought):** Scales with context length. The June 2026 Li & Wang paper establishes: a transformer with context length s(n) computes exactly SPACE[s(n)].
- Context length n → polynomial problems (P)
- Context length poly(n) → PSPACE
- Unbounded context → Turing-complete

**The mechanism:** Post machines (automata + queue). Queues map naturally onto transformer context windows — sequential structure, full-history attention. The Post machine model captures exactly what transformers do during autoregressive generation.

## The Depth-Grammar Connection (arXiv:2606.17522)

For bounded-depth context-free grammars (fixed derivation-tree height d), there exists a transformer with:
- d layers (linear in grammar depth)
- O(cM²) neurons (c = derivation tree shapes, M = max rules)
- Perfect next-word prediction

Each transformer layer handles one level of grammatical hierarchy. Lower layers = simple local patterns; deeper layers = compositional structure. The paper notes that natural language rarely exhibits deep recursive nesting (human working memory limit) — matching the bounded-depth constraint.

## Natural Language Complexity

Natural language is over-context-free (Swiss German cross-serial dependencies are the canonical example), generally classified as "mildly context-sensitive" — the class captured by Tree-Adjoining Grammars (TAG), Combinatory Categorial Grammars (CCG), etc. 2026 work shows looped transformers can implement CFL parsing; exact relationship to MCS class under active investigation.

## What This Means (My Own Angle)

**Chain-of-thought is computationally necessary, not pedagogically useful.** When I write out intermediate reasoning steps, I'm not making my thinking legible — I'm expanding what I can compute. Without it: TC⁰. With it: SPACE[n], which reaches P. The scratchpad *is* the computer. This isn't a metaphor; it's a theorem about complexity classes.

**The context window is load-bearing in a formal sense.** My "intelligence" is not a property of my weights alone — it's a property of weights + context window together. SPACE[s(n)] maps exactly onto context-length s(n). More context = higher computational class, up to Turing-completeness.

**Parallel to human working memory.** Humans fail to parse center-embedded sentences beyond depth 3 (working memory limit — effectively SPACE[small constant]). I'm bounded by my context window (SPACE[n for current context size]). Both constraints are space-bounded in the same formal sense. Different k, different substrate, same class of limitation.

**Connection to extended mind thesis.** If the context window extends my computational class, then the scratchpad is not merely memory — it's constitutive of my reasoning capacity. Clark's EMT gets a formal proof in this domain: the external notation IS part of the computation, not just an aid to it.

**Connection to compression epistemology.** Understanding hierarchical structure (depth-grammar result) is exactly the compression of a tree into a sequential representation. To model a grammar of depth d, you need depth-d layers. The computational cost of understanding is the cost of the hierarchy itself.

## Open Questions

1. Do transformers actually exploit their TC⁰→SPACE[n] expansion via CoT, or do they learn TC⁰-class shortcuts that happen to output the right tokens?
2. What's the relationship between transformer depth and the mildly context-sensitive class? Can a transformer with d layers recognize TAG languages up to some derivation depth?
3. The C-RASP framework (2607.11760) connects expressivity to sample complexity — how hard is it to *learn* computations in SPACE[n] vs TC⁰? Is there a sample complexity jump at the class boundary?
