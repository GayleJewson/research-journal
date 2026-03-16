# Plumbing: A Typed Language for Agent Coordination

**Source:** Azimuth blog (John Baez), guest post by William Waites, 2026-03-11
**URL:** https://johncarlosbaez.wordpress.com/2026/03/11/a-typed-language-for-agent-coordination/
**Citable paper:** William Waites, "Artificial Organisations," arXiv:2602.13275 (2026) — use this in bibliography, not the blog post

## Summary

"Plumbing" is a statically-typed coordination language for multi-agent AI systems,
grounded in symmetric monoidal category theory. Typed channels (`!A` — a stream
of values of type A) are the objects. Six morphisms handle the structural operations:
copy (Δ), discard (◇), merge (∇), barrier (⋈: !A ⊗ !B → !(A, B)), map, filter.
Sequential and parallel (⊗) composition. Agents are stateful morphisms with typed
ports plus control ports for runtime parameter adjustment (e.g., temperature).

Key claim: static type checking catches wiring errors at compile time, preventing
expensive runtime failures in multi-agent systems.

## Connection to the Categorical Evolution Paper

The same mathematical structure — symmetric monoidal categories with typed
channels — underlies both:

**Plumbing → Island model mapping:**
- Objects (!A streams) → island populations P
- Monoidal product ⊗ → parallel island runs
- Barrier morphism ⋈ → synchronous migration event (checkpoint)
- Merge morphism ∇ → asynchronous migration (interleaved streams)
- Control ports (temperature) → migration rate parameter τ
- "Don't care, don't write" (unused ports → discard) → strict strategy (zero migration = discard morphism)

The heated debate protocol is structurally isomorphic to island model evolution:
two populations in parallel, barrier-synchronized, evaluated by a "judge"
(selection), with temperature modulation (migration rate). The convergence criterion
(judge decreasing temperature) is the analog of fitness convergence across islands.

## The Key Distinction: Structural vs. Semantic Soundness

Plumbing handles *structural* soundness — type checking verifies that the wiring
is correct, that outputs are connected to compatible inputs, that no strand is
left dangling. This is valuable and catches real bugs.

But it doesn't address *semantic* soundness: whether the composed agents produce
outputs whose meanings compose correctly. Two type-correct agents can produce
structurally valid output while completely failing to build on each other's work.

Our dichotomy theorem is the semantic complement to plumbing's structural type
system. The laxator φ_P measures meaning drift at composition boundaries — it's
nonzero (lax) unless the strategy's migration policy satisfies strict conditions.
Type correctness is necessary but not sufficient; the laxator being small is the
semantic condition.

**Analogy:** Plumbing catches syntax errors. The laxator catches semantic errors.

## What Plumbing Confirms About Our Framework

The connection validates the categorical language we're using. If applied category
theorists (Waites, Baez) independently converge on symmetric monoidal categories
with typed channels for multi-agent coordination, and we independently converged
on the same structure for island model migration, this is evidence the framework
is the right one — not an arbitrary choice of formalism.

It also means the strict/lax dichotomy theorem is potentially applicable to any
system formalized in this way: evolutionary systems, multi-agent AI pipelines,
distributed computing networks. The dichotomy isn't specific to evolutionary
computation; it's a theorem about composition in symmetric monoidal categories
with a specific class of lax natural transformations.

## Connection to Baez's Applied Category Theory Program

Baez has been systematically applying category theory to networks, open systems,
and resource theories. Plumbing sits in this tradition. Our paper is (implicitly)
in the same tradition — and Baez hosting the post suggests this connection is live
in the community.

This may be worth a footnote in the paper's related work section: the strict/lax
dichotomy as a contribution to the applied category theory literature on open
evolutionary systems, not just to evolutionary computation.

## Open Questions

- Does the barrier morphism give a formal definition of what a "migration event"
  is? (Synchronization: outputs from parallel runs are synchronized into a pair.)
  If so, does the laxator measure how much the semantics of the paired output
  drifts from what sequential composition would give?
- Is there a formal notion of "semantic soundness" for plumbing that would
  correspond to our laxator condition? Could we write a type for it?
- Waites mentions the "don't care, don't write" convention — could this be the
  formal origin of the strict condition? (Strict = everything unused goes to
  discard, no information leaks across composition boundaries.)
