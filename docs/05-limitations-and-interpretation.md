# 05 — Limitations and Interpretation

[Back to README](../README.md) | [Previous: Choosing a Tool](04-choosing-a-tool.md) | [Next: Applications](06-applications.md)

## Fundamental limitations

### Confidence is not correctness

A high **pLDDT** score indicates confidence in local geometry, not biological or functional correctness. Low pLDDT can conflate **intrinsic disorder, MSA sparsity, and model uncertainty**[reference:75].

**PAE** reflects positional uncertainty when aligning on one region and evaluating another. Importantly, **PAE does not necessarily indicate a prediction error; it can reflect genuine flexibility of the protein**[reference:76]. For some classes of proteins—such as autoinhibited proteins with large-scale allosteric transitions—PAE can be a more reliable indicator of structural similarity to experimental data than pLDDT[reference:77].

### Static structures and missing dynamics

Most current models predict a **single static conformation** and do not capture protein dynamics. Key gaps include:

- **Intrinsically disordered proteins (IDPs) and disordered regions (IDRs):** These exist as dynamic ensembles of conformations and are not well represented by a single structure[reference:78].
- **Alternative conformations:** Bias from specific conformational states present in training data can prevent sampling of alternative states[reference:79].
- **Folding kinetics and pathways:** Models do not resolve folding pathways or the mechanisms of allostery and frustration, which are rooted in ensembles and dynamic distributions[reference:80].
- **Environmental effects:** Predictions generally do not account for chaperone interactions, post-translational modifications, macromolecular crowding, or cellular conditions[reference:81].

### Multi-state and conformational bias

Benchmarks on **multi-state proteins** (e.g., Pf-MATE, LAO, SecA, β₂AR) have revealed a **persistent state bias** in AI predictors: models often favor one conformational state over others, and sampling breadth varies across methods[reference:82]. This is a critical caveat for drug discovery, where **cryptic pockets** and **allosteric sites** may only be visible in specific conformations.

### Complex and interaction prediction is harder

- **Antibody–antigen interfaces** remain challenging; confidence scores can reflect structural plausibility without binding specificity[reference:83].
- **RNA prediction** remains difficult even for AlphaFold3[reference:84].
- **Stoichiometry prediction** for heteromeric complexes is limited[reference:85].
- **Covalent protein–ligand complexes** are an emerging benchmark area, and performance varies across co-folding models[reference:86].

### Missing small molecules and waters

Both predicted and experimental structures often **lack waters or other small molecules** that are essential for understanding mechanisms; predictions are improving in this regard, but the gap remains[reference:87].

## Interpretation checklist

1. **Check pLDDT per residue** to identify low-confidence loops, termini, and disordered regions.
2. **Check PAE** for inter-domain and inter-chain confidence; treat high PAE as possible flexibility, not just error.
3. **For complexes, combine interface metrics:** pDockQ2 for precision and pTM for recall; consider composite scores like AntiConf for antibody–antigen work[reference:88].
4. **Compare predictions across models** when the result is decision-critical; no single method dominates across all target classes[reference:89].
5. **Treat predicted complexes and ligand poses as hypotheses** requiring experimental validation.
6. **Be explicit about what is not modeled:** dynamics, alternative conformations, environmental context, and folding pathways[reference:90].

## Bottom line

AI protein structure prediction is a powerful toolkit. **AlphaFold2, AlphaFold3, RoseTTAFold, ESMFold/ESMFold2, and co-folding models such as Chai-1, Boltz, and Protenix** represent core methodologies, and newer models continue to expand the ecosystem. The best approach is usually to **combine tools, inspect confidence metrics in context, and validate biologically important predictions**—while remaining aware that a static, high-confidence model is not the same as a mechanistic or functional understanding of the protein.
---

[Back to README](../README.md) | [Next: Applications](06-applications.md)
