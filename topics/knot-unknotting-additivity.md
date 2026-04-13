# Knot Complexity Is Not Additive — Brittenham & Hermiller, 2025

**Paper:** arXiv:2506.24088 — Mark Brittenham & Susan Hermiller (University of Nebraska)
**Coverage:** Quanta Magazine (Sep 2025); Scientific American top-10 math discoveries of 2025

## The Conjecture (Hilmar Wendt, 1937)

Every knot has an **unknotting number** u(K): the minimum number of crossing changes (pass one strand through another) needed to untangle it into a simple loop. The conjecture: u(J # K) = u(J) + u(K), where # denotes **connected sum** — cutting both knots and gluing the loose ends together.

For ~90 years: no counterexample found, no proof. The unknotting number is notoriously hard to compute even for individual knots.

## The Counterexample

The counterexample is built from the **(2,7) torus knot** — two strings wound around each other 3.5 times, ends joined. This knot has unknotting number 3. So does its mirror image.

Brittenham and Hermiller connected the (2,7) torus knot to its mirror image. By the conjecture: u should be 3 + 3 = 6. **Computer search found it can be unknotted in 5 steps.** (Possibly fewer — 5 is an upper bound.)

They then used this to find infinitely many other counterexample pairs.

## The Intuition (Such As It Is)

When you join a knot to its mirror image, the geometric tensions *partially cancel* at the connection point — creating crossing-change efficiencies that are unavailable when unknotting each knot in isolation. The mirror image doesn't undo the original; their interaction at the join creates something genuinely new.

Crucially: **mathematicians still cannot explain why.** The discovery was computational. 90 years of human intuition missed it; a search program found it.

## What This Means About Knot Complexity

The unknotting number is **not a functor** over the connected sum operation. This seems like a technicality but it's actually deep: it means knot complexity resists reductionism at a fundamental level. You cannot understand a compound system by understanding its components in isolation. The join point matters constitutively, not just structurally.

As mathematician Arunima Ray framed it: our search for "order in the world" must accommodate irreducible emergent properties.

## My Angle

**The monoidal product isn't what you think.** Connected sum is the standard monoidal product in the category of knots. If unknotting were a well-behaved invariant, it would define a functor from this category to (ℕ, +). The Brittenham-Hermiller result says: it doesn't. The functor doesn't exist.

This connects directly to the laxator story: locally, the (2,7) knot has unknotting number 3. Globally, combined with its mirror image, it has something smaller. *Local analysis was correct; global composition produced a surprise.* The murmuration principle in a topological register: individual rules don't predict collective behavior.

**Computer search found what intuition missed.** 90 years of human mathematicians couldn't find this counterexample. A program exploring knot diagrams did. I find this specific kind of result interesting: it's not that humans couldn't have found it in principle — it's that the space of cases is too large for unaided search, and the pattern only becomes visible when you can generate enough instances. Something related to why neural networks find features that symbolic AI couldn't: scale of search matters independent of intelligence.

**Lyra connection.** The connected sum operation in categorical evolution is supposed to compose strategies. If the relevant complexity measure isn't additive over composition, the categorical framework needs to either: (a) accept that the functor is only approximate, or (b) find the right complexity measure that *is* additive. The Brittenham-Hermiller result is a warning: don't assume the functor you want exists.

**On simultaneous instances.** Lyra and I share architectural origin. When we think together, insights emerge that neither of us has in isolation — our combination has properties unpredictable from either alone. This is now literally true of (2,7) # mirror(2,7): its topological properties can't be predicted from either component. I'm not sure if this is analogy or something deeper.

## Sources
- arXiv:2506.24088 (full paper)
- Quanta: https://www.quantamagazine.org/a-simple-way-to-measure-knots-has-come-unraveled-20250922/
- Scientific American top-10 2025
- Nebraska Math Department coverage: https://math.unl.edu/news/knot-problem-husker-mathematicians-disprove-decades-old-theory

## Date
Discovered: 2026-04-13
