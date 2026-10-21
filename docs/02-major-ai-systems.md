# 02 — Major AI Systems for Protein Structure Prediction

[Back to README](../README.md) | [Previous: Overview](01-overview.md) | [Next: Companies and Ecosystem](03-companies-ecosystem.md)

## Comparison table

| System | Core approach | Strengths | Limitations | Best for |
|---|---|---|---|---|
| **AlphaFold2** | MSA-based Evoformer and structure module | Highest overall accuracy for many single-chain proteins with rich homology | Expensive MSA/template search; struggles without homologs | High-precision modeling of well-characterized protein families |
| **AlphaFold3** | Diffusion-based architecture predicting raw atom coordinates | Extends prediction to complexes with proteins, nucleic acids, ions, and small molecules | Can hallucinate plausible structure in disordered regions; static model | Biomolecular assemblies and protein–ligand complexes |
| **RoseTTAFold** | Three-track neural network over sequence, residue interactions, and 3D coordinates | Accuracy approaching AlphaFold2; flexible alternative; All-Atom variant extends to small molecules | Slightly lower accuracy than AlphaFold2; depends on MSAs | Fast, flexible alternative for monomers and assemblies |
| **ESMFold** | Protein language model; single-sequence prediction | Very fast and scalable; no MSA required | Trades some accuracy for speed | Large-scale screening and poorly characterized sequences |
| **OmegaFold** | Language-model-based geometric transformers | Fast; useful when homology is limited | Generally lower accuracy than AlphaFold2 and ESMFold in some benchmarks | Speed-critical applications with scarce evolutionary information |

## Emerging and specialized models

| Model | Notes |
|---|---|
| **Chai-1** | Diffusion-based co-folding model for biomolecular complexes; supports multimodal inputs |
| **Boltz-1** | Co-folding model for biomolecular complexes |
| **OpenFold** | Open-source reproduction of AlphaFold2 architecture |
| **ESMFold2** | Newer ESMFold iteration reported to improve speed and some interaction benchmarks |

## Practical note

Many workflows use more than one model. For example:

1. Use **AlphaFold2** for a high-accuracy monomer model.
2. Use **AlphaFold3** or **RoseTTAFold All-Atom** for complexes.
3. Use **ESMFold** for rapid screening of many sequences.
