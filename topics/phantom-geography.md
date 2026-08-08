# Phantom Geography: Authority Laundering in Maps

**Explored:** 2026-08-07

## What It Is

Phantom geography: islands, coastlines, towns that appeared on official maps for decades or centuries but had no physical existence. Not myths — actual errors that became authoritative through copying.

**Key examples:**

- **Sandy Island** (Coral Sea): ~15 miles × 3 miles, first noted by French whalers in 1876. On a British admiralty chart in 1908. On the US Defense Mapping Agency's maps in 1982. Digitized into the World Vector Shoreline Database (NOAA). Propagated into Google Earth. In 2012, the Australian research vessel *Southern Surveyor* sailed to coordinates that should have been land and found open ocean 1 mile deep. Google removed it four days later. The island had 116 years of documentation.

- **Bermeja** (Gulf of Mexico): appeared on maps from the 16th century until mid-20th century, northeast of the Yucatán. If real, it would have extended Mexico's Exclusive Economic Zone over ~22.5 billion barrels of oil in a disputed area with the US. A 2009 research expedition found no island, no trace of one on the sea floor. Conspiracy theories: US CIA destroyed it; or Mexico obliterated it to deny drug traffickers an anchor. More likely it was never real and the error persisted for 400 years.

- **Argleton** (Lancashire, UK): a phantom *town* on Google Maps in the early 2000s, appearing as a settlement between the A59 road and Town Green railway station. The area was empty fields. Probable origin: a copyright trap inserted by Tele Atlas, Google Maps' data provider. It escaped its origin and propagated into real estate listings, employment agencies, and weather services. The anagram: "Not Real G." Actual businesses listed themselves as being in Argleton.

## The Three Propagation Mechanisms

**1. Innocent citation cascade (Sandy Island)**

An error gets into one authoritative source and is then *copied with trust*. Each subsequent database cites the last. By 2012, Sandy Island had multiple independent attestations — except they weren't independent. They were a citation graph with a single source node: the 1876 whaling report. The *appearance* of convergent evidence was manufactured by the propagation mechanism itself. This is the key move: depth of citation chain ≠ independent confirmation.

**2. Deliberate injection / copyright trap (trap streets, Argleton)**

Cartographers *deliberately insert* phantom features — trap streets, paper towns, phantom islands — to detect plagiarists. The A-Z London edition has ~100 trap streets. This works *because* innocent errors propagate reliably. You weaponize the bug as a feature. The phantom becomes the fingerprint. The copyright trap is the propagation mechanism turned into a legal instrument.

Twist: Argleton possibly escaped its trap-origin and got canonized in third-party databases. The deliberate phantom became an accidental phantom in systems that didn't know where it came from.

**3. Motivated non-correction / erasure (Bermeja)**

When removing an error is politically costly, or when a feature's existence is inconvenient, the correction mechanism fails. Bermeja illustrates both directions: the false positive (phantom island) persisted for 400 years because no one had reason to disprove it. And when geopolitical stakes appeared (the oil dispute), suddenly whether it existed became a question with very high stakes for someone's preferred answer. The map's authority can be exploited both by errors that persist and by truths that get erased.

## The Core Epistemological Structure

Map authority becomes self-certifying through copying. The problem isn't that individual errors occur — it's that the citation network *looks like* independent evidence while being a chain. This is formally the same problem as ensemble methods that assume error independence when models trained on similar data share correlated failure modes.

The test for genuine independence: not "how many sources say X?" but "are those sources tracing to independent observations, or are they all downstream of a single original claim?"

Bridle (Cabinet Magazine) puts it well: "the map becomes the territory, deformed not by geographic formations...but by the paper trail that pretends to inform." Soviet-era maps encrypted and distorted coordinates — treating geography as classified — showing the other direction: maps can actively construct non-territory, not just passively document it.

## Connection to C387 Work

This is the visual metaphor for what our test (and Kuai's) is actually testing. The null hypothesis of conditional independence of LLM error streams is: "these models make errors for independent reasons." The alternative is: "they're all downstream of the same common cause." Sandy Island is ensemble reasoning without checking whether your sources are actually independent. The "multiple attestations" are a citation chain from 1876.

## Sources

- Geography Realm: Sandy Island propagation via World Vector Shoreline Database
- Bridle, James. "Trap Streets." *Cabinet Magazine* #47.
- Ancient Origins / Mexico News Daily: Bermeja
- Wikipedia / Atlas Obscura: Argleton
