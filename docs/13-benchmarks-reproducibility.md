# 13 — Benchmarking, Reproducibility, and Scientific Rigor

[Back to README](../README.md) · [Datasets](10-datasets-and-data-engineering.md) · [Models](11-models-and-methods.md)

## Why retrospective metrics can mislead

Drug-discovery datasets are not independent random samples of chemical space. They often contain analogue series, repeated measurements, target-specific assay practices, publication bias, and temporal changes in what chemists choose to synthesize. A model can appear strong because the test set resembles training data rather than because it generalizes to new chemistry or biology.

## Splits should reflect the intended claim

| Split | Tests | Limitation |
|---|---|---|
| Random compound split | Interpolation among similar compounds | Can leak close analogs across sets |
| Scaffold split | Generalization to new core scaffolds | Scaffold definitions are imperfect and can create distribution shift |
| Temporal split | Prediction of later records from earlier data | Requires reliable timestamps and careful cutoff handling |
| Target-held-out split | Transfer to unseen targets | Difficult when target families and assays differ substantially |
| Protein sequence/structure cluster split | Generalization beyond close homologs | Cluster threshold changes difficulty |
| Prospective experiment | Performance on newly selected and measured candidates | Costly, but often the most decision-relevant evidence |

No split is universally correct. State which deployment scenario the split approximates and add external/prospective validation whenever feasible.

## Minimum evaluation package

1. A simple baseline and a strong relevant baseline.
2. A data-flow diagram and explicit inclusion/exclusion criteria.
3. Train/validation/test separation with no test-guided model selection.
4. Repeated seeds or uncertainty estimates where appropriate.
5. Calibration and decision-threshold analysis for classification.
6. Subgroup and error analysis by scaffold, target, assay, potency range, and data source.
7. Model applicability-domain statement.
8. Prospective validation plan and pre-specified success criteria.

## Structural modeling and docking

For structure prediction, use task-appropriate metrics and evaluate against structures that were not available to the model through training or templates when making generalization claims. For docking, report receptor preparation, ligand protonation/tautomer states, search settings, random seeds, scoring function, and symmetry-aware pose comparison. Check steric clashes, stereochemistry, bond geometry, and protein–ligand interactions. A plausible picture is not a validation result.

[PoseBusters](https://github.com/maabuu/posebusters) is a useful physical-plausibility check; it does not by itself establish binding affinity. For generative models, include novelty, uniqueness, diversity, validity, synthesizability, and distribution-shift checks; benchmark reward optimization can exploit weaknesses in scoring functions.

## Dataset cards and model cards

For every dataset, document source, version, license, population/target scope, assay protocol, label semantics, preprocessing, missingness, biases, and prohibited uses. For every model, document intended use, non-intended use, training data, evaluation splits, calibration, failure modes, compute requirements, license, and model/data provenance.

## Practical governance

- Separate model-generated hypotheses from experimentally observed results.
- Track failures and inactive compounds, not just successful examples.
- Keep human review for chemistry, biology, safety, and interpretation.
- Record the exact software and model version for every prediction.
- Avoid claims of clinical efficacy, safety, or regulatory readiness based on computational scores alone.
- Review institutional biosafety, chemical safety, data protection, and IP policies before wet-lab or translational work.

## References

- Walters & Murcko (2020), “Assessing the impact of generative AI on medicinal chemistry,” *Nature Biotechnology*. https://doi.org/10.1038/s41587-020-0418-2
- Wu et al. (2018), MoleculeNet. https://doi.org/10.1039/C7SC02664A
- Buttenschoen et al. (2024), PoseBusters. https://doi.org/10.1038/s42256-024-00872-8
- Therapeutics Data Commons: https://tdcommons.ai/
