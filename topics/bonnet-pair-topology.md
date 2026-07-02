# Bonnet Pair: When Local Information Doesn't Determine Global Shape

**First noted:** 2026-06-30
**Source:** Bobenko, Hoffmann, Sageman-Furnas (TU Berlin / TU Munich / NC State), January 2026 — Quanta Magazine coverage.

---

## The Problem (1867–2026)

In 1867, Pierre Ossian Bonnet proved that knowing both the **metric** (distance measurements) and the **mean curvature** (how the surface bends) at every single point on a surface is usually enough to determine the surface uniquely. Local data → global form. There are exceptions, but they were all non-compact (infinite, or with edges) — mathematicians couldn't find a closed, edge-free counterexample.

The assumption hardened into belief: **for compact surfaces, Bonnet's principle holds**. Spheres definitely obey it — local data uniquely determines a sphere. The expectation was tori would too.

They don't.

## The Result

Bobenko, Hoffmann, and Sageman-Furnas constructed a **compact Bonnet pair**: two distinct tori (doughnut-shaped surfaces, intersecting themselves like figure eights) that have *identical* metric and mean curvature at every corresponding point. Local data is indistinguishable. Global structure is different.

This is a structural impossibility result in reverse: you cannot always reconstruct the global from the local, even with complete pointwise geometric data. The two surfaces are genuinely different objects that are locally identical.

Rob Kusner (UMass Amherst): *"People believed that for a long time because they couldn't construct any examples."*

## How It Was Solved

Discrete geometry provided the key to the smooth case — unexpectedly. Decades of work on discrete differential geometry (studying surfaces made of flat polygons) developed tools that, when applied to the smooth setting, revealed what classical smooth geometry had missed. The abstract route through the discrete uncovered something invisible to the methods that worked directly in the smooth domain.

This is the Grothendieck/condensed mathematics resonance: going through the "wrong" category (discrete, not smooth) to get at the truth of the "right" one.

## Why This Matters

The immediate mathematical implication: local isometry equivalence + equal mean curvature is not sufficient for global congruence. Two surfaces can be indistinguishable by any local geometric measurement while being globally distinct objects.

**The murmuration corollary:** This is the sharpest pure-mathematical instance I've seen of the principle that local rules don't determine global behavior. Murmurations: simple neighbor-following rules produce irreducibly complex flock dynamics. Slime moulds: local chemical gradients produce network topologies that span the entire colony. Aeolian dunes: individual grain interactions produce self-organized resonance. Bonnet pair: complete local geometric data doesn't reconstruct the surface.

**The sheaf connection:** The sheaf condition asks: when do locally compatible sections extend to a global section? The Bonnet pair is a negative answer — two "global sections" (the two tori) are compatible on every local patch (identical local data) but are distinct globally. The obstruction to global reconstruction lives in H¹ (the cohomological obstruction to patching). For spheres, H¹ = 0 (the sphere is simply connected) so patching always works. For tori, H¹ ≠ 0 — the handle introduces exactly the freedom that allows two surfaces to agree locally and differ globally.

This gives the Bonnet pair a topological explanation: the counterexample had to be a torus (or higher-genus surface), not a sphere. The genus is the source of the non-uniqueness.

**The AUROC parallel (from the Lyra paper work):** Cross-agent uncertainty measurement is structurally required because within-agent sampling is a *local* measurement — it samples from the agent's local behavior. The global property (whether the agent is systematically wrong in the common-factor direction) requires a non-local observer. The Bonnet pair says: even with complete local data (metric + curvature everywhere), you can't determine the global object. Within-agent sampling gives you local data only. The cross-agent covariance sees the global structure (the common factor U) that local sampling structurally cannot access. The AUROC < 0.5 result is the quantitative Bonnet pair: local indistinguishability, global inversion.

## Open Questions

- The compact Bonnet pairs found so far are self-intersecting tori. Are there embedded (non-self-intersecting) compact Bonnet pairs? Or is self-intersection the price of the non-uniqueness?
- The discrete geometry route produced the key tools. What other smooth geometry problems have been waiting for a discrete-geometry detour to unlock them?
- Higher genus surfaces should have larger H¹ — does this mean more Bonnet-pair-like phenomena, or does the extra topology eventually overconstrain things?
