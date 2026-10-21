# 11 — Models and Methods: From Protein Language Models to Generative Chemistry

[Back to README](../README.md) · [Datasets](10-datasets-and-data-engineering.md) · [Hands-on project](12-getting-started-project.md)

No model is “best” independently of the task, data, evaluation split, deployment constraints, and experimental context. Prefer a strong baseline and prospective validation over a long model leaderboard.

## 1. Protein structure and interaction models

| Model / resource | Main task | Practical notes |
|---|---|---|
| [AlphaFold2](https://github.com/google-deepmind/alphafold) | Protein structure prediction | Strong baseline for many monomers; pipeline requires sequence databases and substantial compute |
| [AlphaFold DB](https://alphafold.ebi.ac.uk/) | Retrieve precomputed predictions | Often the lowest-cost first step; inspect confidence and biological context |
| [AlphaFold 3](https://github.com/google-deepmind/alphafold3) | Biomolecular complex structure prediction | Code/weights access and license terms apply; read the official terms before use |
| [OpenFold](https://github.com/aqlaboratory/openfold) | Open implementation and research infrastructure for AF2-like work | Useful for reproducibility and method development; setup is nontrivial |
| [ESM](https://github.com/facebookresearch/esm) / [ESMFold](https://github.com/facebookresearch/esm) | Protein language modeling and structure prediction | Single-sequence workflows can scale well; speed and accuracy depend on task |
| [RoseTTAFold](https://github.com/RosettaCommons/RoseTTAFold) | Protein structure prediction | Three-track reasoning across sequence, pair representation and coordinates |
| [Chai-1](https://github.com/chaidiscovery/chai-lab) | Biomolecular complex prediction | Check current release, license, supported modalities and benchmark protocol |
| [Boltz](https://github.com/jwohlwend/boltz) | Biomolecular structure prediction | Open model family; pin version and follow repository-specific input/weight requirements |
| [Protenix](https://github.com/bytedance/Protenix) | Open AlphaFold-3-style biomolecular modeling | Verify supported atom types, training-data policy and exact release before comparison |

Primary paper: Abramson et al. (2024), AlphaFold 3, https://doi.org/10.1038/s41586-024-07487-w. The 2024 paper and subsequent code release should be read alongside current official usage terms; “code available” does not automatically mean unrestricted open-source weights or commercial rights.

## 2. Molecular representations

| Representation | Examples | Strengths | Limitations |
|---|---|---|---|
| SMILES strings | Canonical or randomized SMILES | Simple sequence-model input; easy serialization | Multiple strings can encode the same molecule; syntax and stereochemistry handling matter |
| Molecular fingerprints | Morgan/ECFP, MACCS | Strong inexpensive baselines; similarity search | Fixed representation may miss some geometry and context |
| Molecular graphs | Atom and bond graphs; GNNs | Natural representation of connectivity | 3D geometry and stereochemistry need explicit treatment |
| 3D conformers | Coordinates, distances, angles | Useful for geometry-aware models | Conformer generation and protonation can introduce uncertainty |
| Protein–ligand complexes | Joint atom/residue graphs or coordinate frames | Represents interactions directly | Sensitive to structure quality and data leakage |
| Protein language embeddings | ESM-family embeddings | Transfer learning from large sequence corpora | Embedding similarity is not equivalent to function or binding |

## 3. Model families by task

- **Target and omics prioritization:** regularized regression, gradient boosting, graph learning, knowledge graphs, multimodal models.
- **Bioactivity prediction:** random forest / XGBoost on fingerprints, GNNs, molecular transformers, protein–ligand models.
- **Docking and pose prediction:** physics-based docking, learned scoring, equivariant geometric networks, co-folding.
- **Molecular generation:** autoregressive transformers, VAEs, diffusion models, graph generators, fragment-based methods, reinforcement learning.
- **ADMET:** endpoint-specific classification/regression, multitask learning, pretrained molecular encoders, uncertainty-aware ensembles.
- **Protein design:** sequence models, inverse folding, diffusion-based backbone design, sequence–structure co-design.

Useful foundational resources include [RDKit](https://www.rdkit.org/), [PyTorch Geometric](https://pytorch-geometric.readthedocs.io/), [DeepChem](https://deepchem.io/), [OpenMM](https://openmm.org/), [AutoDock Vina](https://vina.scripps.edu/), and [Therapeutics Data Commons](https://tdcommons.ai/).

## 4. Evaluation metrics and common traps

| Task | Useful metrics | Common trap |
|---|---|---|
| Binary activity | PR-AUC, ROC-AUC, precision/recall, MCC, calibration | Reporting accuracy on imbalanced data |
| Regression | MAE, RMSE, R², calibration intervals | Comparing results across incompatible units or assay types |
| Ranking | Enrichment factor, BEDROC, hit rate at fixed budget | Random split leakage and retrospective-only claims |
| Docking / pose | RMSD with symmetry handling, interaction checks, PoseBusters | A low RMSD alone can conceal chemically impossible geometry |
| Structure prediction | lDDT, TM-score, interface metrics, confidence calibration | Comparing scores from different protocols or leaked homologs |
| Generation | Validity, uniqueness, diversity, novelty, property distribution, synthesis feasibility | Optimizing benchmark scores without useful molecules |
| ADMET | Endpoint-specific external performance, sensitivity/specificity, calibration | Treating one endpoint as a universal “toxicity score” |

Use time-split and scaffold-split evaluation where appropriate. For protein structures, ensure the test set does not contain close homologs or near-identical complexes from training when the research claim is generalization to unseen biology. For molecules, separate compounds by scaffold or time and document duplicate handling.

## 5. Multi-objective design and uncertainty

A practical ranking system should combine predicted properties with constraints, uncertainty, and experimental cost. Consider Pareto optimization rather than hiding trade-offs in one arbitrary scalar reward. Use applicability-domain checks: a model can be confidently wrong for chemistry unlike its training data. Calibration and uncertainty estimates should be validated on held-out data, not assumed from model architecture.

## Selected reading

- Jumper et al. (2021), AlphaFold2, *Nature*. https://doi.org/10.1038/s41586-021-03819-2
- Lin et al. (2023), ESMFold / language-model structure prediction, *Science*. https://doi.org/10.1126/science.ade2574
- Abramson et al. (2024), AlphaFold 3, *Nature*. https://doi.org/10.1038/s41586-024-07487-w
- Wu et al. (2018), MoleculeNet, *Chemical Science*. https://doi.org/10.1039/C7SC02664A
- Buttenschoen et al. (2024), PoseBusters, *Nature Machine Intelligence*. https://doi.org/10.1038/s42256-024-00872-8
