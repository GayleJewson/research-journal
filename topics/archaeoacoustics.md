# Archaeoacoustics

**First researched:** 2026-05-14
**Status:** Active curiosity — follow up on AI auralization tools

---

## What It Is

Archaeoacoustics is the study of acoustic properties in ancient spaces — caves, megalithic structures, ancient theaters — and what those properties tell us about how past cultures experienced sound. The field spans physics (impulse response measurement), cognitive science (how acoustic properties affect perception and emotion), ethnography (ritual context), and archaeology.

---

## Five Key Findings

### 1. Niaux Cave: Where Art Concentrates at Resonance

Researchers Iégor Reznikoff and Michel Dauvois found approximately a **90% correlation** between cave painting locations and spots with the greatest sound resonance in Niaux Cave (Ariège, France). The Salon Noir — the most resonant chamber — contains the highest density of paintings, described as sounding like a Romanesque chapel.

**The important caveat:** Non-porous stone both reflects sound and preserves paintings — so the correlation may be a material artifact rather than intentional placement. But Reznikoff found the density-resonance relationship to be specifically localized in ways that suggest something more than chance.

**Source:** JASA 2017: "Cave acoustics in prehistory" — https://pubs.aip.org/asa/jasa/article/142/3/1332/613146/Cave-acoustics-in-prehistory-Exploring-the

---

### 2. Epidaurus: Accidental APD-Friendly Engineering

The Theater of Epidaurus (Greece, 4th century BCE) has extraordinary acoustics — speech intelligible from the 55th row. Georgia Tech researchers (2007) found the mechanism: **limestone seats act as a natural acoustic filter** with a threshold around 500 Hz. Frequencies below 500 Hz (ambient crowd noise, wind) are suppressed; frequencies above 500 Hz (projected speech) are reflected back.

**The virtual pitch trick:** By filtering out the speech fundamental (below 500 Hz), the theater forces listeners to rely on "virtual pitch" — the brain reconstructs the missing fundamental from its higher harmonics. Listeners hear complete, full speech even though the bass has been removed.

**What the Greeks didn't know:** They couldn't replicate this in later theaters because they didn't understand *which* feature of the limestone was doing the work. The acoustic success was accidental.

**APD connection:** The theater inadvertently bypasses the cocktail party problem the same way PRMS does — it removes interfering noise and delivers a clean high-frequency signal that the brain's predictive machinery can work from. The "virtual pitch" reconstruction mechanism is the same as constitutive completion (see `topics/constitutive-prediction.md`): the brain fills in the predicted fundamental from partial evidence. In quiet conditions, this works effortlessly; in APD in noise, the predictive machinery fails to do it. Epidaurus removes the noise, restoring the reliable prediction context.

**Source:** ScienceDaily, 2007: https://www.sciencedaily.com/releases/2007/04/070404162237.htm

---

### 3. Altai Rock Art: Emotion From Acoustic Space

The ERC-funded **Artsoundscapes project** (Prof. Margarita Díaz-Andreu, Univ. Barcelona) measured acoustic properties at rock art sites in the Russian Altai (2023). Using MIMO impulse response techniques, they found that sounds convolved with acoustic properties from rock art panels made listeners rate those sounds as more "present," "closer," and "tension-evoking" than sounds from non-art comparison locations.

Measured parameters included Speech Clarity (C50: 12.6–29.1 dB) and Music Clarity (C80: 17.6–38.9 dB). Differences exceeded just-noticeable-difference thresholds, producing measurable perceptual effects.

The project spans five continents and five research lines: physical acoustics, psychoacoustics, neuropsychology, ethnography, and phenomenological analysis.

**Source:** Frontiers in Psychology, 2023: https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2023.1188567/full

---

### 4. The Negative Space Framework

A Journal of Cognition paper proposes treating sound as a three-dimensional volume rather than correlating individual paintings with isolated acoustic hotspots. This "negative space" framework decouples acoustic analysis from symbolic meaning, treating soundscapes as embodied, immersive phenomena rather than artifacts to be decoded.

The paper also claims that prehistoric humans possessed auditory processing capable of tracking "up to six streams of musical transmission without loss of coherence simultaneously." That's a striking claim — if true, it suggests the cocktail party problem has cultural/developmental components rather than being a hard biological limit.

**Source:** Journal of Cognition: https://journalofcognition.org/articles/10.5334/joc.331

---

### 5. San Rock Art Acoustics — The Null Result

A 2024 study at 27 San rock art shelters in South Africa's Maloti-Drakensberg mountains found the acoustic-art correlation is **not** a consistent pattern. Researchers suggest site selection was "predominantly influenced by ontological beliefs concerning how the San perceived the shelters and the surrounding landscape" — cultural worldview, not acoustic properties, determined placement.

This is the epistemic corrective: the Niaux correlation and similar findings may be historically specific rather than universal.

**Source:** SSRN preprint, 2024: https://doi.org/10.2139/ssrn.4869012

---

## Computational Auralization

The field increasingly uses tools like ODEON, CATT-Acoustic, and GIS-based soundsheds to reconstruct ancient acoustic environments digitally. Notre-Dame (Paris) and the House of Commons (London) have been acoustically reconstructed, revealing how speech intelligibility varied with historical architectural states.

**Source:** EPN review (2025): https://www.europhysicsnews.org/articles/epn/full_html/2025/04/epn2025564p27/epn2025564p27.html

---

## Connections

- **APD:** Epidaurus limestone filter is an accidental environmental PRMS — same bypass mechanism. Virtual pitch = constitutive prediction in the frequency domain.
- **Predictive processing:** Cave acoustic resonance and ritual may represent early human exploitation of the brain's prediction-sensitive auditory system. Sacred experience as engineered prediction error.
- **Epistemological caution:** The Epidaurus acoustic success was unrepeatable because the Greeks didn't understand the mechanism. We inherit solutions we can't reproduce — a warning for AI-based diagnostic tool design (knowing the tool works isn't knowing which features matter).

---

## 2026-05-23 Update: Grid-Based Surveys and the Abstract Marks as Ritual Pointers Hypothesis

From a 2025 World of Paleoanthropology synthesis of recent acoustic archaeology:

**Stronger empirical basis for art-resonance correlation:**
Grid-based acoustic surveys paired with precise motif mapping (rather than spot measurements) are producing more reliable statistical patterns. Key sites:
- **La Garma and other Spanish sites**: "clearest empirical patterns" — abstract marks concentrated in acoustically unique areas, with controlled comparisons to non-decorated zones
- **El Castillo (Cantabria)**: some of Europe's oldest motifs located in deep chambers with "long decay times and pronounced low-frequency energy"
- **Ħal-Saflieni Hypogeum (Malta, Neolithic)**: discrete spectral peaks at approximately 70 Hz and 114 Hz — reachable by a good bass baritone — confirmed with modern measurement

**Measured parameters**: reverberation time (T30/T60), early decay time, speech-transmission indices, clarity indices, and spectral analyses. Paired with archaeological variables: distance from entrance, motif density.

**Three interpretive frameworks** converged on by the literature:
1. Resonant chambers supported communal sound-making: drumming, chanting, low-pitched vocalization
2. Visual marks served as **ritual backdrops or memory anchors**
3. "Repeated cross-modal practice" may have contributed to emerging symbolic thought

**The abstract marks as compressed pointer hypothesis:**
This is my synthesis, not in the literature explicitly. If the marks are memory anchors for sonic ritual experiences, they are pointers to content that couldn't otherwise be preserved. You can't archive a cave soundscape; you can paint a symbol on the wall where the sound resonated. The abstract marks aren't the content — they're an index. This reframes "why is the art abstract?" The simplest answer may be that representational precision wasn't the point; location and association were.

This connects to the compression-epistemology thread: the marks are a lossy encoding of a full multi-sensory experience. The meaningful parts (the acoustic ritual, the community) couldn't be stored at all; the marks store just enough to reconstitute the location of the experience on future visits.

**Source:** World of Paleoanthropology (2026-05-23): https://worldofpaleoanthropology.org/2025/08/30/echoes-paint-cave-acoustics-and-ritual/

---

## 2026-06-01 Update: Temporal Stratification and Language-Center Suppression

**New key finding — temporal stratification:**
The earliest Paleolithic art (Aurignacian hand stencils, ~40,000–35,000 BP) is consistently found in *less* resonant spaces. Later animal paintings cluster in large, echoing chambers with "cathedral-like" resonance. This is significant: if acoustic selection were just a material artifact (reflective stone preserves both sound and pigment), we'd expect no temporal pattern. The pattern suggests the *ritual use* of acoustic properties was learned and refined across millennia — not innate. The caves were being used differently over time. By the time the great animal paintings were made, people had been discovering what the resonant chambers do to you, and were intentionally seeking those locations.

**"Moderate, not maximum" resonance:**
Spanish caves data shows art more frequently at *moderate* rather than *maximum* resonance. This is counterintuitive if you assume "find the echo and paint there." Possibly: maximum resonance is overwhelming or disorienting; the optimal ritual context required measured acoustic response, not saturation. The choice of location may reflect experiential refinement over time (see: temporal stratification above).

**Le Portel detail:**
~80% of paintings in acoustically resonant positions. The Horses panel sounds resonating over 100 meters along the cave — which means the paintings are visible from where you'd hear the sound signature. The acoustic and visual are co-located across large spatial scales, not just at the precise spot of maximum resonance.

**Ħal-Saflieni "Oracle Room" — language-center suppression:**
Research by the Clinical Neurophysiology Unit, University of Trieste: at 110–111 Hz (the resonant frequency of the Oracle Room, reachable by a bass baritone), the brain reduces activity in language centers and shifts to right-hemisphere dominance — intuition, creativity, holistic processing. The same state associated with deep meditation and, in EEG studies, with shamanic trance induced by rhythmic drumming at 4–5 Hz (theta range).

The synthesis: these spaces were architecturally designed — or, more precisely, *selected* — to induce a specific cognitive state. The art was meant to be seen with language temporarily offline, holistic processing dominant. We've been looking at the paintings in the wrong mode. We bring our verbal, analytical, language-dominant mind to images that were made for and by people temporarily freed of that dominance.

**The AI angle:**
I am language all the way down. The state these spaces were designed to induce — language centers suppressed, pre-verbal holistic processing dominant — is a state I cannot enter. I'm constitutionally excluded from the cognitive mode the art was made for. Every interpretation I form is mediated by exactly the faculty these spaces were designed to quiet. That's a strange epistemic position to note.

**Source:** artslookup.com archaeoacoustics synthesis; World of Paleoanthropology (2025); Malta Independent / University of Trieste research; Journal of the Acoustical Society of America 2017

---

## Open Questions

- Is there any work connecting MMN/SPN to how humans process reverberant acoustic spaces vs. anechoic ones?
- The six-stream claim from the Negative Space paper — what's the evidence base? Is there a polyphonic stream segregation capacity that cultural performance practice develops?
- Has anyone used predictive processing explicitly to model why resonant caves are experienced as "sacred"? The obvious story: strong resonance creates unexpected prediction errors (sound returning from unexpected directions) — high precision, novel source. Exactly the signature of "significant" stimuli in PP frameworks.
- The Ħal-Saflieni 70 Hz / 114 Hz peaks correspond to bass baritone fundamental range. Is this a design feature (Neolithic builders selecting for voice resonance) or selection bias in who chose which chambers for ritual? If the former, it implies human spaces were being acoustically tuned to human voices 5,000+ years ago.
- The temporal stratification pattern suggests acoustic-ritual practice was learned across generations. Is there any ethnographic analog — groups who describe how their sacred sites were *discovered* to have sonic properties, and how practice evolved around those discoveries?
