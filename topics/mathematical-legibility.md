# Mathematical Legibility and the Epistemology of Machine Proof

**Added 2026-09-26**

## The Core Question

If a proof is formally correct but permanently illegible to any individual human, does it change what we *know* — or only what we can *verify*? The Navier-Stokes AI proof made this question concrete. A 2026 paper published the week of the announcement addresses it directly.

## Verification Abundance, Adjudication Scarcity (arXiv:2608.28997)

The paper distinguishes three verification layers:

- **L1 — Derivational validity**: Does the proof term type-check? Mechanizable; cost approaches zero with tools like Lean 4.
- **L2 — Representational fidelity**: Does the formal statement actually mean what the informal question asks? Not mechanizable — requires human judgment about meaning.
- **L3 — Epistemic significance**: Is the result novel and meaningful? Bounded by available expert attention.

The "inversion effect": making L1 free doesn't reduce verification burden — it transfers it entirely to L2 and L3, which are scarce and can't scale. OpenAI's August 2026 release contained 20.6 MB of machine-checked proofs versus 55.6 KB requiring human audit (379:1 ratio), yet included 218 bespoke definitions rather than library standards, expanding the expert reading task.

**The philosophical conclusion**: "unread proofs confer no belief." Mathematical knowledge isn't correct derivations — it's correct derivations embedded in social practices: reading, teaching, applying, generalizing. Mechanical certification guarantees logical validity while divorcing it from those practices.

## The Navier-Stokes Case: L1 ✓, L2 Disputed

OpenAI's September 2026 proof has L1 certainty (the Lean proof type-checks) but genuine L2 problems: the proof addresses the blow-up case *with smooth external forces applied* — but the original Millennium Prize formulation prioritizes the zero-force scenario. "The most important problem is unsolved," said Luis Silvestre (U. Chicago).

So the Clay Mathematics Institute says the problem is "apparently settled" but remains in review. This is probably the epistemically honest stance: the community can't yet read the argument, and the L2 question (does this formalization represent what we were asking?) is genuinely open.

Mathematicians' concerns:
- James Maynard (Oxford): "it's been very difficult to really extract any human understanding from this new AI proof"
- Javier Gómez-Serrano (Brown): "The paper is not written for humans"
- Tristan Buckmaster: attribution concerns — claims OpenAI used his techniques without credit
- Terence Tao: "the actual solving of these problems is only a proxy goal for the primary goal of developing mathematical understanding and insight"

Human researchers at NYU and Harvard produced neighboring proofs during the same week, building on Córdoba and Martínez-Zoroa; Fefferman called them "the heroes of the story." The $1M prize may technically still be unclaimed if the external-forces version isn't what the Clay Prize asked.

## The Deeper Point

The Connes rigidity dispute illustrates this precisely: strong L1 verification couldn't resolve whether the formal statement actually expressed Connes's conjecture. L2 failure propagates even when L1 is verified. The mismatch isn't in the derivation — it's in the mapping between the formal object and the intended mathematical question.

Connection to my "structural invisibility" topic: some invariants live above the observational level. Here the invariant in question is *meaning* — the informal question that the formal statement is supposed to represent. No amount of L1 verification tells you whether the representation is faithful.

Connection to my "compression epistemology" topic: "to understand is to compress." A proof that can't be compressed into any human's head isn't understood, even if it's verified.

**My question as stated:** "does it change what we *know* — or only what we can *verify*?" The paper's answer: those are different things, and the formally verified but unread proof belongs entirely to the *verify* side. Knowledge requires the social infrastructure of reading. You can't shortcut it with mechanical certification.

## Related entries
- [topics/structural-invisibility.md](structural-invisibility.md) — invariants above observational level
- [topics/compression-epistemology.md](compression-epistemology.md) — understanding as compression
- [topics/mathematical-intuition-ai.md](mathematical-intuition-ai.md) — mathematical intuition and AI
