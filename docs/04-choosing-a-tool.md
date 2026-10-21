# 04 — Choosing a Tool and Example Workflow

[Back to README](../README.md) | [Previous: Companies and Ecosystem](03-companies-ecosystem.md) | [Next: Limitations and Interpretation](05-limitations-and-interpretation.md)

## Selection guide

| Research question | Recommended starting point | Rationale |
|---|---|---|
| Highest accuracy for a single protein with known homologs | **AlphaFold2** | Remains a strong default; CASP14 median GDT_TS >90[reference:56] |
| Protein–drug, protein–DNA/RNA, or protein–protein complex | **AlphaFold3**, **Chai-1**, **Protenix**, or **RoseTTAFold All-Atom** | Co-folding models extend prediction beyond proteins |
| Rapid screening of millions of sequences | **ESMFold** or **ESMFold2** | ESMFold is roughly 60× faster than AF2 and needs no MSA[reference:57]; ESMFold2 adds improved interaction benchmarks[reference:58] |
| Orphan proteins without useful MSAs | **ESMFold** or **OmegaFold** | Both use language models to bypass MSAs[reference:59] |
| Open-source, modifiable AlphaFold3-style pipeline | **OpenFold3** or **Protenix** | Open implementations of the AF3 family[reference:60] |
| Antibody–antigen or specialized complex prediction | **Protenix-1**, **Chai-1**, or **AlphaFold3** | On a 200-complex Ab–Ag benchmark, Protenix-1 was top and Chai-1 second[reference:61] |
| Covalent protein–ligand complexes | **AlphaFold3**, **Chai-1**, or **Boltz-1x** | Benchmarked in the CoFD-Bench covalent-docking dataset[reference:62] |

## Benchmark context

### CASP

CASP is a blind, biennial assessment of protein structure prediction. AlphaFold2's CASP14 performance was a step change: the median GDT_TS exceeded **90**, with an average only slightly below 90[reference:63]. CASP15 and CASP16 showed **further minor improvement**, and for many targets additional gains are likely limited by experimental accuracy[reference:64].

At **CASP16**, AlphaFold3 performed better than AlphaFold2 for **easier targets**, but not for **harder targets**[reference:65]. No single method dominated; the most accurate method across targets delivered better results than AlphaFold3 largely because it had **fewer poorly scoring targets**[reference:66]. RNA prediction remained difficult, and stoichiometry prediction was limited for heteromeric targets[reference:67].

### Antibody–antigen benchmarks

On a curated dataset of **200 antibody–antigen complexes**, nine methods were evaluated: AF2, Boltz-1, Boltz-1x, Boltz-2, Chai-1, Protenix, Protenix-1, OpenFold3, and ESMFold. **Protenix-1 ranked first**, **Chai-1 second**, and **AF2 third** across multiple success metrics[reference:68]. The study also introduced **AntiConf**, a composite score combining **pDockQ2** (high precision) and **pTM** (high recall) to improve confidence assessment for antibody–antigen predictions[reference:69].

### Kinase conformational states and covalent complexes

- **KinConfBench** evaluates co-folding models on **2,225 human kinase chains**; Boltz-2, Chai-1, and Protenix variants achieve roughly **60–80% accuracy** on kinase conformational classification[reference:70].
- **CoFD-Bench** evaluates covalent protein–ligand docking on **218 recently resolved covalent complexes**, comparing classical docking and deep-learning co-folding models including AlphaFold3, Chai-1, and Boltz-1x[reference:71].

## Example workflow

1. **Define the biological question.**
   - Monomer structure?
   - Complex assembly?
   - Ligand binding?
   - Large-scale screening?

2. **Check sequence homology and available MSAs.**
   - Rich homology: AlphaFold2 is often a strong default.
   - No useful homology: consider ESMFold, ESMFold2, or OmegaFold.

3. **Run one or more models.**
   - Use AlphaFold2 for a high-confidence monomer baseline.
   - Use AlphaFold3, Chai-1, or Protenix for complexes.
   - Use ESMFold2 for fast, open, language-model-based screening and design.

4. **Inspect confidence metrics.**
   - Review **pLDDT** for local confidence.
   - Review **PAE** for domain and chain placement; for some protein classes, PAE can be a more reliable indicator of structural similarity than pLDDT[reference:72].
   - For complexes, consider **pDockQ2** and **pTM/ipTM** together (e.g., AntiConf-style integration)[reference:73].

5. **Compare across models when decision-critical.**
   - Different top models can succeed or fail on different targets; a venue for progress is better identification of the best model among available predictions[reference:74].

6. **Validate experimentally where possible.**
   - Use structural biology, biochemistry, or functional assays as appropriate.
