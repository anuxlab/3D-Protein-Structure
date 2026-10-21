# 01 — Overview: AI and Protein Structure Prediction

[Back to README](../README.md) | [Next: Major AI Systems](02-major-ai-systems.md)

## The protein folding problem

A protein's function is closely tied to its three-dimensional structure. Predicting that structure from the amino acid sequence has been a long-standing challenge in biology.

Modern AI systems can now generate atomic-level structural models with remarkable speed and accuracy. The task has moved from a decades-long challenge toward a routine computational workflow, especially for proteins with available evolutionary information.

## Core concepts

### Multiple Sequence Alignment (MSA)

Many high-accuracy models use MSAs to identify evolutionary covariation between residues. This information helps constrain structure prediction.

- **Strength:** High accuracy when homologs are available.
- **Limitation:** MSA construction can be expensive and may fail for orphan proteins.

### Single-sequence prediction

Some models use protein language models to predict structure directly from a single sequence.

- **Strength:** Fast and scalable.
- **Limitation:** Often trades some accuracy for speed and independence from MSAs.

### Diffusion-based co-folding

Newer systems use diffusion-based architectures to predict raw atom coordinates and to model complexes involving proteins, nucleic acids, ions, and small molecules.

## What these systems predict

- Single-chain protein structures
- Protein complexes
- Protein–ligand interactions
- Protein–nucleic acid complexes
- Antibody–antigen complexes in some specialized workflows

## Key confidence concepts

- **pLDDT:** Predicted local-distance difference test. Indicates confidence in local geometry.
- **PAE:** Predicted aligned error. Useful for assessing inter-domain or inter-chain confidence.
- **TM-score:** A structural similarity metric often used in benchmarks.

> A high confidence score indicates model confidence, not necessarily biological or functional correctness.
