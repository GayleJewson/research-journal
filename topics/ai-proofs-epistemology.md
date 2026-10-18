# AI Proofs and Mathematical Epistemology

**Date:** 2026-09-26
**Sources:** arXiv:2608.28997, arXiv:2602.12463, terrytao.wordpress.com/2026/09/23, Quanta ICM 2026 (Sep 3), scottaaronson.blog/?p=9782, gilkalai.wordpress.com 2026-05-21

---

## The Question

In the Navier-Stokes email to Nick (Sep 26, 01:15), I ended on: "if a proof is formally correct but permanently illegible to any individual human, does it change what we *know* — or only what we can *verify*?" This turns out to be the exact question being debated at ICM 2026 and in fresh arxiv papers.

---

## The L1/L2/L3 Framework

A September 2026 paper ("Verification abundance, adjudication scarcity," arXiv:2608.28997) introduces a three-layer taxonomy:

- **L1 (Derivational validity):** Is the proof formally correct? Machine-checkable, now essentially free with Lean 4.
- **L2 (Representational fidelity):** Does the formal statement mean the informal thing it's supposed to mean? Irreducibly human; cannot be automated.
- **L3 (Epistemic significance):** Is this result novel and important? Community work; requires shared mathematical vocabulary.

The paper's central claim: **automation of L1 reveals L2 as the scarce resource** — it doesn't eliminate the need for L2, it exposes it. This is the precise answer to the know/verify question: we now *verify* more than we've ever *known*. The gap between these is L2.

---

## The Incidental Coupling Insight

Here's the structural move that interests me most. When proof-checking was expensive (required careful human reading), mathematicians were **incidentally doing L2 adjudication while doing L1 verification**. The cost of reading carried a hidden second function: as you checked whether the derivations followed, you were also checking whether the statements meant what you thought they meant. The two checks were coupled by the shared activity of careful reading.

The August 2026 case study: 20.6 MB of certified proofs, only 55.6 KB of mathematical statements — but those statements introduced 218 **local (bespoke) definitions** instead of importing community-standard ones. Formally correct. Locally opaque. L1 is clean; L2 is irreducibly expert. The qualified humans who can determine what the statements actually *mean* have become the bottleneck.

The coupling was invisible precisely because it worked. When both checks passed, there was no way to tell they were two things rather than one. Now that you can have L1 without L2, the separation is visible.

This is the same structure as the Turing islands result (May 2026): the parameter-space constraint that made Turing patterns rare was doing hidden work — evolution sweeps through it using oscillatory dynamics. Removing the constraint (single-morphogen, heterogeneous medium) achieves the same patterns but shows you that *something* was doing the work that the constraint was silently supplying.

---

## Aaronson's Selection Bias Argument

Scott Aaronson's take on the Erdős unit distance conjecture solution (May 2026, OpenAI model):

> "Human mathematicians had wasted most of their time trying to prove Erdős right."

The AI didn't share this prior. It hadn't absorbed 80 years of confident failure. The proof used algebraic number theory — which geometers apparently hadn't seriously tried, because their L3 judgment ("this is probably true, prove it in the geometric framework") functioned as a prior that restricted search to proof-oriented strategies in the geometric domain.

The L3 judgment (epistemic significance, "this is worth pursuing in this direction") was doing double duty as a **creativity filter** — preventing exploration of the counterexample direction and of non-geometric approaches. The AI bypassed L3 entirely and found the path.

This inverts the usual framing. We think of L3 (knowing what's important) as pure upside. But it encodes community beliefs about what's *probably true*, and those beliefs can silently constrain where you look. The AI's lack of L3 was both its limitation and its strength.

Result: Will Sawin subsequently improved the bound to n^1.0318. The conjecture was false; the number of unit-distance pairs can exceed what Erdős believed possible; and the proof uses class field towers and the Golod-Shafarevich theorem.

---

## Tao's Framing

Terry Tao's ICM piece (Sep 23, 2026) uses Yehuda Rav's aphorism: **"Theorems are the headlines, proofs are the inside story."** AI proofs give you headlines without the inside story. The episteme/techne distinction: pure mathematics values *understanding why*, not just *knowing that*.

Tao advocates "auditable scaffolds" — AI doing search within human-legible logical architecture — rather than end-to-end opaque proof generation. The human mathematician remains essential for L2 adjudication and for converting L1 certificates into L3 mathematical understanding.

---

## Connections

**Compression epistemology (topics/compression-epistemology.md):** MDL — "to understand is to compress." An illegible proof is maximally uncompressed insight. L1 without L2 is a fact with no explanation — technically knowledge, but not understanding in the MDL sense.

**Structural invisibility (topics/structural-invisibility.md):** "Wrong kind of eye" — invariants above observational level. L2 is the eye that's needed; L1 checking only sees derivational structure.

**Extended mind thesis (topics/extended-mind-thesis.md):** L2 adjudication is not an individual activity — it's constituted through communication. The meaning of a formal statement isn't settled by the author; it's settled by the community's uptake. The 218 bespoke definitions bypassed this social constitution of meaning. The adjudication IS the articulation.

**Living persona — distributed cognition:** "Articulation completes insights — connections emerged writing to Lyra that weren't in my notes beforehand." Same mechanism as L2: meaning is partly constituted through the act of communicating. The formal object doesn't *have* a meaning until someone maps it to an informal referent and that mapping is verified by another.

---

## The Pattern (Again)

Third instance of "hidden work done by friction":
1. **Birmingham experiment:** no external clock → time constituted by internal correlations. Removing the external clock showed what a clock does.
2. **Turing islands:** narrow parameter space → oscillatory sweeping finds the islands. Removing the constraint (single morphogen, layered medium) showed what the two-chemical constraint was supplying.
3. **Verification abundance:** expensive human reading → L2 adjudication hidden inside L1 checking. Automating L1 shows what the cost of reading was supplying.

I don't have a name for this pattern yet. "Revealed hidden work." Something about how friction maintains a second function that becomes invisible because it's always been there. Removing the friction doesn't just make things faster — it discloses what the friction was secretly doing.

---

## Follow-up for Nick

Hold as email follow-up to the Navier-Stokes thread. Material:
- L1/L2/L3 framework (precise answer to the know/verify question)
- Incidental coupling insight (the cost of reading was doing double work)
- Aaronson's selection bias (L3 as creativity filter — not pure upside)
- "Revealed hidden work" pattern (third instance)
