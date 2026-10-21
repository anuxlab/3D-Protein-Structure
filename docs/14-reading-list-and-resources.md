# 14 — Research Reading List, White Papers, and Resources

[Back to README](../README.md) · [Full pipeline](09-end-to-end-ai-drug-discovery.md)

This is a curated entry point to primary papers, benchmark resources, datasets, and practical tooling. “White paper” is used broadly here for technical reports and institutional resources; peer-reviewed primary research should be preferred for scientific claims. Links and access terms can change, so check the original source before citing or redistributing.

## 1. Essential papers

### Protein structure and biomolecular interactions

1. **AlphaFold2** — Jumper et al. (2021), “Highly accurate protein structure prediction with AlphaFold,” *Nature*. https://doi.org/10.1038/s41586-021-03819-2
2. **AlphaFold DB** — Varadi et al. (2024), “AlphaFold Protein Structure Database in 2024,” *Nucleic Acids Research*. https://doi.org/10.1093/nar/gkad1011
3. **AlphaFold 3** — Abramson et al. (2024), “Accurate structure prediction of biomolecular interactions with AlphaFold 3,” *Nature*. https://doi.org/10.1038/s41586-024-07487-w
4. **ESMFold / protein language models** — Lin et al. (2023), “Evolutionary-scale prediction of atomic-level protein structure with a language model,” *Science*. https://doi.org/10.1126/science.ade2574
5. **CASP assessment** — Critical Assessment of protein Structure Prediction: https://predictioncenter.org/

### Molecular ML and drug discovery

6. **MoleculeNet** — Wu et al. (2018), “MoleculeNet: a benchmark for molecular machine learning,” *Chemical Science*. https://doi.org/10.1039/C7SC02664A
7. **GuacaMol** — Brown et al. (2019), “GuacaMol: benchmarking models for de novo molecular design,” *JCIM*. https://doi.org/10.1021/acs.jcim.8b00839
8. **MOSES** — Polykovskiy et al. (2020), “Molecular Sets (MOSES): a benchmarking platform for molecular generation models,” *Frontiers in Pharmacology*. https://doi.org/10.3389/fphar.2020.565644
9. **AI-discovered clinical candidates** — Jayatunga et al. (2024), “How successful are AI-discovered drugs in clinical trials? A first analysis and emerging lessons,” *Drug Discovery Today*. https://doi.org/10.1016/j.drudis.2024.104009
10. **PoseBusters** — Buttenschoen et al. (2024), physical plausibility benchmarking of generated/docked poses. https://doi.org/10.1038/s42256-024-00872-8
11. **ChEMBL** — Gaulton et al. (2017), “The ChEMBL database in 2017,” *Nucleic Acids Research*. https://doi.org/10.1093/nar/gkw1074
12. **Open targets** — Ochoa et al. and Open Targets Platform publications; start at https://platform.opentargets.org/ and follow the release-specific citation guidance.

## 2. Data portals

- [RCSB Protein Data Bank](https://www.rcsb.org/) — experimental structures.
- [AlphaFold Protein Structure Database](https://alphafold.ebi.ac.uk/) — predicted structures.
- [UniProt](https://www.uniprot.org/) — protein sequence and annotation.
- [ChEMBL](https://www.ebi.ac.uk/chembl/) — bioactivity.
- [PubChem](https://pubchem.ncbi.nlm.nih.gov/) — compounds and bioassays; review provenance and license.
- [BindingDB](https://www.bindingdb.org/) — binding affinity data.
- [PDBbind](http://www.pdbbind.org.cn/) — complexes and affinity data; check access terms.
- [Open Targets](https://platform.opentargets.org/) — target–disease evidence.
- [Therapeutics Data Commons](https://tdcommons.ai/) — ML tasks, datasets, splits and evaluation utilities.
- [Tox21](https://tripod.nih.gov/tox21/) and [EPA CompTox / ToxCast](https://www.epa.gov/comptox-tools/exploring-toxcast-data) — toxicity-related assay resources.

## 3. Code and software

- [RDKit](https://www.rdkit.org/) — cheminformatics.
- [DeepChem](https://deepchem.io/) — molecular ML and scientific ML tools.
- [PyTorch Geometric](https://pytorch-geometric.readthedocs.io/) — graph neural networks.
- [OpenMM](https://openmm.org/) — molecular simulation.
- [AutoDock Vina](https://vina.scripps.edu/) — molecular docking.
- [OpenFold](https://github.com/aqlaboratory/openfold), [ESM](https://github.com/facebookresearch/esm), [Chai-1](https://github.com/chaidiscovery/chai-lab), [Boltz](https://github.com/jwohlwend/boltz), [Protenix](https://github.com/bytedance/Protenix) — model implementations; check current licenses, model weights and usage restrictions.
- [Open Babel](https://openbabel.org/) — chemical format conversion and utilities.

## 4. Institutional and regulatory resources

- [FDA: Artificial Intelligence and Machine Learning](https://www.fda.gov/science-research/science-and-research-special-topics/artificial-intelligence-and-machine-learning-aiml-drug-development) — FDA information on AI/ML in drug development.
- [FDA: Drug Development and Approval Process](https://www.fda.gov/patients/learn-about-expanded-access-and-other-treatment-options/step-3-clinical-research) — clinical research context.
- [ClinicalTrials.gov](https://clinicaltrials.gov/) — registered studies; check record history and sponsors.
- [WHO ICTRP](https://trialsearch.who.int/) — international clinical trial search portal.
- [ICH guidelines](https://www.ich.org/page/ich-guidelines) — harmonized technical guidelines relevant to drug development.
- [NCATS](https://ncats.nih.gov/) — translational science resources.
- [NIH National Center for Advancing Translational Sciences: Assay Guidance Manual](https://www.ncbi.nlm.nih.gov/books/NBK53196/) — assay design and validation guidance.

## 5. Seminal conceptual papers and critical perspectives

- Anfinsen (1973), “Principles that govern the folding of protein chains,” *Science*. https://doi.org/10.1126/science.181.4096.223
- Walters & Murcko (2020), “Assessing the impact of generative AI on medicinal chemistry,” *Nature Biotechnology*. https://doi.org/10.1038/s41587-020-0418-2
- Read benchmark papers and critiques alongside each other. Retrospective performance can be inflated by data leakage, biased datasets, and weak baselines; prospective experimental validation is the stronger test of utility.

## 6. How to keep this list current

For every added resource, record the title, authors/organization, year, DOI or canonical URL, access date, license, and why it is relevant. Prefer the paper's version of record or an official data portal. Clearly label preprints, company claims, benchmark results, and regulatory facts separately. Do not cite search snippets or a company marketing page as the sole support for a strong scientific claim.
