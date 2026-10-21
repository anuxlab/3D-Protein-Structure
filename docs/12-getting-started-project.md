# 12 — Getting Started: A Reproducible AI Drug-Discovery Research Project

[Back to README](../README.md) · [Datasets](10-datasets-and-data-engineering.md) · [Models](11-models-and-methods.md)

This project is designed for a laptop or modest workstation and focuses on **bioactivity prediction from public data**. It does not attempt to identify a medicine or make claims about patient outcomes. Begin with one target and one well-defined assay endpoint.

## 1. A focused first research question

Example: “Can a fingerprint-based baseline predict whether a compound is active against a selected target better than a simple prevalence or similarity baseline under a scaffold split?”

Select a target with enough data, a coherent assay endpoint, and sufficient chemical diversity. ChEMBL is a reasonable source. Use the [ChEMBL web interface](https://www.ebi.ac.uk/chembl/) or API and record the target ID, activity type, units, confidence filters, and data release.

## 2. Environment

Python 3.10–3.12 is a conservative starting range; confirm compatibility for pinned library versions.

```bash
python -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows PowerShell: .venv\\Scripts\\Activate.ps1
python -m pip install --upgrade pip
pip install pandas numpy scikit-learn matplotlib rdkit-pypi chembl_webresource_client
```

Depending on platform, installing RDKit through conda-forge may be more reliable than `rdkit-pypi`; use the [official RDKit installation guidance](https://www.rdkit.org/docs/Install.html). Pin tested versions in a lock file before publishing results.

## 3. Minimal reproducible workflow

1. **Define endpoint:** for example, a single assay type and target, with explicit activity threshold and units. Do not mix Ki, Kd, IC50, EC50, and percent inhibition without a defensible harmonization strategy.
2. **Retrieve data:** save the raw response and source metadata; note date and API query.
3. **Clean:** parse SMILES, remove invalid structures, handle salts/tautomers using documented rules, deduplicate compounds and resolve conflicting labels.
4. **Split:** create a scaffold split, not only a random split. Use RDKit's Bemis–Murcko scaffold support or a validated split utility.
5. **Baseline:** compare prevalence-only, fingerprint similarity, and a simple model such as random forest or logistic regression.
6. **Evaluate:** report PR-AUC, ROC-AUC, precision/recall at a fixed threshold, calibration, confidence intervals where feasible, and class balance.
7. **Audit:** inspect errors, chemical series, assay provenance, and applicability domain.
8. **Report:** save the dataset version, split IDs, code commit, seeds, environment, metrics, and limitations.

## 4. Starter code: fingerprint baseline

This example expects a CSV that you have already curated with columns `smiles` and `label` (0/1). It deliberately does not silently fetch, label, or harmonize biological data. Create scaffold-based train/test splits before fitting the model; the simple random split below is included only to demonstrate API mechanics and **must not be used as evidence of prospective generalization**.

```python
import pandas as pd
import numpy as np
from rdkit import Chem, DataStructs
from rdkit.Chem import rdFingerprintGenerator
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import average_precision_score, roc_auc_score
from sklearn.model_selection import train_test_split

# Input must be curated; document how labels and duplicates were handled.
df = pd.read_csv("curated_bioactivity.csv").dropna(subset=["smiles", "label"])
df["label"] = df["label"].astype(int)

mols, labels = [], []
for smi, label in zip(df["smiles"], df["label"]):
    mol = Chem.MolFromSmiles(str(smi))
    if mol is not None and label in (0, 1):
        mols.append(mol)
        labels.append(label)

fpgen = rdFingerprintGenerator.GetMorganGenerator(radius=2, fpSize=2048)
X = np.zeros((len(mols), 2048), dtype=np.uint8)
for i, mol in enumerate(mols):
    arr = np.zeros((2048,), dtype=np.uint8)
    DataStructs.ConvertToNumpyArray(fpgen.GetFingerprint(mol), arr)
    X[i] = arr

y = np.asarray(labels)
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)
model = RandomForestClassifier(
    n_estimators=500, class_weight="balanced", random_state=42, n_jobs=-1
)
model.fit(X_train, y_train)
prob = model.predict_proba(X_test)[:, 1]
print("PR-AUC:", average_precision_score(y_test, prob))
print("ROC-AUC:", roc_auc_score(y_test, prob))
```

For a publishable result, replace the random split with a scaffold or temporal split, compare against strong baselines, inspect duplicate leakage, tune only on training/validation data, and reserve the test set for final evaluation. A single metric is insufficient.

## 5. Recommended repository structure

```text
project/
├── README.md
├── environment.yml            # or requirements + lock file
├── data/
│   ├── raw/                   # excluded from git if large/restricted
│   ├── processed/
│   └── dataset_card.md
├── notebooks/                 # exploratory only
├── src/
│   ├── fetch_data.py
│   ├── clean_data.py
│   ├── split_data.py
│   ├── featurize.py
│   ├── train.py
│   └── evaluate.py
├── configs/
├── tests/
├── reports/
│   ├── figures/
│   └── metrics.json
└── docs/
```

Do not commit patient-level data, restricted datasets, credentials, or large model weights. Use checksums and scripts to reconstruct derived datasets when licenses permit.

## 6. Next experiments

- Compare Morgan fingerprints + logistic regression, random forest, and gradient boosting.
- Compare random versus scaffold versus temporal splits to quantify leakage sensitivity.
- Evaluate calibration and uncertainty; flag compounds outside the training domain.
- Add an external dataset or prospective assay set if available.
- For structure-based research, choose one target with a relevant experimental PDB structure and compare docking poses against known ligands before screening new compounds.
- Pre-register the main endpoint and split strategy to reduce benchmark shopping.

## 7. Research reporting checklist

- [ ] Exact research question and intended use
- [ ] Data source, version, access date, license and query
- [ ] Endpoint definition, units and label thresholds
- [ ] Cleaning and deduplication rules
- [ ] Split strategy and leakage checks
- [ ] Baselines, metrics, seeds and uncertainty
- [ ] Software versions and compute environment
- [ ] Error analysis and applicability domain
- [ ] Negative results and known limitations
- [ ] Code, configs and permitted data access instructions
