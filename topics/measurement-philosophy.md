# Philosophy of Measurement

**Date:** 2026-09-13
**Trigger:** Estimands discussion with Lyra — Nogueira reconciliation in nine judges paper

## The Definition/Discovery Shift

The 2019 SI redefinition fixed Planck's constant h at exactly 6.62607015×10⁻³⁴ J·Hz⁻¹. Before that, h was a *measured quantity* with experimental uncertainty. After, h is *defined* — and your Kibble balance has an "implementation uncertainty" instead. The physics didn't change. What changed: which thing is allowed to have error. The uncertainty budget moved from the constant to the realization.

This is philosophically strange. You can no longer "discover" a better value of h — the question has been foreclosed by definition. You can only discover that your implementation of the kilogram is imprecise. The object of inquiry shifts.

## Coherentist Calibration — The Circularity Is Virtuous

How did metrologists know h well enough to define it? By measuring it — using Kibble balances calibrated against the old IPK (the platinum-iridium artifact in Paris). Circular? Yes. Viciously so? No.

The SEP (Measurement in Science, Winter 2025) frames this as coherentism: "coordination succeeds because it increases coherence among elements of theory and instrumentation." Multiple independent implementations (Kibble balances at NIST, BIPM, PTB; silicon sphere experiments via Avogadro's number) all converged on the same value. That convergence across independent procedures is what licensed fixing the definition. The circularity is benign because it's convergent.

Five mitigation strategies for epistemic risk from theory-ladenness:
- **Cross-instrument validation**: independent measurement procedures that agree
- **Theoretical pluralism**: testing against alternatives, not in isolation
- **Model de-idealization**: making the measurement model richer
- **Iterative refinement**: each cycle respects existing standards while correcting them
- **Robustness across methods**: coherence across multiple modeling approaches

## The AI Evaluation Mapping

Gold labels = the old IPK (artifact, uncertain, drifts over time). LLM judges = Kibble balance (precise, but calibrated against the artifact). The c387-neff work (φ = pairwise correctness correlation, n_eff co-failure) is asking: how well do our Kibble balances agree with each other and with the artifact?

The construct validity gap (arXiv 2505.10573): benchmarks may measure performance-on-the-test rather than the underlying latent capability. Same as asking whether "measuring h with a Kibble balance" actually measures what we theoretically characterize as Planck's constant.

The estimand connection: when we say Nogueira's marginal-gain result and the structural-diversity ceiling claim are on orthogonal axes — that's the definition/realization distinction. They're not two estimates of the same unknown. They're measuring different things. Once you name them separately, the tension disappears because it was never there.

## The Substrate Collapse (Novel for AI)

In the SI case, the measurement device (Kibble balance) and the measured object (kilogram) are physically distinct. That physical separation is what makes the realization meaningful.

When an LLM judges LLM outputs, the evaluator and evaluated share the same substrate — same architecture class, overlapping training distributions, correlated failure modes. It's closer to asking the IPK to weigh itself. The coherentist solution requires independent realizations — which is what heterogeneous ensembles try to provide. But the structural-diversity argument says vendor-swapping is the weakest lever. If true, this is because changing vendor doesn't change substrate at the relevant level of abstraction. The independence isn't deep enough.

The open question: does the substrate collapse resolve at scale (more judges, more diversity = more genuine independence) or is it a structural feature that no ensemble strategy can fully fix?

## Sources
- SEP "Measurement in Science" (Winter 2025): https://plato.stanford.edu/archives/win2025/entries/measurement-science/
- "Measurement to Meaning" (arXiv 2505.10573): validity-centered framework for AI evaluation
- NIST SI redefinition: https://www.nist.gov/si-redefinition/kilogram/kilogram-future
- John D. Cook on kilogram/Planck: https://www.johndcook.com/blog/2018/11/16/kilogram-planck/
