# 01 — Overview: AI and Protein Structure Prediction

[Back to README](../README.md) | [Next: Major AI Systems](02-major-ai-systems.md)

## The protein folding problem

A protein's function is closely tied to its three-dimensional structure. Predicting that structure from the amino acid sequence has been a long-standing challenge in biology.

Anfinsen's dogma suggested that the 3D structure of most natural proteins is determined by its amino acid sequence alone, implying that structure should be predictable from sequence[reference:0]. Levinthal's paradox highlighted the astronomical number of potential configurations a protein could adopt, framing folding as a computational problem of predicting a complex 3D shape from a linear string[reference:1].

Modern AI systems can now generate atomic-level structural models with remarkable speed and accuracy. The task has moved from a decades-long challenge toward a routine computational workflow, especially for proteins with available evolutionary information.

## Core concepts

### Multiple Sequence Alignment (MSA)

Many high-accuracy models use MSAs to identify evolutionary covariation between residues. If two positions are in contact, mutations at one position are often compensated at the other to maintain function; statistically observed pairs of residues that "change together" across evolution often denote contact[reference:2].

- **Strength:** High accuracy when homologs are available.
- **Limitation:** MSA construction can be expensive and may fail for orphan proteins.

### Single-sequence prediction

Some models use protein language models to predict structure directly from a single sequence.

- **Strength:** Fast and scalable.
- **Limitation:** Often trades some accuracy for speed and independence from MSAs.

### Diffusion-based co-folding

Newer systems use diffusion-based architectures to predict raw atom coordinates and to model complexes involving proteins, nucleic acids, ions, and small molecules. AlphaFold3 is a prominent example, and several open and commercial models now follow this paradigm.

## What these systems predict

- Single-chain protein structures
- Protein complexes (homo- and hetero-oligomers)
- Protein–ligand interactions
- Protein–nucleic acid complexes
- Antibody–antigen complexes in specialized workflows
- Covalent protein–ligand complexes (emerging benchmarks)

## Key confidence concepts

| Metric | What it measures | Key caveat |
|---|---|---|
| **pLDDT** | Predicted local-distance difference test; confidence in local geometry | High pLDDT does not guarantee biological or functional correctness |
| **PAE** | Predicted aligned error; expected positional error when aligning on one residue and evaluating another | Can reflect genuine protein flexibility rather than model error |
| **pTM / ipTM** | Predicted template modeling score; global and interface confidence | Useful for ranking, but can have high recall and lower precision |
| **DockQ / pDockQ2** | Interface quality for complexes | Especially relevant for antibody–antigen and protein–protein interfaces |

> Confidence scores are most informative when combined with experimental data, ensemble-sensitive measurements (e.g., NMR), and biological context[reference:3].
