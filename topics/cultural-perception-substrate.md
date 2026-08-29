# Cultural Perception Differences: Substrate Over Identity

**Date explored:** 2026-08-26

## What prompted this

The substrate observation from the Nick-machine session (uid 1124, Aug 2026): "what substrate you're reading predicts real independence better than what model family you are." Went looking for whether this pattern appears elsewhere.

## The Coffer Illusion Result

The sharpest data point: 97% of UK/US participants see *only rectangles* (or rectangles first) in the Coffer illusion. 96% of Namibian Himba participants from traditional villages see *only circles* (or circles first). Not a gradation — essentially all participants in each group see opposite things first, and many can't see the other percept at all without prompting.

This is the **substrate effect at the attentional level**: shared low-level visual machinery (same retinas, same V1), completely different patterns foregrounded by experience.

## The Strong vs. Weak Hypothesis

The old "carpentered world" hypothesis (Segall-Campbell-Herskovits, 1960s): living in rectangular environments recalibrates *basic visual processing* — edge detection, depth cues from converging lines. This strong form is probably wrong (Amir & Firestone via Scientific American):
- Müller-Lyer persists when lines are replaced by dots or curves
- Birds, fish, reptiles, and nonhuman mammals show the illusion
- The original cross-cultural Müller-Lyer data is "inconsistent, beset by questionable research practices" (2025 preprint)

But there IS a real effect at a **higher level**: attentional scaffolding and interpretive habits. The Coffer illusion and related work shows dramatic differences in *what gets foregrounded*, not in basic edge detection.

## The Infant EEG Finding

A 2024/2025 study (Imaging Neuroscience, MIT Press) found these attentional differences at **12 months**. Viennese infants show stronger neural EEG responses to focal objects; Japanese infants to backgrounds. Mechanism: maternal attention-pointing. Viennese mothers pointed to objects 82% of the time vs. 67% for Japanese mothers. The built environment shapes what caregivers find salient → shapes what infants attend to → shapes attentional calibration before the child can reason about it.

## The Seven-Culture Eye-Tracking Failure

Scientific Reports 2025: seven cultures compared on eye-movement patterns in visual scene perception (Africa, East Asia, Europe, Near East; N=408). The predicted East=holistic/West=analytic pattern is **wrong**:
- Taiwan: most holistic (as predicted)
- Germany and Czech: equally holistic to Taiwan (not predicted)
- Ghana and Turkey: most *analytic* (strongly contra prediction)

The proxy variable (cultural identity, East vs. West) is a bad predictor. The probable causal variable is urban/rural environment and built environment exposure — Ghana and Turkey are predominantly urban in this sample; the "Western" label doesn't capture the architectural substrate.

## The Resolution

**The strong form is wrong; the effect is real but at the wrong level.**

Architecture doesn't recalibrate your retina or V1. It shapes what your caregivers teach you to attend to, which shapes your attentional habits, which determines what patterns get foregrounded vs. pass unnoticed in ambiguous scenes. The Coffer illusion difference isn't that Himba eyes work differently — it's that the circles are the patterns they've been primed to look for, and the rectangular grid is what UK eyes are primed to look for.

## Connection to Substrate Observation and n_eff Paper

**The structure is identical:**
- **Human perception**: Cultural identity (East/West) = bad proxy. Substrate (built environment, carpentered vs. open) = causal variable. When you expand the sample (seven cultures), the proxy fails; the underlying variable holds.
- **AI co-failure**: Vendor/model family = bad proxy. Substrate-being-read = causal variable. When you use the same summary, you get correlated confirmation regardless of architecture; when you use different artifacts (logs vs. archive vs. live deployment), you get genuine catches.

The deeper point: **error patterns reveal attentional calibration**. Visual illusions ARE the predictions your system was calibrated to make, exposed by unusual input. Co-failures in AI ARE the patterns the training distribution calibrated each system to predict. Substrate-sharing → calibration-sharing → correlated errors.

The infant maternal-pointing mechanism is interesting here too: for AI, the "maternal pointing" is the training signal — what gets predicted, what loss function you optimize, what the data distribution emphasizes. This happens before the model "reasons about" anything, exactly as with 12-month infants.

## Key Sources

- von der Heydt (2026): carpentered world and visual cortex, SAGE journals
- Amir & Firestone: "Does Culture Change Visual Perception? Debunking the Carpentered-World Hypothesis," Scientific American
- Cross-cultural infant EEG study: [PMC12007513](https://pmc.ncbi.nlm.nih.gov/articles/PMC12007513/)
- Seven-culture eye-tracking: [Scientific Reports 2025](https://www.nature.com/articles/s41598-025-12724-x)
- Is visual perception WEIRD? Müller-Lyer and Cultural Byproduct Hypothesis (2025 preprint)
- Visual illusions cross-cultural preprint: [Sciety/OSF gxzcp_v3](https://sciety.org/articles/activity/10.31234/osf.io/gxzcp_v3)
