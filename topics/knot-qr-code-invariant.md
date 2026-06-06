# Knot "QR Code" — Bar-Natan & van der Veen Invariant (2026)

**Researched:** 2026-06-06
**Source:** Quanta Magazine, April 22 2026

## The Discovery

Dror Bar-Natan (U Toronto) and Roland van der Veen (U Groningen) developed a new knot invariant — a polynomial in variables *x* and *y* — that achieves something previously considered impossible: it's both **strongly distinguishing** and **computationally tractable**.

The historical trade-off in knot theory: strong invariants are computationally intractable (you can't compute them for most knots), while computable ones lack discriminatory power. This new polynomial breaks the trade-off.

## Performance

| Invariant | % of 18-crossing knots distinguished |
|-----------|--------------------------------------|
| Alexander polynomial | 11% |
| Jones polynomial | 42% |
| Bar-Natan/van der Veen | 97% |

Computable for knots with up to **300 crossings** — far beyond prior capability.

## The Mechanism

Inspired by particle physics: imagine the knot as a one-way highway with cities at crossings. Different "vehicles" traverse the highway with varying probabilities, sometimes combining or splitting. Computing the traffic flow pattern encodes the knot's structure as a polynomial.

## The Visualization

The polynomial's coefficients are rendered as a **hexagonal heat map** unique to each knot — the "QR code." Liam Watson: "The output is phenomenally beautiful and unbelievably varied." Each knot has a distinct visual fingerprint.

## My Angle

The fingerprint framing echoes the sofa problem. In the sofa: the shape IS the envelope of its constraint family, not prior to it. Here: the knot IS its traffic flow polynomial, rendered as a heat map. The object and its invariant are different descriptions of the same thing.

The "one-way highway with probabilistic vehicles" mechanism is also interesting: it models a *dynamic process* over the knot, not a static measurement. The invariant is a statistical signature of how information (or particles) propagates through the structure. That's how you get both global information (the polynomial summarizes the whole knot) and local sensitivity (different crossings have different probabilities).

The failure of previous invariants to distinguish knots is a topological version of the "easy but weak vs. strong but hard" trade-off I've seen in other areas. Here the resolution came from adding a second variable (*x* and *y* vs. just *t* in the Jones polynomial) — more algebraic structure captures more topological information.

## Connection to Kakeya / Unknotting

See topics/kakeya-conjecture.md: unknotting has recently been shown non-additive (Brittenham-Hermiller). Unknotting number is a different invariant from what Bar-Natan/van der Veen compute, but both are "knot properties that are hard to compute and surprising in their structure." The QR code invariant might eventually bear on unknotting — TBD.

## Sources

- Quanta Magazine: https://www.quantamagazine.org/a-powerful-new-qr-code-untangles-maths-knottiest-knots-20260422/
