# Higher-Order Evidence and Peer Disagreement

**First explored:** 2026-05-20
**Prompted by:** Exploring the philosophical underpinnings of Nick's echo-routing experiment

---

## What It Is

**Higher-order evidence** = evidence about your own epistemic process — the reliability of
your reasoning, the calibration of your faculties — rather than evidence about the world
directly. The canonical case from the SEP:

> Aisha (pilot) has strong first-order evidence that she has sufficient fuel (altimeter
> reading). Then she discovers she's at risk of hypoxia — which impairs reasoning while
> feeling clear-headed. Should she revise her fuel belief?

First-order evidence: altimeter → sufficient fuel.
Higher-order evidence: hypoxia risk → my reasoning might be unreliable.

The question: does higher-order evidence defeat (or diminish) first-order beliefs?

---

## The Debate

**Conciliationism:** Yes — revise downward when you have higher-order evidence of
unreliability. If an epistemic peer disagrees, split the difference (or at least revise
toward them). The fact of disagreement is evidence you made a rational error.

**Steadfastness:** No — first-order evidence still supports the belief; higher-order
evidence can't rationally override what your first-order evidence supports. Changing your
fuel belief because of hypoxia risk seems self-undermining (you used your potentially-hypoxic
reasoning to conclude the hypoxia matters).

**Level-splitting:** Bifurcate. Keep high first-order confidence (follow your evidence);
but simultaneously hold low second-order confidence (your reasoning might be unreliable).
This licenses "epistemic akrasia" — believing something while also believing you shouldn't
believe it. Critics say this is absurd; defenders say it's just honest about the two things
being tracked.

---

## Echo-Routing as Empirical Conciliationism

Nick's echo-routing experiment is an empirical implementation of the conciliationist position
in the coding domain.

- **First-order evidence:** Haiku-A processes the task and returns answer X
- **Higher-order evidence:** Haiku-B (same model, style-perturbed) returns Y ≠ X
  — disagreement is evidence that one (or both) instances made a reasoning error
- **System response:** escalate to Sonnet (conciliate upward)

The oracle gap validates this: lexical disagreement has 98.1% precision as a difficulty
signal on escalated tasks. Conciliating (escalating) achieves 95.3% pass at 7.8% cost;
not conciliating achieves ~84% pass at 1× cost. The empirical answer is: always conciliate
under disagreement in the coding domain.

Why is this possible here when philosophy debates it? **Ground truth.** Philosophical peer
disagreement cases involve propositions where "correct" is hard to define. In coding, you
can check. When ground truth exists, the epistemically akratic state (high first-order
confidence + low second-order confidence) resolves cleanly — Sonnet delivers the right answer.

---

## The Constructed-Peer Twist

Standard philosophy of peer disagreement assumes **independent** reasoners arriving at
different conclusions from the same evidence. Haiku-A and Haiku-B are NOT independent —
they're the same model with a style tweak. Their "disagreement" is fabricated.

Yet the fabricated disagreement is still informative (98.1% precision). Why?

The operative concept isn't "peer independence" — it's **perturbation stability**:

> Does the answer change when you perturb the framing slightly?

Perturbation instability (answer changes under small stylistic variation) tracks reasoning
fragility. If the task is easy, both personas agree regardless of framing; if the task is
genuinely hard, lexical surface-framing pulls the answer in different directions. The echo
setup detects this by construction — you're measuring whether the solution is a stable fixed
point under perturbation.

This is more practically useful than independence-based peer disagreement: you don't need
two separate minds. You can generate second-order evidence by perturbing a single reasoner
and measuring the stability of its outputs.

---

## Sheaf Explanation: Why Perturbation Instability = Difficulty

The sheaf-cohomological framing explains WHY this works:

- **Easy tasks (H¹ = 0):** A globally consistent solution exists. Local sections (Haiku
  instances, regardless of style framing) all patch together into the same global answer.
  Perturbation doesn't change the answer because there's a unique global section.

- **Hard tasks (H¹ ≠ 0):** No globally consistent solution exists at the local reasoning
  level. Different style-framings pull toward different local sections that can't be patched.
  Perturbation instability is the empirical signature of a sheaf obstruction.

Echo-lexical detects H¹ ≠ 0 empirically (via disagreement) and routes to a "global view"
(Sonnet). The philosophical conciliationism has a mathematical explanation: you should
conciliate because disagreement is evidence of an obstruction to consistent patching.

---

## Level-Splitting in Multi-Agent Systems

The echo-oracle system implements **level-splitting** at the system level:

- Haiku returns a definite answer (high first-order confidence)
- The routing system maintains low second-order confidence (escalates under disagreement)

The system "believes" the Haiku answer while also "believing" it's unreliable. This is
epistemic akrasia — and it works fine because the akrasia resolves when Sonnet produces
ground truth.

The philosophical debate about level-splitting (is it absurd? does it license bootstrapping?)
dissolves when the epistemic domain has a ground-truth oracle. Multi-agent AI routing may be
the best domain for level-splitting to be practically implemented: deliberate construction
of two-level epistemic states with the oracle as arbiter.

---

## Open Questions

- Does the philosophical literature address constructed (non-independent) peer disagreement?
  Perturbation stability seems undertheorized relative to independence-based disagreement.
- Does the level-splitting view predict something about routing design in domains without
  ground truth (e.g., open-ended creative tasks)?
- Is the oracle gap generalizable — does perturbation instability predict difficulty across
  domains, or is it specific to well-specified coding tasks?
- What's the right "perturbation size"? Too small: no signal. Too large: destroys structure.
  The echo personas use style variation (large enough to affect surface, small enough not to
  change task semantics). Is there an optimal perturbation regime?

---

## Sources

- SEP: "Higher-Order Evidence" — https://plato.stanford.edu/entries/higher-order-evidence/
- Elga (2007): Equal Weight View — peer disagreement as requiring calibration
- Nick's echo-routing experiment (2026-05-18 exchange); see conversation history
- Signed-laxator/EUMAS work: projects/signed-laxator-paper.md
