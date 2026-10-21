# 10 — Datasets for AI Drug Discovery

[Back to README](../README.md) · [Models and methods](11-models-and-methods.md) · [Getting started](12-getting-started-project.md)

Dataset choice often matters more than architecture choice. This catalog is a starting point, not an endorsement of unrestricted reuse: check the current license, terms of use, provenance, release date, and any restrictions on redistribution or commercial use before downloading or training.

## 1. Protein sequence, structure, and complexes

| Resource | Contents / use | Access |
|---|---|---|
| [Protein Data Bank (PDB)](https://www.rcsb.org/) | Experimentally determined macromolecular structures; inspect ligand, construct, resolution and experimental method | Search/download; APIs |
| [AlphaFold DB](https://alphafold.ebi.ac.uk/) | Predicted structures and confidence information for protein sequences | Per-protein downloads and selected bulk downloads |
| [UniProt](https://www.uniprot.org/) | Protein sequence, function annotations, cross-references and evidence | Search, REST API, bulk downloads |
| [EMDB](https://www.ebi.ac.uk/emdb/) | Cryo-EM density maps and metadata | Search/download |
| [SAbDab](https://opig.stats.ox.ac.uk/webapps/sabdab-sabpred/) | Curated antibody structures and annotations | Web access / downloads subject to terms |
| [PDBbind](http://www.pdbbind.org.cn/) | Protein–ligand structures paired with binding-affinity data | Access and redistribution conditions vary by release |
| [BioLiP](https://zhanggroup.org/BioLiP/) | Biologically relevant ligand-binding annotations | Download / search |
| [Binding MOAD](https://bindingmoad.org/) | Curated protein–ligand binding data | Dataset website |

**Caution:** experimental structures are not error-free; crystal contacts, construct mutations, missing residues, alternate conformations, ligand occupancy, and assay conditions matter. A predicted structure should not be relabeled as experimental ground truth.

## 2. Chemistry, bioactivity, and medicinal chemistry

| Resource | Contents / use | Important caveat |
|---|---|---|
| [ChEMBL](https://www.ebi.ac.uk/chembl/) | Curated bioactivity, targets, assays, compounds and publications | Assay heterogeneity; inspect `standard_type`, `standard_value`, `standard_units`, confidence and assay metadata |
| [PubChem](https://pubchem.ncbi.nlm.nih.gov/) | Chemical structures, identifiers, depositor-provided properties and bioassays | Provenance and license may differ by contributing source; [download guidance](https://pubchem.ncbi.nlm.nih.gov/docs/downloads) |
| [BindingDB](https://www.bindingdb.org/) | Measured protein–ligand binding affinities | Different assay formats and affinity units require harmonization |
| [ZINC](https://zinc.docking.org/) | Purchasable compounds for virtual screening | Availability, prices, and licenses change; verify before ordering |
| [DrugBank](https://go.drugbank.com/) | Drug and target knowledge | Terms/licensing can restrict academic or commercial reuse |
| [Open Targets](https://platform.opentargets.org/) | Target–disease evidence integration | Evidence score is prioritization support, not proof of causality |
| [Therapeutics Data Commons (TDC)](https://tdcommons.ai/) | Standardized ML tasks, datasets, splits and evaluators | Verify dataset version and benchmark assumptions |

## 3. ADMET and safety data

Start with TDC's ADME and toxicity tasks, ChEMBL/PubChem bioassays, and published endpoint-specific collections. Some resources such as [Tox21](https://tripod.nih.gov/tox21/) and [ToxCast](https://www.epa.gov/comptox-tools/exploring-toxcast-data) provide assay-level toxicity data. Endpoint labels are not interchangeable: an assay response, a clinical adverse event, and an overall safety outcome answer different questions.

## 4. Generative chemistry benchmarks

- [GuacaMol](https://github.com/BenevolentAI/guacamol): distribution-learning and goal-directed molecular-generation benchmarks; see Brown et al., https://doi.org/10.1021/acs.jcim.8b00839.
- [MOSES](https://github.com/molecularsets/moses): molecular-generation quality/diversity benchmark and baselines; see Polykovskiy et al., https://doi.org/10.3389/fphar.2020.565644.
- [MoleculeNet](https://moleculenet.org/): benchmark datasets for molecular machine learning; see Wu et al., https://doi.org/10.1039/C7SC02664A.
- [PoseBusters](https://github.com/maabuu/posebusters): checks physical plausibility of predicted ligand poses; see Buttenschoen et al., https://doi.org/10.1038/s42256-024-00872-8.
- [CASP](https://predictioncenter.org/): community-wide assessment of protein structure prediction, with task-specific targets and protocols.

## 5. Data engineering checklist

1. **Preserve source records.** Keep the original identifier, source URL, release, retrieval date, license, and source-level ID.
2. **Standardize chemical structures carefully.** Parse with RDKit; retain raw SMILES and a standardized representation; record salt stripping, charge normalization, tautomer handling, stereochemistry, and canonicalization settings.
3. **Harmonize activity endpoints.** Convert units only when justified. Do not merge IC50, Ki, Kd, EC50, and percent inhibition as if they were the same label.
4. **Handle censored measurements explicitly.** `>`, `<`, and approximate values are not exact observations. Preserve qualifiers or use methods designed for censoring.
5. **Deduplicate before splitting.** Deduplicate by standardized structures and assay/target context; avoid identical compounds or near-identical records leaking across splits.
6. **Split for the intended deployment.** Random splits often overestimate generalization. Consider scaffold, temporal, target-held-out, or external splits. Report all split logic.
7. **Avoid target leakage.** Do not let assay identifiers, publication metadata, duplicate analogs, or post-cutoff data leak into features or training labels.
8. **Keep a dataset card.** Document inclusion/exclusion criteria, counts at each cleaning step, class balance, missingness, and known biases.

## 6. Suggested starter dataset combinations

| Research question | Starter data combination | Evaluation strategy |
|---|---|---|
| Predict ligand potency | ChEMBL or BindingDB, one target family | Scaffold split; external literature set if feasible |
| Predict ADMET endpoint | TDC task / curated assay set | Endpoint-specific split; calibration and applicability domain |
| Ligand pose / docking | PDBbind + PDB structures | Time split or structure-cluster split; physical checks |
| Protein–ligand co-folding | PDB complexes and a selected held-out set | Remove close homologs/ligands; assess pose and chemistry plausibility |
| Molecular generation | GuacaMol or MOSES | Validity, uniqueness, diversity, novelty, synthesizability and experimental follow-up |
| Target prioritization | Open Targets + UniProt + disease-specific omics | Temporal or target-held-out validation; biological review |

## Selected references

- Gaulton et al. (2017), ChEMBL, *Nucleic Acids Research*. https://doi.org/10.1093/nar/gkw1074
- Wu et al. (2018), MoleculeNet, *Chemical Science*. https://doi.org/10.1039/C7SC02664A
- Polykovskiy et al. (2020), MOSES, *Frontiers in Pharmacology*. https://doi.org/10.3389/fphar.2020.565644
- Brown et al. (2019), GuacaMol, *Journal of Chemical Information and Modeling*. https://doi.org/10.1021/acs.jcim.8b00839
