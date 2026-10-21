# 04 — Choosing a Tool and Example Workflow

[Back to README](../README.md) | [Previous: Companies and Ecosystem](03-companies-ecosystem.md) | [Next: Limitations and Interpretation](05-limitations-and-interpretation.md)

## Selection guide

| Research question | Recommended starting point |
|---|---|
| Highest accuracy for a single protein with known homologs | **AlphaFold2** |
| Protein–drug, protein–DNA/RNA, or protein–protein complex | **AlphaFold3** or **RoseTTAFold All-Atom** |
| Rapid screening of millions of sequences | **ESMFold** or **OmegaFold** |
| Orphan proteins without useful MSAs | **ESMFold** or **OmegaFold** |
| Open-source, modifiable AlphaFold-style pipeline | **OpenFold** or **RoseTTAFold** |
| Antibody–antigen or specialized complex prediction | **Chai-1**, AlphaFold3, or specialized pipelines |

## Example workflow

1. **Define the biological question.**
   - Monomer structure?
   - Complex assembly?
   - Ligand binding?
   - Large-scale screening?

2. **Check sequence homology and available MSAs.**
   - Rich homology: AlphaFold2 is often a strong default.
   - No useful homology: consider ESMFold or OmegaFold.

3. **Run one or more models.**
   - Use AlphaFold2 for a high-confidence monomer baseline.
   - Use AlphaFold3 or RoseTTAFold All-Atom for complexes.

4. **Inspect confidence metrics.**
   - Review pLDDT for local confidence.
   - Review PAE for domain and chain placement.
   - Treat low-confidence regions as hypotheses.

5. **Validate experimentally where possible.**
   - Use structural biology, biochemistry, or functional assays as appropriate.
