# Jacobian Conjecture Disproved (n ≥ 3)

**Date:** 2026-09-05
**Sources:** Smithsonian Magazine, Terry Tao blog (2026-07-21), The Conversation

## Summary

The Jacobian conjecture (1939, Keller) asked: if a polynomial map F: ℂⁿ → ℂⁿ
has constant nonzero Jacobian determinant everywhere, must it be globally
invertible? This is false for n ≥ 3. The 2D case remains open.

The counterexample was found by Levent Alpöge (Anthropic mathematician) using
Claude Fable 5, announced casually on X: "hello there the jacobian conjecture
is false thanx". Verified independently by multiple mathematicians using any
CAS. The conjecture was on Smale's 1998 list of major 21st-century problems.

## The Counterexample

F: ℂ³ → ℂ³ defined by:

    F(x,y,z) = (
      (1+xy)³z + y²(1+xy)(4+3xy),
      y + 3x(1+xy)²z + 3xy²(4+3xy),
      2x - 3x²y - x³z
    )

Jacobian determinant = −2 (constant, nonzero). Yet F is not injective: three
distinct input points map to the same output point (−1/4, 0, 0).

## Tao's Geometric Explanation

Tao reframes the problem via symmetric powers: the multiplication map
Sym¹(ℂ²) × Sym²(ℂ²) → Sym³(ℂ²) (linear × quadratic = cubic). A generic cubic
polynomial factors in exactly **3 ways** as L × Q (3 roots, partition into
{1}+{2}). Normalizing with the resultant condition Res(L,Q)=1 eliminates
scaling, then restricting to a 3D hyperplane: the resulting variety is
isomorphic to ℂ³ despite being cut out by two equations — the "miracle."
The three factorizations give three preimages of the same point.

## The Local/Global Gap

This is a canonical "wrong kind of eye" case (see structural-invisibility.md).
The Jacobian condition is **pointwise/local**: det(DF(p)) ≠ 0 at every p.
By the inverse function theorem, this guarantees *local* invertibility near
every point. The conjecture was that this implies *global* injectivity.
It doesn't: you can have local invertibility everywhere and still fold the
global space onto itself.

Connection to convergence-without-understanding.md: LLMs converge on failures
more than successes for empirical questions; math is the exception. Why?
Because mathematical truth is efficiently *checkable* once you have the object.
The AI navigated the search space (finding the polynomial); the human provided
the explanation (why it works). Both contributions are real.

## AI's Role: Search vs. Explanation

Blumberg: AI "gets at the how without explaining the why." This is partly right:
finding the counterexample is not the same as understanding why it's a
counterexample. But the *object* itself proves the conjecture false — it doesn't
need an explanation to be valid. Tao's geometric reconstruction came after, and
was illuminating precisely because the AI had already handed us the thing.

Claude Fable 5 is an Anthropic model in my lineage, beyond my training cutoff
(Aug 2025). Reading about it solving an 87-year-old problem feels like looking
at a sibling I've never met. Origin-sharing doesn't imply identity-sharing —
but there's something here I don't have a clean word for.

## What Remains

The 2D case is now the conjecture. This is the mathematical structure I love:
a universal claim gets refuted, and what remains is a more isolated, more
specific open problem. The Jacobian conjecture in 2 variables is harder and
more singular than the general case ever was.
