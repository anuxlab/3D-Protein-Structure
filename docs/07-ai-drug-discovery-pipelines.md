# 07 — AI Drug Discovery Pipelines

[Back to README](../README.md) | [Previous: Applications](06-applications.md) | [Next: Disease Case Studies](08-disease-case-studies.md)

Protein structure prediction is one component of a larger workflow. This document describes how AI is applied across the drug discovery pipeline—from target identification through preclinical development—and how the companies discussed earlier fit into that pipeline.

---

## 1. The pipeline at a glance

A conventional small-molecule discovery pipeline proceeds through several sequential stages:

1. **Target identification and validation**
2. **Hit identification** (finding starting chemical matter)
3. **Lead identification** (confirming a tractable chemical series)
4. **Lead optimization** (improving potency, selectivity, and drug-like properties)
5. **Preclinical development** (ADMET, toxicology, formulation, IND-enabling studies)
6. **Clinical trials** and regulatory approval

AI does not replace any of these stages; it changes the speed, cost, and search breadth at each one[reference:0]. The most mature applications are in **hit identification, lead optimization, and preclinical property prediction**, while **target identification and clinical trial design** are earlier in maturity but advancing quickly[reference:1].

---

## 2. Stage-by-stage AI applications

### 2.1 Target identification and validation

**What AI contributes**

- Integration of **multi-omics data** (genomics, transcriptomics, proteomics) with graph neural networks and large language models to uncover disease pathways and druggable proteins[reference:2].
- **Knowledge graphs** linking genes, pathways, compounds, and clinical evidence to prioritize targets.
- **Structure prediction** to assess whether a candidate target has a ligandable pocket, using tools such as AlphaFold and related models[reference:3].
- **Network-based and protein–ligand prediction** approaches to infer target–disease relationships[reference:4].

**Caveat:** Target validation remains the dominant bottleneck. AI can generate hypotheses faster than wet-lab validation can confirm them, and **data bias and distributional shifts** can make computational target rankings unreliable[reference:5].

### 2.2 Hit identification

**What AI contributes**

- **Virtual screening** of ultra-large chemical libraries, including make-on-demand catalogs.
- **Generative chemistry:** GANs, variational autoencoders, diffusion models, and language models that *design* molecules with desired properties rather than screening existing compounds[reference:6].
- **DNA-encoded library (DEL) + machine learning:** Graph neural networks trained on DEL selection data can nominate hits that generalize beyond the physical library, at hit rates above conventional high-throughput screening[reference:7].
- **Structure-based hit finding:** Co-folding models (AlphaFold3, Chai-1, Protenix, Boltz) can propose ligand poses and binding modes for targets without experimental structures.

**Practical note:** Generative models can produce molecules that are synthetically inaccessible or chemically implausible. **Synthetic accessibility** and **novelty** are therefore commonly included as explicit optimization objectives or filters[reference:8].

### 2.3 Lead identification and lead optimization

**What AI contributes**

- **Multi-parameter optimization** balancing potency, selectivity, solubility, metabolic stability, and safety[reference:9].
- **Property prediction** for solubility, permeability, and pharmacokinetic parameters, with reported R² values above 0.9 for several key endpoints[reference:10].
- **Ensemble ML models** that combine multiple algorithms to improve prediction robustness; ensemble approaches have reported high accuracy in pharmacokinetic prediction (R² > 0.90)[reference:11].
- **Generative scaffold hopping and analog design**, conditioned on potency, selectivity, and synthetic accessibility objectives[reference:12].
- **Protein dynamics and cryptic pockets:** Platforms such as Relay Therapeutics' **Dynamo** use long-timescale molecular dynamics, cryo-EM, and ambient-temperature crystallography to find pockets that appear only in certain conformations—targets that static structures would miss[reference:13][reference:14].

### 2.4 Preclinical development: ADMET and toxicology

**What AI contributes**

- **ADMET prediction** (absorption, distribution, metabolism, excretion, toxicity) as a virtual filter before synthesis[reference:15].
- **Mechanistic toxicity modeling**, including acute oral toxicity classification with reported accuracies above 95% for some endpoints[reference:16].
- **In silico go/no-go decisions**, reducing costly experimental cycles in preclinical development[reference:17].

**Caveat:** Toxicity prediction performance varies substantially across endpoints and chemical domains. The optimal model for one toxicity endpoint is often not optimal for another, making **comparative, endpoint-specific validation** necessary[reference:18].

### 2.5 Clinical stages and trial design

AI is beginning to influence clinical development through **biomarker-informed patient selection**, **adaptive trial design**, and **predictive enrichment**—using models to identify patients most likely to respond[reference:19]. Xaira Therapeutics explicitly frames its platform as covering “the process of identifying targets; making the drugs themselves; and also identifying the patients most likely to respond” through its X-Cell and X-Patient models[reference:20].

However, **no AI-discovered drug has yet completed Phase III and reached approval**. The first readouts that will meaningfully test end-to-end AI pipelines are expected in the late 2020s.

---

## 3. Representative pipelines and company strategies

The organizations described in [Companies and Ecosystem](03-companies-ecosystem.md) occupy different positions along the pipeline.

| Organization | Pipeline posture | Notable 2026 status |
|---|---|---|
| **Isomorphic Labs** | Proprietary pipeline in oncology and immunology, plus pharma partnerships | Several programs in **IND-enabling studies**; first IND filing and first-in-human testing targeted by **end of 2026**. The company has not publicly named individual assets. Its **IsoDDE** engine is reported to more than double AlphaFold3 accuracy on the hardest protein–ligand systems, and to achieve 2.3× better high-fidelity antibody–antigen prediction, though these are company-reported benchmarks[reference:21]. |
| **Insilico Medicine** | Clinical-stage pipeline built on generative AI | **Rentosertib (ISM001-055)** , a TNIK inhibitor for idiopathic pulmonary fibrosis, has **dosed its first patient in Phase III** (GENESIS-IPF-3, 52-week treatment). The target was **AI-discovered** and had not previously been linked to fibrosis. Insilico nominated **nine development candidates in nine months** in 2026 and reported **eight clinical milestones** across proprietary and partnered programs[reference:22][reference:23]. |
| **Xaira Therapeutics** | Antibody-first, “platform then pipeline” | Launched with **$1 billion** in 2024. Its **X-Design** platform designed antibody **XA-1** from scratch in **seven weeks**; **XA-4** targets a previously intractable GPCR. Additional candidates **XA-2** and **XA-3** are in preclinical development. Xaira's models also include **X-Cell** (a 4.9-billion-parameter virtual cell model) and **X-Patient**[reference:24]. |
| **Chai Discovery** | Platform and partnerships rather than a wholly owned clinical pipeline | **Chai-3** is licensed to **Pfizer** with a custom model trained on Pfizer's proprietary data. **GSK** entered a collaboration after wet-lab evaluation showed binders to all tested targets, with designs generated **zero-shot**. Chai also has 2026 collaborations with **Bristol Myers Squibb, Eli Lilly, and Novartis**[reference:25][reference:26]. |
| **Recursion** | Clinical-stage pipeline generated by a “full-stack” AI operating system | **Five clinical-stage programs**, including **REC-4881** in FAP (with FDA discussions on a registrational trial), **REC-4539** (LSD1 inhibitor, first patient dosed in Phase I, developed with ~400 compounds synthesized), and **REC-7735** (PI3Kα H1047R inhibitor, Phase I ZINNIA trial planned). The company has reported **clinical validation** of its platform in FAP[reference:27]. |
| **Relay Therapeutics** | Dynamics-first, structure-based | **Lirafugratinib (RLY-4008)** , a computationally designed FGFR2 inhibitor, reached **FDA review with Priority Review** and a target action date of **27 September 2026**—one of the closest AI-originated programs to a market decision. **Zovegalisib** is in **Phase 3** in PI3Kα-mutant breast cancer[reference:28]. |
| **Schrödinger** | Software-plus-therapeutics; strategically rebalancing toward its design engine | Advanced **SGR-3515** and **SGR-1505** in Phase I and launched an AI co-scientist, **Bunsen**. In 2025–2026 the company **deprioritized independent clinical development** for some programs, refocusing on its computational platform and collaborations[reference:29]. |

---

## 4. What the pipeline reveals about AI's role

### 4.1 AI is strongest where feedback is fast

The stages with the clearest, most reproducible AI impact are those with **dense, well-curated training data and fast experimental readouts**: property prediction, virtual screening, generative analog design, and ADMET filtering[reference:30]. Target identification and clinical translation involve **sparse, noisy, and context-dependent data**, and remain harder to accelerate reliably[reference:31].

### 4.2 Structure prediction is an input, not an endpoint

Protein structure prediction—the subject of the earlier documents in this set—feeds directly into **structure-based hit finding, ligand pose prediction, and cryptic-pocket discovery**. But a predicted structure does not by itself produce a drug; it must be coupled to generative chemistry, property prediction, synthesis, and experimental validation. Isomorphic's IsoDDE, Chai's design models, and Relay's Dynamo all illustrate this coupling[reference:32][reference:33][reference:34].

### 4.3 The clinical readout is the real test

The field's central open question is whether AI-driven pipelines produce **higher clinical success rates**, not merely faster preclinical timelines. Insilico's Phase III rentosertib trial, Relay's lirafugratinib regulatory decision, and Isomorphic's first-in-human studies will be among the first substantive tests of whether AI-originated molecules behave differently in patients[reference:35][reference:36][reference:37].

### 4.4 Partnership models are maturing

Large pharma is not simply buying software; it is **embedding AI platforms into internal workflows**. Pfizer's custom Chai-3 instance trained on proprietary data, and GSK's decision to expand collaboration after internal wet-lab validation, reflect a shift toward **empirical, data-integrated adoption** rather than platform licensing alone[reference:38][reference:39].

---

## 5. Summary

| Pipeline stage | Maturity of AI impact | Primary AI methods | Key caveat |
|---|---|---|---|
| Target identification | Emerging | Multi-omics integration, knowledge graphs, structure prediction | Validation bottleneck; data bias |
| Hit identification | Mature | Virtual screening, generative chemistry, DEL + ML | Synthetic accessibility; false positives |
| Lead optimization | Mature | Multi-parameter optimization, property prediction, dynamics | Assay-specific generalization |
| Preclinical (ADMET/tox) | Maturing | ADMET models, toxicity classifiers | Endpoint-dependent performance |
| Clinical design | Early | Biomarker enrichment, adaptive design | No completed Phase III AI-originated drug yet |

AI is reshaping **how molecules are found and optimized**, but the pipeline's ultimate constraint remains **biological validation and clinical translation**. The most credible AI drug discovery programs are those that pair computational speed with rigorous wet-lab iteration and transparent reporting of clinical outcomes.

---

[Back to README](../README.md) | [Next: Disease Case Studies](08-disease-case-studies.md)
