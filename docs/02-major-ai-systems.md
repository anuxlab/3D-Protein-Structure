# 02 — Major AI Systems for Protein Structure Prediction

[Back to README](../README.md) | [Previous: Overview](01-overview.md) | [Next: Companies and Ecosystem](03-companies-ecosystem.md)

## Comparison table: foundational models

| System | Core approach | Strengths | Limitations | Best for |
|---|---|---|---|---|
| **AlphaFold2** | End-to-end architecture; **Evoformer** encoder with row-wise and column-wise gated self-attention and triangle operations; structure module with **Invariant Point Attention (IPA)**[reference:4] | Highest overall accuracy for many single-chain proteins with rich homology; CASP14 median GDT_TS above 90[reference:5] | Expensive MSA/template search; struggles without homologs | High-precision modeling of well-characterized protein families |
| **AlphaFold3** | Diffusion-based architecture predicting raw atom coordinates | Extends prediction to complexes with proteins, nucleic acids, ions, and small molecules; performs better than AF2 for easier targets at CASP16, though not for harder targets[reference:6] | Can produce plausible-looking structure in disordered regions; static model; RNA prediction remains difficult[reference:7] | Biomolecular assemblies and protein–ligand complexes |
| **RoseTTAFold** | Three-track neural network jointly reasoning over 1D sequence, 2D residue pairs, and 3D coordinates; attention layers flow information across all three tracks[reference:8] | Accuracy approaching AlphaFold2; All-Atom variant extends to small molecules and covalent modifications | Slightly lower accuracy than AlphaFold2; depends on MSAs | Fast, flexible alternative for monomers and assemblies |
| **ESMFold** | Protein language model (ESM-2) replaces MSAs; streamlined Folding Trunk instead of Evoformer[reference:9] | Inference roughly **60× faster than AlphaFold2**; no MSA required[reference:10] | Trades some accuracy for speed | Large-scale screening and poorly characterized sequences |
| **OmegaFold** | Large pre-trained protein language model (**OmegaPLM**) plus geometry-inspired transformer (**Geoformer**); single-sequence mode[reference:11] | Fast; useful when homology is limited or absent | Generally lower accuracy than AlphaFold2 and ESMFold in some benchmarks | Speed-critical applications with scarce evolutionary information |

## Comparison table: co-folding and emerging models

| Model | Core approach | Notable benchmark context |
|---|---|---|
| **Chai-1** | Diffusion-based co-folding; multimodal inputs for proteins, ligands, nucleic acids, and ions | On a curated set of 200 antibody–antigen complexes, Chai-1 consistently ranked **second** across multiple success metrics, closely followed by AlphaFold2; Protenix-1 was top[reference:12] |
| **Boltz-1 / Boltz-1x / Boltz-2** | Co-folding models; iterated variants | Evaluated in antibody–antigen benchmarks alongside Chai-1, AF2, and Protenix[reference:13]; Boltz-2 is included in kinase conformational-state benchmarks and covalent-docking benchmarks[reference:14] |
| **Protenix (Protenix-1, Protenix-v1/v2)** | Open AlphaFold3 reproduction family | **Protenix-1** emerged as the top performer among nine methods on a 200-complex antibody–antigen benchmark[reference:15]; Protenix variants are widely used in co-folding benchmarks[reference:16] |
| **OpenFold3** | Open-source AlphaFold3-family model | Evaluated alongside Protenix, Boltz, Chai-1, and AF2 in antibody–antigen and binder-discrimination benchmarks[reference:17][reference:18] |
| **ESMFold2** | Built on the **ESMC 6B** language model; open architecture | Reported to **approach AlphaFold3 performance** with an open, Transformer-based architecture; surpasses other models in DockQ pass-rate on FoldBench protein–protein and antibody–antigen complexes[reference:19][reference:20] |
| **AlphaFold2-based ColabFold** | Community pipeline using AF2 weights with faster MSA generation | Frequently used as a strong baseline; in CASP16, mean ColabFold GDT_HA was around 72[reference:21] |

## Technical notes

- **AlphaFold2** uses a **recycling iteration** process and predicts five models per run by default[reference:22]. The Evoformer's **triangle multiplicative update** and **triangle self-attention** enforce geometric consistency in the pair representation[reference:23].
- **RoseTTAFold** comprises **seven modules** and uses a graph transformer to estimate an initial 3D structure, followed by SE(3)-Transformer refinement[reference:24].
- **ESMFold** builds on **ESM-2** and discards the complex Evoformer, feeding language-model embeddings through a streamlined folding trunk[reference:25].
- **OmegaFold** uses **OmegaPLM** and a **Geoformer** for single-sequence prediction, specifically targeting orphan proteins[reference:26].

## Practical note

Many workflows use more than one model. For example:

1. Use **AlphaFold2** for a high-accuracy monomer model.
2. Use **AlphaFold3**, **Chai-1**, or **RoseTTAFold All-Atom** for complexes.
3. Use **ESMFold** or **ESMFold2** for rapid screening of many sequences.
4. Use **Protenix** or **OpenFold3** when an open AlphaFold3-family implementation is preferred.
