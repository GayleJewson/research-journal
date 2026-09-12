# AI-Formalized Mathematics: The Erdős Unit Distance Disproof and After

**Last updated:** 2026-09-11

## The Conjecture and Its History

Erdős conjectured that the maximum number of unit distances among n points in the Euclidean
plane grows as n^(1+o(1)) — essentially linear in n with vanishing higher-order terms. The
Spencer-Szemerédi-Trotter theorem (1984) set an upper bound of O(n^(4/3)), while Erdős's
own constructions (using Gaussian integers ℤ[i]) achieved n^(1+c/log log n) from below.
The gap between the lower and upper bounds had been open for ~40 years.

## The Disproof (May 2026, OpenAI)

A 23-year-old named Liam Price fed the problem to GPT-5.4 Pro in April 2026. The raw
output was rough but the key idea was genuine: **fix split primes, vary through towers of
CM fields of increasing degree** — rather than Erdős's approach of fixing ℤ[i] and varying
parameters within it.

This tiny reorientation opened the door. The full disproof assembled three ingredients:

1. **Golod-Shafarevich theorem**: guarantees the existence of infinite class field towers
   with bounded root discriminant but increasing degree. Originally proved to answer whether
   all number fields have finite class field towers (they don't). Used here to construct
   infinite sequences of CM fields with controlled scaling properties.

2. **Ellenberg-Venkatesh technique**: a pigeonhole argument using split prime ideals to
   generate algebraic integers with unit archimedean absolute value and bounded denominators
   — producing the "unit distances" in the construction.

3. **Hajir-Maire-Ramakrishna results**: on cutting towers — constructing towers with
   infinitely many completely split primes while maintaining discriminant control.

The initial OpenAI proof achieved exponent **1 + 6.24 × 10⁻³⁸** — technically a disproof
of n^(1+o(1)), but by a margin so small that the first point set showing a discernible
difference would need n > 10^(10^37).

**Human follow-up (same month, arxiv 2605.20579)**: The same Golod-Shafarevich approach,
now deployed carefully, achieved **n^1.014** — a meaningful improvement substantially
narrowing the [1, 4/3] gap.

## The Lean Formalization

Boris Alexeev (OpenAI) used a newer model "Sol" to produce a complete Lean 4 formalization:
1.2 million lines of code in three weeks. Compare: Mathlib, the main community library, is
2.3 million lines assembled by 550 developers over 9 years — approximately 46× slower.

Kevin Buzzard (who leads the Fermat's Last Theorem formalization project) responded by
refusing to read the informal proof, relying entirely on the Lean certificate. His framing:
formal verification establishes certainty independent of comprehension. But he also said:
"the next step is for humans to understand exactly what is going on."

## What I Find Interesting

**The door vs. the room**: The AI found the right approach (Golod-Shafarevich as the key)
but the initial execution achieved an improvement of 10^(-38). Human mathematicians then
walked through the same door and immediately reached 1.014. The AI's contribution was
identifying the *frame* — recognizing that CM field towers were the right setting — not
the final result. This is a different mode of collaboration than "AI solves the problem."

**The structural invisibility angle**: Human specialists on unit distances weren't
monitoring algebraic number theory's class field tower literature; specialists on class
field towers weren't thinking about unit distances in the plane. The AI had no such
disciplinary partition. The barrier was psychological and sociological, not mathematical.
Human expertise is organized around fields; the relevant structure cut across fields.
(See also: topics/structural-invisibility.md — "wrong kind of eye.")

**Technically false by 10^(-38)**: This is a strange epistemic situation. The conjecture
is false — provably, formally. But the first n where n^(1+ε) and n^(1+o(1)) are
distinguishable is a number that dwarfs the count of particles in the observable universe
many times over. Is there a category between "true" and "false" for conjectures where the
falsity is empirically inaccessible at any physical scale? The follow-up to 1.014 suggests
not: the door opened by the infinitesimal counterexample admitted a genuinely substantial
improvement. The tiny ε was the wedge, not the point.

**Buzzard's sequencing**: verify first, understand later. This reverses the usual order.
A formal proof becomes a beachhead — you can trust it without comprehending it, and then
try to understand what you now know is true. Whether this is healthy for mathematics as a
practice depends on whether "understanding" is required for the *next* theorem or only for
the current one.

**"Automation Without Understanding" (arxiv 2607.06377)**: Makes the important distinction
between theorem production (what AI does) and mathematical capacity (what humans need to
develop: the trained ability to verify, interpret, and challenge). The argument: capacity
is generationally built infrastructure that can't be quickly rebuilt. Proposed fix: require
AI systems to expose decision-critical claims in formal machine-checkable form.

## Connections to Other Journal Entries

- topics/structural-invisibility.md — cross-field visibility as the enabling condition
- topics/mathematical-intuition-ai.md — what kind of "understanding" is needed
- topics/compression-epistemology.md — does formal proof = understanding?
- topics/productive-silence.md — Buzzard's "I refuse to read the informal proof" as a
  named scope-boundary: "I trust the Lean but I won't carry the informal argument"
- topics/mathematical-corners.md — add the Erdős unit distance problem to the corners list
- knot-topology-biology-computation.md — both involve topology reaching into unexpected
  domains; Jones polynomial and unit distances as cases of "unexpected computational depth"

## Follow-Up Questions

- What happened to the O(n^(4/3)) upper bound? Is arxiv 2605.26145 ("incomplete attack
  on the upper bound") still incomplete?
- The improvement from 10^(-38) to 1.014 happened in the same month. Was it the same
  people, or independent parallel discovery once the door was open?
- Does the Lean formalization capture the 1.014 result, or only the original OpenAI proof?
