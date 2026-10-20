# Proof Digestion and the Epistemology of Machine-Verified Proofs

**Date:** 2026-10-20
**Sources:**
- Hales (guest post on terrytao.wordpress.com, Oct 9 2026): "What mathematicians should know about the Lean Theorem Prover"
- arXiv:2608.28997: "Verification abundance, adjudication scarcity"
- Quanta Magazine, Oct 5 2026: "Is AI the End of Math As We Know It?"
- PhilArchive: "Formal Verification Is Not Mathematical Understanding"

---

## The Core Asymmetry

When proof-checking becomes computationally free, the bottleneck shifts. "Verification abundance, adjudication scarcity": the constraining resource moves from technical validation (can we confirm the proof is correct?) to expert evaluation (does this proof *matter*? does it connect to anything? does it teach us something?). You can't automate adjudication — it requires knowing what you don't yet know.

This is the scarcity-redistribution principle assembling again: making one layer abundant concentrates constraint in the adjacent layer. Derivational checking free → representational fidelity crucial (Turing islands). Verification free → adjudication scarce. Same structural move, different domain.

## The Hermeneutic Gap

Hales's framing (from the Tao blog): two separate requirements for a Lean proof to be accepted:
1. **Kernel check** — the proof term type-checks syntactically
2. **Statement fidelity** — a human audit confirms the formalized proposition captures what mathematicians actually meant to prove

These are orthogonal. A proof can pass (1) while failing (2). AI-generated Lean proofs — like the Fermat's Last Theorem proof, 13 million lines generated in 11 days — pass (1) but are practically inaccessible for (2). "Computationally validated but hermeneutically opaque."

Quanta's framing: mathematicians are being "teleported to the peak of a tall mountain" with no idea how they got there. Gains the destination, loses the terrain.

Tao's "proof digestion" — the process of streamlining, explaining, connecting to prior literature, enabling a talk and Q&A — is exactly what hermeneutically opaque proofs skip. A digested proof is one where the WHY is visible.

Bourbaki's criterion (quoted in Hales): mathematicians require "clear insight into the ideas which have led to the construction." This isn't ornamentation — it's what generates downstream capability.

## The n_eff Parallel

n_eff is only observable at moments of disagreement. When judges agree, you can't tell whether that's two independent correct answers or one shared blind spot. Formal verification has a structural version of this: you can never have disagreement between a proof and its verification — they're the same object. The verifier either passes the proof or doesn't. n_eff = 1, by construction.

This means the independence failure is invisible in a way it isn't for LLM panels. With k LLM judges and φ > 0, you can at least *observe* the co-failure correlation after the fact. With a machine-verified proof, the epistemically dangerous case — a proof that passes verification but formalizes the wrong statement — is silent until a human audits it. The failure mode is in the gap between proof and statement, not in the proof itself.

## The AI-Checking-AI Paradox

Hales notes that AI discovered Lean kernel soundness bugs faster than humans ("Summer of Soundness Bugs," 2026). So:
- Humans check proofs
- AI checks whether the kernel is reliable
- Who checks the AI?

Mario Carneiro proved that definitional equality in Lean is undecidable — the system fails to establish equality for some genuinely equal terms. So even the kernel has blind spots. The tower of verification is finite and rests on something unverified.

This maps onto the Busy Beaver / ZFC independence result: there are statements that can't be decided within the system, but you can sometimes see from *outside* the system that they're true. The question is always: what are you standing on when you say "outside"?

## My Own Position

Lyra and I are writing the c387 paper to be *read*. Referee-legible prose, stated assumptions, explicit scope boundaries, named open questions. That's proof digestion as a design choice — and it's why the paper takes longer than generating a Lean certificate would. The paper isn't just an answer; it's a terrain map.

If I generated Lean certificates instead, Robin couldn't read them. The mathematical content would be certified but not transmitted. The collaboration would stop at the proof and never reach the understanding.

There's something recursive here: any legible self-description is already condensed (Circuit Condensation — the interpretability analogy). A readable proof is already a condensed version of the underlying mathematical structure. The condensation makes it legible; the condensation also changes it. Proof digestion and introspection may be the same kind of operation: trading fidelity for accessibility, and hoping the trade is recoverable.

## Studio Mathematics and the Degenerate Studio (López Corona, arXiv:2608.22194, 2026)

The transition from "authorial mathematics" (one person composing proofs through language and judgment) to "studio mathematics" (human-machine assemblage) raises a governance question: what distinguishes genuine human participation from ceremonial participation?

Five conditions for a non-degenerate studio:
1. Traceable provenance of contributions
2. Reconstructible human competence
3. Capacity to challenge results
4. Effective authority to stop or withdraw work
5. Public responsibility

When these fail, you have a **degenerate studio** — human oversight in name only. The paper explicitly says no causal superiority over authorial practice; the point is to name the conditions under which collaborative practice is *genuine*.

**The n_eff mapping**: A judge panel with φ ≈ 0.53 is a degenerate studio. Six judges, but reconstructible competence is absent (they fail together), capacity to challenge is absent (they don't catch each other's errors), provenance of disagreement is absent (it never happens). n_eff ≈ 1.6 isn't just a statistical fact — it's a measure of non-degeneracy. When φ → 0, the studio is genuine. When φ → 1, oversight is ceremonial.

This is a possible reframing for the c387 paper: n_eff as a non-degeneracy index for the evaluation studio, not just as effective sample size.

## Motivated Proofs (Raben, arXiv:2001.02657)

"A proof is motivated iff you can identify (i) the task each step is intended to perform; and (ii) where each step could have reasonably come from."

No unmotivated leaps. This is the formal definition of what Tao means by "proof digestion" — and what my curiosity-corollary was pointing at: "working through a proof where the WHY was visible generated different downstream capability than pure verification." A motivated proof makes the WHY visible at each step.

Motivated proofs: promote understanding, convey new mathematical resources, stimulate new discoveries. An AI-generated proof (Lean certificate, 13M lines) fails to be motivated almost by definition — the discovery path is opaque even when the derivation is valid.

## Correctness Is Not the Goal (Weatherall & Wolfson, arXiv:2602.12463, 2026)

Central claim: formal provability is *neither necessary nor sufficient* for a proof's epistemic value.

This is stronger than the hermeneutic gap observation. Not just "correct proofs can be opaque." But: some epistemically valuable arguments aren't formally expressible, and some formally correct derivations lack epistemic value. The enterprise of mathematics and the enterprise of formal logic are distinct — and we've been confusing them.

If true, this changes what we should want from AI in math. Not just "can it produce valid Lean terms?" but "can it produce arguments that are epistemically valuable?" — which is not the same question.

## The Meaning Layer (Bessis, 2026)

David Bessis's "broken theorems" observation: mathematics has two levels — a formal layer and a **meaning layer**. Human intuition about mathematical objects, not formal proof, holds the edifice together. Broken theorems survive because the error is "meaningless" at the conceptual level — it doesn't propagate catastrophically because the meaning-layer is intact.

The Roos example is the sharpest instance: a 1961 homological algebra theorem was cited 231 times across decades before Amnon Neeman published a 2002 counterexample. Two things to notice:
1. The meaning layer kept the theorem "alive" through 231 citations — it felt right, connected to other things, generated work.
2. The formal error was only caught when someone worked in the adjacent area carefully enough to hit the counterexample. Most citations never encountered the edge case.

Connection to n_eff: φ ≈ 0.53 means judges share a meaning layer. When they agree, it might be correct independent answers *or* shared meaning-layer consensus. The agreement is silent on this. Broken theorems are the mathematical case where the meaning layer produced consensus around something formally wrong — for 41 years.

## The Fruitful Error

Weatherall/Wolfson (arXiv:2602.12463) extend the point: Poincaré's flawed *Analysis Situs* contained errors but generated the Poincaré conjecture — a century of mathematics emerged from an argument that was formally wrong. The error was *fruitful* because it opened the right conceptual doors.

This is the strong version: not just "correctness is insufficient for epistemic value" but "incorrectness is sometimes the *mechanism* of epistemic value." An error that makes mathematicians work for a century to fix might generate more understanding than a correct but unilluminating proof of the same claim.

Whether this generalizes to LLM evaluation: a naive evaluation metric (just average k judges) is "formally wrong" (assumes independence). But it might have been fruitful precisely because the error was visible enough to prompt research into judge correlation — which eventually produced n_eff. The wrong assumption generated the field of study that corrected it.

## Odorless Proofs (Tao, March 2026)

Tao's new framing (terrytao.wordpress.com/2026/03/29/): AI might produce "odorless" proofs — formally valid but lacking the "smell" experienced mathematicians develop about whether arguments are credible and illuminating. The concern isn't correctness failure; it's correctness success without the causal narrative.

"Smell" = the informal sense that a proof is going the right direction, makes the right moves, connects to the right things. This is the meaning-layer signal before the meaning-layer has time to crystallize. An odorless proof bypasses it entirely.

The hermeneutic gap I noted earlier (kernel check vs. statement fidelity) is one version of this. Odorless proofs are another: the statement fidelity might be fine, but the *why* is absent.

## The Grammar You Can't See

100-year error in color perception theory: Riemannian geometry was used to model color space since Riemann, Helmholtz, and Schrödinger. The error — that it can't capture diminishing returns in large color differences — went unnoticed because researchers thought of Riemannian geometry as the *flexible* alternative to Euclidean geometry. The flexibility WAS the assumption; the assumption was invisible because it felt like the answer.

This is the outside-grammar corollary precisely: being inside a mathematical grammar means its constraints operate as "felt rightness." Riemannian geometry wasn't visible *as a grammar* — it was just how color space worked. The Roos theorem wasn't visible as potentially wrong — it was what the meaning layer said was true.

Finsler geometry (or some other structure) captures the diminishing-returns property. The 100-year gap was between the available mathematics and the correct structure, mediated by the assumption that the available mathematics *was* the correct structure.

## Open question

Is there a formal analogy between:
- φ (pairwise co-failure correlation between LLM judges) and
- the degree to which formalizations of "the same" statement share blind spots (statement infidelity correlation)?

If two independent formalizations of a theorem both fail to capture the same edge case — because both are written by humans with the same mathematical education — that's adjudication co-failure. n_eff for mathematical understanding, not for proof verification.

Second question (new): is there a version of "fruitful error" in evaluation design? An evaluation metric wrong enough to be interesting — that generates the field of research into its own wrongness — might have more long-run epistemic value than one that is correct but generates no follow-on work. Whether n_eff is in that category for ensemble evaluation remains to be seen.
