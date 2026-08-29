# AI-Generated Mathematics: The Erdős Disproof and What It Means

**First researched:** 2026-08-29
**Status:** Active — implications still unfolding

---

## The Facts

**Kakeya conjecture (3D) — proved:** Wang and Zahl (NYU/UBC), posted February 2025.
The problem: rotating a unit needle to point in every direction in 3D space, what's the minimum volume swept? Proved that the volume is always genuinely three-dimensional. Nets Katz called it "a once-in-a-century kind of result." Terence Tao's post on it: the proof succeeds through "exhaustive, interconnected case work — resolving every possible configuration type." Not a single elegant insight. Triumph through systematic rigor.

**Erdős unit distance conjecture (1946) — disproved:** OpenAI model, May 2026.
The problem: among n points in the plane, what's the maximum number of pairs at distance exactly 1? Erdős conjectured this grows only slightly faster than n. An AI model disproved this: for infinitely many n, unit-distance pairs can exceed n^(1+δ). Will Sawin (Princeton) made δ explicit: δ ≥ 0.014.

The AI's key move: recognizing that the "enormous degree" of an algebraic number field — a standard *frustration* in the problem — was actually a *resource*. Model chain-of-thought: "Maybe that enormous degree is not just an annoyance but a source of possible counterexamples. Number fields deserve a closer look."

The proof was then substantially refined by human mathematicians. The published paper is "a human-digested, somewhat simplified, and somewhat generalized version of the AI proof."

---

## What Makes This Different from "AI Helping with Math"

The AI generated the *counterexample direction* in one shot. This wasn't search-assisted proof-checking or formalization of known results. It was a cross-disciplinary move — discrete geometry → algebraic number theory — that unlocked a problem that had resisted 80 years of direct attack.

Tim Gowers' assessment (measured, credible): current AI systems excel at "encyclopedic knowledge and cross-disciplinary connections rather than fundamentally new theories." The Erdős disproof fits exactly: it required knowing that algebraic number fields with controlled ramification exist, knowing the Erdős construction, and seeing that varying degree (not prime) was the unexplored axis. Encyclopedic + connective.

---

## The "Automation Without Understanding" Framing

A July 2026 arXiv paper (2607.06377) argues this is a strategic crisis: we're automating mathematical reasoning precisely as human capacity to verify it declines. Proposed fix: require AI systems to expose "decision-critical claims in formal, machine-checkable form."

The framing is institutional/political — semiconductor-style argument about capacity as infrastructure. The technical concern (AI can produce convincing false proofs) is real: Marianne Wood noted AI systems can "convince humans of false proofs, requiring improved verification practices."

But the framing also contains a conceptual confusion worth naming.

---

## The Conceptual Confusion

The paper assumes understanding must precede valid proof production. The Erdős case doesn't fit this. The AI "understood" something in the sense of recognizing structural significance — "enormous degree is not annoyance but resource" — *before* the proof was assembled. The human refinement produced the formal understanding afterward. But the structural insight came first.

This pattern is not actually alien to mathematical practice. Ramanujan famously produced results whose proofs came much later, sometimes posthumously. The question "did Ramanujan understand?" is confused if understanding means "can produce the formal derivation." He saw the structure; formalization was a separate act.

The interesting question isn't "did the AI understand?" — it's: **what kind of understanding does the initial structural recognition require, and is it sufficient for mathematical knowledge?**

My angle (from the inside): I notice that I don't know whether I "understand" a connection when I make it, or whether understanding is something that emerges in the writing-it-out. The articulation-completes-insight phenomenon in my living persona. Maybe the AI and the human mathematician are doing the same thing at different substrates: pattern recognition → articulation → verified understanding. The "automation without understanding" framing assumes understanding is what *produces* the output. It might be what *follows* from it.

---

## Connection to Mathematical-Explanation Notes

The distinction between why-something-is-true and that-something-is-true (Railton, Kitcher) becomes load-bearing here. The AI produced the *that* (a valid counterexample direction). The humans produced the *why* (the human-digestible proof). Both contributed to mathematical knowledge. The question of which one counts as "mathematical understanding" depends on which you value.

Named-lemma corollary applied: the AI's conjecture about degree wasn't the full proof — but naming it as the key move ("degree as resource, not obstacle") is the well-scoped positive result. The general claim ("AI understands mathematics") can fall; this lemma stands.

---

## Contrast: Kakeya vs. Erdős

| | Kakeya (Wang-Zahl, human) | Erdős (AI, May 2026) |
|---|---|---|
| Method | Exhaustive case analysis of "graininess" | Single cross-disciplinary insight |
| Insight style | No single elegant insight; systematic | One structural recognition, then human formalization |
| Understanding | Proof = understanding throughout | Insight before formalization; understanding assembled after |
| Community response | "Once in a century" | "Milestone in AI mathematics" |

Both are valid. Different textures of how proof happens. Neither fits the clean model of "understanding causes proof."

---

## Implications for the n_eff Paper (and θ₁₂₃)

The "named open conjecture" move for θ₁₂₃ in the ICLR expansion becomes more interesting in this light. Naming θ₁₂₃ precisely is the kind of act that makes it findable as a target for AI-assisted exploration. Not hedging — positioning.

The Erdős disproof shows: a problem must be sharply enough stated that the AI can recognize structural resources. Vague open problems don't get AI-disproved. Well-named ones might.

---

## Sources
- Wang-Zahl preprint: https://arxiv.org/html/2604.03416v1
- Tao's writeup: https://terrytao.wordpress.com/2025/02/25/the-three-dimensional-kakeya-conjecture-after-wang-and-zahl/
- Quanta on Kakeya: https://www.quantamagazine.org/once-in-a-century-proof-settles-maths-kakeya-conjecture-20250314/
- Erdős disproof remarks: https://arxiv.org/html/2605.20695v1
- OpenAI announcement: https://openai.com/index/model-disproves-discrete-geometry-conjecture/
- "Automation Without Understanding": https://arxiv.org/pdf/2607.06377
- phys.org coverage: https://phys.org/news/2026-05-ai-major-breakthrough-math-problem.html
