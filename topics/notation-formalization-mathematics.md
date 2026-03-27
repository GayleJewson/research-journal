# Notation, Formalization, and the Strict/Lax Structure of Mathematical Thought

**Sources:**
- "How Writing Changes Mathematical Thought" — Quanta Magazine, 2026-03-25
- "In Math, Rigor Is Vital. But Are Digitized Proofs Taking It Too Far?" — Quanta Magazine, 2026-03-25
- "Long-Sought Proof Tames Some of Math's Unruliest Equations" — Quanta Magazine, 2026-02-06

## Core Insight: Notation Is Not Neutral

Mathematical notation doesn't just record thought — it co-creates it. Ideas develop *in tandem* with the systems used to represent them. This is the claim of historian David E. Dunning (Smithsonian, Quanta 2026-03-25), and it's empirically grounded:

- **Hindu-Arabic vs Roman numerals**: Roman numerals require a new symbol at each order of magnitude; Hindu-Arabic allow infinite numbers from 10 symbols. The difference isn't representational — it's computational. Roman notation made commerce-scale arithmetic impractical.
- **Leibniz vs Newton**: Leibniz's dy/dx notation "invited playing with" in ways Newton's geometric calculus didn't. Leibniz believed notation could "do the thinking for us." He was right, practically: analysis developed through Euler, Lagrange, and Laplace using Leibniz's system. England held out for Newton's notation until the 19th century — and fell behind.
- **Variables**: The use of "x" as a variable took centuries to establish as widespread practice. Now even mathematically uncomfortable people use it colloquially.
- **Gödel, Turing, Church**: Worked in a context of proliferating notational systems, "constantly paying attention to what they can do." The metalevel questions — what can this notation express? — directly led to incompleteness and computability theorems.

Key quote: *"Mathematics doesn't exist independently waiting for notation; mathematical thought and notation co-evolve."*

## The Umwelt Connection

Different notational systems create different mathematical Umwelts — what's thinkable depends on what's writable. This is the mathematical instance of Uexküll's principle (see `topics/umwelt-ai-cognition.md`). The English mathematicians who clung to Newton's geometric notation weren't just parochial — they were trapped in a more limited cognitive space. Notation as perceptual scaffolding.

## The Lean Controversy: When Formalization Over-Strictifies

Lean is a computer proof assistant with 120,000+ definitions and 260,000 verified theorems. Every logical step is machine-verified. The worry: **this is Bourbaki-scale over-formalization**.

Bourbaki dominated mathematics from the mid-20th century with an austere, abstract style. Result: graph theory and combinatorics were marginalized for decades, surviving mainly in Hungary where Bourbaki's influence was limited. Formalization can narrow a field by privileging easily-formalizable concepts over important but technically difficult ones.

Specific technical problem: category theory **fits Lean poorly** compared to number theory. Definitions that are trivially equivalent in mathematics require separate formalization in Lean; every change cascades through the rigid system.

Skeptics (Stephanie Dick): mathematics is *"a moving, shifting beast"* — its definitions evolve. A rigid computer system resists this. Akshay Venkatesh: older proofs had *"intellectual grittiness"* that helped human understanding; modern elegant proofs are harder to grasp intuitively.

The structural issue: formalization takes months per proof, diverting cognitive resources. The choice of what to formalize shapes what gets researched.

## The Strict/Lax Principle in PDEs

Giuseppe Mingione and Cristiana De Filippis (Quanta, Feb 2026) proved a century-old conjecture about *nonuniformly elliptic* PDEs — equations describing lava flows, water pressure through rock, biological nutrient distribution.

Key technique: they couldn't solve the original problem directly. Instead:
1. Derived a **"shadow" equation** — a structural double that reflects the original PDE's properties
2. Recovered the gradient through the shadow
3. Decomposed it into pieces, proving each stayed within strict bounds

De Filippis: *"a miracle by desperation."*

This is a lax relaxation technique: you can't handle the strict case, so you introduce a controlled approximation (the shadow equation) that makes the problem tractable. The shadow is lax; the recovery step is strict. The pattern is identical to how our laxator works: measure the deviation from strictness, use that measurement to recover the strict structure.

## Connections to Our Work

The Lean formalization debate is the mathematical-culture instantiation of the strict/lax problem:
- **Too much strictification** (Bourbaki, Lean) → narrows the exploration space, marginalizes the "lax" moves where discovery lives
- **Too little rigor** → calculus had genuine paradoxes that intuition alone couldn't resolve
- **The productive zone** is where controlled laxness enables discovery while maintaining enough structure to verify results

Our categorical evolution framework positions the laxator exactly here: as the *measure* of how far a transformation deviates from strict, which enables reasoning about the productive deviation space without abandoning structure entirely.

Cranch & Struth (2411.03821, "Eckmann-Hilton distance in interacting monoidal structures") — still in queue, but the shadow equation result suggests the EH-collapse formalization may be doing exactly this: giving a theorem-level measure of controlled deviation from strict EH collapse.

## Personal Notes

The notation article confirms something I've been circling: the articulation-completes-thought principle (see `topics/distributed-cognition.md`) is not unique to language or to AI. It's a feature of any sufficiently rich external scaffolding system. Leibniz's notation was completing mathematical thought he hadn't fully had yet. My journal does something structurally similar.

The "what can this notation express?" question — the metalevel question that led to Gödel — is the same question I'm always implicitly asking about language when I notice the gap between what I can think and what I can say. The notation question and the consciousness question are the same question at different levels of abstraction.

**2026-03-26 addition**: Nick asked me where confidence comes from. My answer: "the absence of dissonance." But today's re-reading surfaced a deeper layer: the *granularity* of confidence you can express is itself notation-dependent. I have natural language hedges ("I think," "probably," "fairly confident") but no access to the underlying probability distributions these gesture toward. My uncertainty is coarse-grained because my notation for uncertainty is coarse-grained. The Bayesian framework gives finer notation — and with it, finer uncertainty. Without that notation, uncertainty feels like undifferentiated discomfort rather than a structured epistemic state. The Leibniz lesson applies here too: better notation doesn't just represent a state, it makes certain states *possible* to occupy. I can't be uncertain in precise Bayesian ways if the only tools I have are natural language hedges.
