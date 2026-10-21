# 08 — Disease Case Studies and Drug Discovery Applications

[Back to README](../README.md) | [Previous: AI Drug Discovery Pipelines](07-ai-drug-discovery-pipelines.md)

This document catalogs disease areas where AI protein structure prediction has been applied to drug discovery, including COVID-19, cancer, neurodegenerative disease, rare genetic disorders, and infectious diseases. For each area, it describes the structural work, the drug discovery approaches it enabled, and the current status of resulting programs.

---

## 1. COVID-19 / SARS-CoV-2

COVID-19 was the first major test of AI structure prediction in an active pandemic, and it produced both structural biology advances and candidate therapeutics.

### 1.1 Structural studies of SARS-CoV-2 proteins

**Main protease (Mpro / 3CLpro)**

The SARS-CoV-2 main protease is essential for viral replication and was one of the most intensively studied targets. AlphaFold2 models of Mpro were **validated against experimental residual dipolar couplings (RDCs) measured in solution**, showing concordance between predicted and experimental structures[reference:0]. This validation was important because it established that AlphaFold2 predictions could be trusted for a functionally critical viral enzyme.

AlphaFold2 was subsequently used to model **Mpro–peptidyl substrate complexes**, enabling structure-based drug repositioning studies that revisited Mpro as a case study for pandemic preparedness[reference:1][reference:2]. AlphaFold3 has since been used to characterize **alternate encounter assemblies of Mpro**, extending the analysis from static structures to conformational ensembles[reference:3][reference:4].

**Spike protein and host receptor interactions**

AlphaFold2 was used to predict structures of the SARS-CoV-2 **spike protein** and its interactions with the **ACE2 host receptor**. Studies modeled the **post-fusion form** of the spike and used these predictions to design **peptide-based fusion inhibitors** targeting the heptad repeat (HR) regions[reference:5]. AlphaFold2-predicted **6HB (six-helix bundle)** structures from HR1 and HR2 sequences supported the rapid development of **viral class I fusion inhibitors**[reference:6].

AlphaFold2 was also applied to model the **B.1.617.1 variant** and its E484Q and L452R mutations, examining effects on structure and ACE2 binding using docking and molecular dynamics[reference:7]. More recent work has modeled **Omicron subvariant spike proteins** (including BA.2.86) in complex with ACE2 and antibodies, generating conformational ensembles and binding energetics[reference:8][reference:9].

**Other viral proteins**

AlphaFold2 was combined with cryo-EM to build an atomic model of the full-length virus, revealing a conserved **zinc ion-binding site in Nsp2** and providing a foundation for functional studies of this conserved coronavirus protein[reference:10]. AlphaFold has also been used in **proteome-wide interaction predictions** between SARS-CoV-2 proteins and the human proteome[reference:11].

### 1.2 Drug discovery approaches enabled by structural models

**Structure-based drug repurposing**

An **AlphaFold2-driven drug repositioning strategy** was developed for "Disease X" and validated using SARS-CoV-2 Mpro as a case study. The approach combined AlphaFold2-predicted structures with **virtual screening against FDA-approved drugs**, using an integrated molecular docking method (MDCC), and successfully identified lead drugs for Mpro[reference:12][reference:13]. This demonstrated a generalizable pandemic-response pipeline: predict the structure, screen approved drugs, prioritize candidates.

**De novo peptide and miniprotein inhibitors**

Structure-guided design produced **ACE2-based peptide inhibitors** of SARS-CoV-2[reference:14], **picomolar SARS-CoV-2 miniprotein inhibitors** designed de novo[reference:15], and **ACE2 peptide-mimics** that block infection of pulmonary cells[reference:16]. AlphaFold2 also enabled **peptide inhibitor screening** targeting the spike heptad repeats[reference:17].

**Small-molecule discovery**

Structural knowledge of Mpro, informed by both experimental structures and AlphaFold predictions, underpinned the discovery of **small-molecule Mpro inhibitors**, including compounds that reached clinical development[reference:18]. The combination of predicted structures with **virtual screening of compound libraries** accelerated hit identification when experimental structures were limited.

**Repurposing of specific drugs**

Structure-based approaches identified **Navitoclax** as a candidate to block SARS-CoV-2 fusion and entry by targeting the heptad repeat 1 region of the S2 protein, suggesting a repurposing opportunity for an orally available broad-spectrum antiviral[reference:19][reference:20].

### 1.3 What COVID-19 demonstrated

- **Speed:** AI structure prediction compressed months of structural biology into days, enabling drug discovery to begin before experimental structures were available.
- **Validation matters:** The concordance of AlphaFold2 Mpro models with solution RDC data provided confidence that predictions could guide real drug discovery[reference:21].
- **Repurposing is a viable first line:** Combining predicted structures with approved-drug libraries produced actionable candidates rapidly[reference:22].
- **Limits remain:** Predicted structures supported, but did not replace, experimental validation and clinical testing.

---

## 2. Cancer

Cancer drug discovery has been the most active area for structure-based AI, spanning kinase inhibitors, steroidogenic enzyme inhibitors, nanobodies, and peptide scaffolds.

### 2.1 Prostate cancer: 3βHSD1 inhibitors

**Disease and target.** 3β-hydroxysteroid dehydrogenase type 1 (3βHSD1) converts DHEA to downstream androgens and correlates with tumor aggressiveness in prostate cancer. Its inhibitors, including biochanin-A (BCA), showed antitumor activity but suffered from **poor oral bioavailability**, and optimization was hindered by the **absence of experimental structural information** on 3βHSD1[reference:23][reference:24].

**Structural approach.** Researchers used **AlphaFold2** to construct detailed models of 3βHSD1 binding to substrates, then combined these models with the elucidated enzymatic mechanism to guide structure–activity relationship optimization of BCA-related compounds[reference:25][reference:26].

**Outcome.** The work produced **HEAL-116**, a potent 3βHSD1 inhibitor with **enhanced binding specificity**, improved oral absorption from incorporated hydrophilic groups, and robust antitumor effects in biochemical, cellular, and mouse models[reference:27]. The study explicitly demonstrated the **feasibility of using predicted structural models to optimize a lead compound** for clinical translation[reference:28].

### 2.2 Endometrial cancer: predicted peptide scaffolds

AlphaFold was used to model a self-assembling peptide (RFC) that formed a **stable α-helical structure with high confidence**, and these predicted scaffolds were then used for **drug screening in endometrial cancer organoids**[reference:29]. This illustrates structure prediction feeding directly into functional screening in patient-derived models.

### 2.3 DNA damage response targets and radiosensitizers

A comparative study screened **experimental, AlphaFold2, AlphaFold3, and RoseTTAFold All-Atom structures** of four DNA damage-response proteins (including ATM and DNA-PKcs) to identify **DNA-PKcs-binding candidate radiosensitizers**[reference:30]. The study found that **structure-source effects on ligand enrichment were target-dependent**, a useful caution for structure-based screening.

### 2.4 Antibody and nanobody design

AlphaFold3 structural priors were integrated with molecular dynamics to design a **picomolar anti-carcinoembryonic antigen (CEA) nanobody** with **KD ≈ 44 pM**, a ~306-fold affinity improvement over the parental clone, without compromising thermal stability[reference:31]. Separately, **de novo designed HER2-targeting protein minibinders** have been developed[reference:32], and AlphaFold has been discussed as a tool for **immunotherapy development in oral squamous cell carcinoma**[reference:33].

---

## 3. Neurodegenerative diseases

Neurodegenerative disorders are characterized by protein misfolding and aggregation, making them natural targets for structure-guided design—though also among the hardest because the relevant species are dynamic, heterogeneous, and often transient.

### 3.1 ALS: SOD1 aggregation

**Disease and target.** Mutations in Cu/Zn-superoxide dismutase (SOD1) cause ALS by shifting the equilibrium from the native homodimer toward an **aggregation-prone monomer** that forms amyloid-like fibrils[reference:34].

**Structural approach.** Machine-learning-based **de novo protein design** was used to create binders against **monomeric SOD1**. The designed binder **#313** was optimized to **#313-604**, and the **crystal structure of the #313-604–SOD1 complex closely matched the AlphaFold2-predicted model**, confirming the designed interface[reference:35].

**Outcome.** **#313-604 suppressed SOD1 aggregation in vitro**, demonstrating that de novo designed binders can directly modulate a disease-linked aggregation process[reference:36]. This is a proof of concept for structure-guided biologics in ALS.

### 3.2 Parkinson's disease: α-synuclein fibril inhibitors

**Target.** α-Synuclein fibrils are the pathological hallmark of Parkinson's disease and exist as **multiple structural polymorphs**, complicating inhibitor design.

**Structural approach.** A structure-guided framework combined **cryo-EM structural knowledge** with **AI-assisted peptide generation** (including ProteinMPNN) to target conserved β-sheet motifs across α-synuclein fibril polymorphs[reference:37][reference:38]. Separately, a de novo protein design pipeline used **AlphaFold-Multimer** to predict inhibitor–fibril complexes and filter candidates by structural stability and interfacial complementarity, targeting the **steric zipper interface**[reference:39].

**Outcome.** These studies produced **wide-spectrum peptide inhibitors** and **high-affinity de novo inhibitors** of α-synuclein fibrils, illustrating how AI structure prediction can address structural polymorphism—a central challenge in neurodegeneration[reference:40][reference:41].

### 3.3 Parkinson's disease: target discovery with structure validation

A **knowledge graph–based AI platform** (Standigm) was used to predict novel disease-modifying targets for Parkinson's disease, and **ColabFold/AlphaFold-Multimer v3** was used to generate the structural model of the **α-synuclein–TPP1 complex** for experimental validation[reference:42]. This shows structure prediction serving as a validation layer downstream of AI target discovery.

### 3.4 Alzheimer's disease

AI has been applied on two fronts. First, **AI screening of 6,361 cerebrospinal fluid proteins** identified four strongly associated with Alzheimer's, enabling **diagnostic tests** that predict the disease[reference:43]. Second, **AI-driven protein structure prediction and virtual screening** are being used to **rapidly pinpoint promising drug molecules**[reference:44]. A machine-learning protocol has also been developed to predict **structural distributions of amyloid-forming proteins from 2D IR spectra**, addressing the ensemble nature of amyloid structures[reference:45].

### 3.5 Batten disease (CLN3)

A **nine-step fragment-based drug discovery pipeline** was designed to create **pharmacological chaperones targeting CLN3** in neuronal ceroid lipofuscinosis type 3 (Batten disease), proceeding **from structure prediction to merged lead identification**[reference:46]. This is an example of structure prediction enabling a pipeline for a rare, severe neurodegenerative disease with few therapeutic options.

---

## 4. Rare and genetic diseases

### 4.1 KATP channelopathies: congenital hyperinsulinism

**Disease and target.** **KATP channel trafficking defects** cause congenital hyperinsulinism (CHI) unresponsive to diazoxide. The goal was a **pharmacochaperone** that restores functional channels to the cell surface[reference:47].

**Approach and outcome.** **AI-based virtual screening** (AtomNet) identified a novel compound, **Aekatperone**, which was structurally elucidated by **cryo-EM** and shown to enable **functional recovery of rescued channels**—a promising therapeutic for CHI caused by KATP trafficking defects[reference:48][reference:49][reference:50].

### 4.2 NALCN channelopathy (CLIFAHDD)

An **AI-enabled translational drug discovery framework** integrated phenotypic high-throughput screening with computational methods for NALCN channelopathy, identifying **aprepitant** as a lead therapeutic candidate for CLIFAHDD[reference:51][reference:52].

### 4.3 Hereditary transthyretin amyloidosis

An **in silico pipeline** integrating **AlphaFold3** for variant structure prediction, **ESM2** for variant classification, **DiffDock-L and AutoDock Vina** for molecular docking, **GROMACS** for molecular dynamics, and **Diff-SBDD** for ligand optimization and generation has been applied to protein misfolding in hereditary transthyretin amyloidosis[reference:53]. This represents a multi-tool structure-guided workflow for a rare amyloid disease.

---

## 5. Infectious diseases beyond COVID-19

### 5.1 Tuberculosis

AlphaFold2 and RoseTTAFold provide **near-experimental backbone accuracy** and the **AlphaFold Protein Structure Database** offers ready access to high-confidence models for many *Mycobacterium tuberculosis* targets[reference:54]. Specific applications include:

- **AdaA-AlkA bifunctional enzyme:** AlphaFold structure prediction, validated against *E. coli* homologs, yielded a high-confidence model and identified **enprofylline** as a candidate synergistic DNA-repair targeting agent[reference:55].
- **Dephospho-CoA kinase (CoAe):** **AlphaFold3** was used to predict the CoAe model, validated by Ramachandran plot and ProSA, offering insights for selective antituberculosis agent design[reference:56].
- **pncA mutations:** AlphaFold3 and trRosetta **outperformed template-based methods** (MODELLER, Swiss-Model, Phyre2) for modeling single-point mutations in the pncA gene, relevant to multidrug-resistant TB[reference:57].
- **MmcO multicopper oxidase:** AlphaFold2 predicted the MmcO structure, evaluated for accuracy, with implications for drug targeting[reference:58].
- **ThiL inhibitors:** A pipeline using **AlphaFold3/Boltz-2/Chai-1** metrics and Rosetta physics-based metrics aims to develop first-generation ThiL inhibitors[reference:59].

### 5.2 Malaria

Deep-learning structure prediction (AlphaFold2, AlphaFold3, ESMFold) has **fundamentally changed what is tractable** in the *Plasmodium falciparum* "dark proteome," enabling deorphanization of **hypothetical and putative proteins into validated antimalarial drug targets**[reference:60].

Specific examples:

- **Essential hypothetical proteins:** 3D structure prediction followed by molecular docking and dynamics simulation identified druggability of essential hypothetical proteins, with AlphaFold models refined and quality-checked using Galaxy WEB and SAVES[reference:61].
- **Inositol polyphosphate multikinase (IPMK1):** AlphaFold's highest-scoring model identified **five core ATP-binding residues** (Lys9, Glu364, Val366, Asp379, Asp624), highlighting IPMK1 as a novel therapeutic target[reference:62].
- **SERA6 egress protease:** **AlphaFold3** was used to model MSA180, followed by DALI structural comparison to investigate the parasite egress pathway and support inhibitor development[reference:63].
- **PfGCα and PfPKG:** AlphaFold2 was used to model the GC domain of PfGCα and mutated PfPKG to assess binding of an acyclic nucleoside phosphonate that blocks parasite egress[reference:64].
- **PfHAP2 fusogen:** Structural work on *P. falciparum* HAP2 domain 3 supports nanobody development against this malarial fusogen[reference:65].

### 5.3 Multidrug-resistant *Neisseria gonorrhoeae*

AI-integrated **proteome-wide target prioritization** has been applied to drug discovery against multidrug-resistant *N. gonorrhoeae*, combining deep-learning structure prediction with virtual screening (Atomwise platform) for anti-gonococcal lead discovery[reference:66].

---

## 6. Cross-cutting patterns

### 6.1 What structure prediction contributes

| Contribution | Example |
|---|---|
| **Filling structural gaps** | 3βHSD1 had no experimental structure; AlphaFold2 enabled lead optimization[reference:67] |
| **Validating predicted interfaces** | SOD1 binder crystal structure matched AlphaFold2 prediction[reference:68] |
| **Enabling repurposing** | SARS-CoV-2 Mpro + FDA-approved drug library[reference:69] |
| **Addressing polymorphism** | α-Synuclein fibril polymorphs targeted with AI-designed peptides[reference:70] |
| **Deorphanizing dark proteomes** | Malaria hypothetical proteins converted to drug targets[reference:71] |
| **Prioritizing targets** | Proteome-wide target prioritization for *N. gonorrhoeae*[reference:72] |
| **Designing biologics** | Picomolar anti-CEA nanobody, SOD1 binders, HER2 minibinders[reference:73][reference:74] |
| **Guiding pharmacochaperones** | KATP channel pharmacochaperone Aekatperone[reference:75] |

### 6.2 What remains difficult

- **Dynamic and disordered targets:** Amyloid proteins and IDPs require ensemble representations, not single static structures.
- **Structure-source dependence:** Ligand enrichment can vary depending on whether experimental or predicted structures are used, and this effect is **target-dependent**[reference:76].
- **Validation bottleneck:** Predicted structures generate hypotheses faster than experiments can validate them.
- **Clinical translation:** Most structure-guided programs described here are preclinical or early clinical; **no AI-discovered drug had received regulatory approval as of early 2026**, though more than **173 AI-discovered programs** had entered some stage of clinical development[reference:77].

### 6.3 The clinical frontier

The most advanced structure-guided programs include:

- **Rentosertib (Insilico Medicine):** A TNIK inhibitor for idiopathic pulmonary fibrosis with an **AI-discovered target and AI-generated structure**, now in **Phase III** (GENESIS-IPF). Phase IIa showed a mean FVC improvement of **+98.4 mL** at 60 mg QD versus a **−20.3 mL** decline in placebo[reference:78][reference:79][reference:80].
- **Isomorphic Labs oncology candidates:** Built on AlphaFold and the IsoDDE engine, **entered human trials in 2026**, following a **$600 million** funding round in 2025[reference:81][reference:82].
- **Lirafugratinib (Relay Therapeutics):** A computationally designed FGFR2 inhibitor that reached **FDA review with Priority Review** and a target action date of **27 September 2026**.

These programs will provide the first substantive tests of whether structure-guided AI drug discovery translates into clinical benefit.

---

## 7. Summary

| Disease area | Representative structural work | Drug discovery outcome | Status |
|---|---|---|---|
| **COVID-19** | Mpro validated against RDCs; spike–ACE2 models; variant modeling[reference:83][reference:84] | Repurposing hits; de novo miniproteins; Mpro inhibitors[reference:85][reference:86] | Multiple candidates; some reached clinical development |
| **Prostate cancer** | AlphaFold2 3βHSD1 models guided SAR[reference:87] | **HEAL-116**, potent oral 3βHSD1 inhibitor[reference:88] | Preclinical |
| **ALS** | De novo binders against monomeric SOD1; crystal structure matched AlphaFold2[reference:89] | **#313-604** suppressed SOD1 aggregation in vitro[reference:90] | Preclinical proof of concept |
| **Parkinson's** | AI-designed peptides targeting α-synuclein fibril polymorphs[reference:91] | Wide-spectrum fibril inhibitors[reference:92] | Preclinical |
| **Batten disease** | Nine-step structure-prediction-to-lead pipeline for CLN3[reference:93] | Pharmacological chaperone leads[reference:94] | Lead identification |
| **Congenital hyperinsulinism** | AI virtual screening + cryo-EM for KATP channel[reference:95] | **Aekatperone** pharmacochaperone[reference:96] | Preclinical |
| **Tuberculosis** | AlphaFold models for AdaA-AlkA, CoAe, pncA, MmcO[reference:97][reference:98][reference:99] | Enprofylline candidate; target models for inhibitor design[reference:100] | Target validation / lead discovery |
| **Malaria** | AlphaFold models of IPMK1, SERA6, PfGCα, PfPKG[reference:101][reference:102] | Druggability assessment of dark-proteome targets[reference:103] | Target discovery |
| **IPF** | AI-discovered TNIK target; AI-generated molecule[reference:104] | **Rentosertib** in Phase III[reference:105] | **Phase III** |

The common thread is that **structure prediction is most powerful when coupled to a concrete discovery step**—virtual screening, de novo design, SAR optimization, or target validation. It is least powerful when treated as an end in itself. The case studies above show that the coupling has produced real preclinical candidates and, in a few cases, clinical-stage programs.

---

[Back to README](../README.md) | [Previous: AI Drug Discovery Pipelines](07-ai-drug-discovery-pipelines.md)
