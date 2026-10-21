# 05 — Limitations and Interpretation

[Back to README](../README.md) | [Previous: Choosing a Tool](04-choosing-a-tool.md)

## Key limitations

- **Confidence is not correctness.** A high pLDDT score indicates confidence in local geometry, not biological or functional correctness.
- **Static structures.** Most models predict a single static conformation and do not capture protein dynamics.
- **Disorder.** Intrinsically disordered regions are often poorly modeled or may receive misleadingly plausible coordinates.
- **Complexes are harder.** Multi-chain and ligand-bound predictions depend strongly on the model and input quality.
- **MSA dependence.** MSA-based models can fail when homologs are unavailable.
- **Single-sequence trade-offs.** Language-model-based methods are fast but may be less precise in some cases.

## Interpretation checklist

1. Check **pLDDT** per residue.
2. Check **PAE** for inter-domain and inter-chain confidence.
3. Identify low-confidence loops, termini, and disordered regions.
4. Compare predictions across models when the result is decision-critical.
5. Treat predicted complexes and ligand poses as hypotheses requiring validation.

## Bottom line

AI protein structure prediction is a powerful toolkit. AlphaFold2, AlphaFold3, RoseTTAFold, and ESMFold represent core methodologies, and newer models continue to expand the ecosystem. The best approach is usually to combine tools, inspect confidence metrics, and validate biologically important predictions.
