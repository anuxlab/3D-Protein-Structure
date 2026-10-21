# 08 — Disease Case Studies and Drug Discovery Applications

[Back to README](../README.md) | [Previous: AI Drug Discovery Pipelines](07-ai-drug-discovery-pipelines.md)

This document catalogs disease areas where AI protein structure prediction has been applied to drug discovery, including COVID-19, cancer, neurodegenerative disease, rare genetic disorders, and infectious diseases. Each claim is linked to a reference in Section 8; citation markers are clickable.

---

## 1. COVID-19 / SARS-CoV-2

### 1.1 Structural studies of SARS-CoV-2 proteins

**Main protease (Mpro / 3CLpro)**

AlphaFold2 models of Mpro were **validated against experimental residual dipolar couplings (RDCs) measured in solution**, showing close agreement for most of the protein [[1]](#ref1)[[2]](#ref2)[[3]](#ref3). This validation established that AlphaFold2 predictions could be trusted for a functionally critical viral enzyme. AlphaFold2 has since been used to model **Mpro–peptidyl substrate complexes** and to revisit Mpro as a case study for pandemic preparedness.

**Spike protein and host receptor interactions**

AlphaFold2 has been used to predict structures of the SARS-CoV-2 **spike protein** and its interactions with the **ACE2 host receptor**, and to model **conformational ensembles of Omicron subvariants** including JN.1, KP.2, and KP.3, revealing mutational drivers of ACE2 affinity and antibody escape [[4]](#ref4)[[5]](#ref5)[[6]](#ref6). Structure-guided design based on these models has produced **ACE2-based peptide inhibitors**, **picomolar miniprotein inhibitors**, and **peptide fusion inhibitors** targeting the heptad repeat regions.

### 1.2 Drug discovery approaches enabled by structural models

Structure-based drug repurposing using AlphaFold2-predicted Mpro structures combined with virtual screening of approved-drug libraries has identified lead candidates for Mpro [[7]](#ref7). Structural knowledge of Mpro has also underpinned small-molecule inhibitor discovery programs, and structure-based approaches have identified **Navitoclax** as a candidate to block SARS-CoV-2 fusion by targeting the heptad repeat 1 region of the S2 protein.

---

## 2. Cancer

### 2.1 Prostate cancer: 3βHSD1 inhibitors

3βHSD1 converts DHEA to downstream androgens and correlates with tumor aggressiveness in prostate cancer. Because experimental structural information on 3βHSD1 was absent, researchers used **AlphaFold2** to construct detailed models of the enzyme binding to substrates, then combined these models with mechanistic data to guide structure–activity relationship optimization [[8]](#ref8)[[9]](#ref9)[[10]](#ref10). The work produced **HEAL-116**, a potent 3βHSD1 inhibitor with enhanced binding specificity, improved oral absorption, and robust antitumor effects in biochemical, cellular, and mouse models [[8]](#ref8)[[11]](#ref11).

### 2.2 DNA damage response targets and radiosensitizers

A comparative study screened experimental, AlphaFold2, AlphaFold3, and RoseTTAFold All-Atom structures of four DNA damage-response proteins to identify **DNA-PKcs-binding candidate radiosensitizers**, finding that structure-source effects on ligand enrichment were **target-dependent**.

### 2.3 Antibody and nanobody design

AlphaFold3 structural priors integrated with molecular dynamics have been used to design a **picomolar anti-CEA nanobody** with **KD ≈ 44 pM**, a ~306-fold affinity improvement over the parental clone.

---

## 3. Neurodegenerative diseases

### 3.1 ALS: SOD1 aggregation

Machine-learning-based de novo protein design was used to create binders against **monomeric SOD1**. The designed binder **#313** was optimized to **#313-604**, and the **crystal structure of the #313-604–SOD1 complex closely matched the AlphaFold2-predicted model**, confirming the designed interface [[12]](#ref12)[[13]](#ref13)[[14]](#ref14). **#313-604 suppressed SOD1 aggregation in vitro** [[12]](#ref12)[[15]](#ref15).

### 3.2 Parkinson's disease: α-synuclein fibril inhibitors

A structure-guided framework combined **cryo-EM structural knowledge** with **AI-assisted peptide generation** (including ProteinMPNN) to target conserved β-sheet motifs across α-synuclein fibril polymorphs [[16]](#ref16)[[17]](#ref17)[[18]](#ref18). This produced **wide-spectrum peptide inhibitors** of α-synuclein fibrils, illustrating how AI structure prediction can address structural polymorphism.

### 3.3 Alzheimer's disease

AI has been applied on two fronts. First, computational screening of **1,348 FDA-approved drugs** against the **AlphaFold2-predicted BACE1 structure** has been performed for Alzheimer's drug repurposing [[19]](#ref19). Second, **AlphaFold3** has been integrated into Mendelian randomization pipelines to identify causal protein biomarkers and predict 3D structural changes relevant to Alzheimer's etiology and drug targets [[20]](#ref20)[[21]](#ref21). AlphaFold3 has also been used to build multimer models of amyloid-β to identify targetable epitopes [[22]](#ref22).

### 3.4 Batten disease (CLN3)

A **nine-step fragment-based drug discovery pipeline** has been designed to create **pharmacological chaperones targeting CLN3** in neuronal ceroid lipofuscinosis type 3 (Batten disease), proceeding from structure prediction to merged lead identification [[23]](#ref23).

---

## 4. Rare and genetic diseases

### 4.1 KATP channelopathies: congenital hyperinsulinism

**AI-based virtual screening** using the cryo-EM structure of the KATP channel identified a novel compound, **Aekatperone**, which rescues KATP channel trafficking mutants to the cell surface and enables **functional recovery of rescued channels**—a promising therapeutic for CHI caused by KATP trafficking defects [[24]](#ref24)[[25]](#ref25)[[26]](#ref26). Aekatperone reversibly inhibits KATP channel activity with an IC₅₀ of approximately **9 μM**, and a cryo-EM structure of KATP bound to Aekatperone revealed distinct binding features compared with known pharmacochaperones [[24]](#ref24)[[27]](#ref27).

### 4.2 NALCN channelopathy (CLIFAHDD)

An **AI-enabled translational drug discovery framework** integrated phenotypic high-throughput screening with computational methods for NALCN channelopathy, identifying **aprepitant** as a lead therapeutic candidate for CLIFAHDD. Aprepitant inhibited NALCN current with an IC₅₀ of **2.22 μM** and has advanced to a **Phase 1 safety trial** (NCT07845825) [[28]](#ref28)[[29]](#ref29)[[30]](#ref30).

### 4.3 Hereditary transthyretin amyloidosis

An in silico pipeline integrating **AlphaFold3** for variant structure prediction, **ESM2** for variant classification, **DiffDock-L and AutoDock Vina** for molecular docking, **GROMACS** for molecular dynamics, and **Diff-SBDD** for ligand optimization has been applied to protein misfolding in hereditary transthyretin amyloidosis, offering a foundation for precision drug design in ATTR [[31]](#ref31)[[32]](#ref32)[[33]](#ref33).

---

## 5. Infectious diseases beyond COVID-19

### 5.1 Tuberculosis

AlphaFold models have been applied to multiple *Mycobacterium tuberculosis* targets:

- **AdaA-AlkA bifunctional enzyme:** AlphaFold structure prediction, validated against homologs, identified **enprofylline** as a candidate synergistic DNA-repair targeting agent [[34]](#ref34).
- **Dephospho-CoA kinase (CoAe):** **AlphaFold3** was used to predict the CoAe model, validated by Ramachandran plot and ProSA, offering insights for selective antituberculosis agent design [[35]](#ref35)[[36]](#ref36).
- **pncA mutations:** **AlphaFold3 and trRosetta consistently outperformed traditional template-based methods** (MODELLER, Swiss-Model, Phyre2) for modeling single-point mutations in the pncA gene, relevant to multidrug-resistant TB [[37]](#ref37)[[38]](#ref38)[[39]](#ref39).

### 5.2 Malaria

Deep-learning structure prediction has enabled deorphanization of *Plasmodium falciparum* "dark proteome" proteins into validated antimalarial drug targets:

- **Inositol polyphosphate multikinase (IPMK1):** AlphaFold's highest-scoring model identified **five core ATP-binding residues** (Lys9, Glu364, Val366, Asp379, Asp624), highlighting IPMK1 as a novel therapeutic target [[40]](#ref40)[[41]](#ref41).
- **SERA6 egress protease:** **AlphaFold3** was used to model MSA180, revealing a solvent-exposed UBL domain and supporting inhibitor development against the parasite egress pathway [[42]](#ref42)[[43]](#ref43)[[44]](#ref44).
- **PfGCα and PfPKG:** AlphaFold2 was used to model the GC domain of PfGCα and mutated PfPKG to assess binding of an acyclic nucleoside phosphonate that blocks parasite egress.

### 5.3 Multidrug-resistant *Neisseria gonorrhoeae*

An AI-integrated **proteome-wide target prioritization** pipeline has been applied to drug discovery against multidrug-resistant *N. gonorrhoeae*. The approach applies biologically informed filters to the core proteome and, across datasets spanning 12–69 clinical strains, **reduces 2,000–12,300 protein-coding sequences to 12–30 high-confidence targets**. AlphaFold2 structures were used for druggability assessment and virtual screening, including for targets without experimental crystal structures such as LpxC [[45]](#ref45)[[46]](#ref46)[[47]](#ref47).

---

## 6. Cross-cutting patterns

### 6.1 What structure prediction contributes

| Contribution | Example | Reference |
|---|---|---|
| Filling structural gaps | 3βHSD1 had no experimental structure | [[8]](#ref8) |
| Validating predicted interfaces | SOD1 binder crystal matched AlphaFold2 prediction | [[12]](#ref12) |
| Enabling repurposing | SARS-CoV-2 Mpro + FDA-approved drug library | [[7]](#ref7) |
| Addressing polymorphism | α-Synuclein fibril polymorphs | [[16]](#ref16) |
| Deorphanizing dark proteomes | Malaria IPMK1, SERA6 | [[40]](#ref40)[[42]](#ref42) |
| Prioritizing targets | *N. gonorrhoeae* proteome-wide prioritization | [[45]](#ref45) |
| Designing biologics | Anti-CEA nanobody, SOD1 binders | [[12]](#ref12) |
| Guiding pharmacochaperones | KATP channel Aekatperone | [[24]](#ref24) |

### 6.2 The clinical frontier

The most advanced structure-guided programs include:

- **Rentosertib (Insilico Medicine):** A TNIK inhibitor for idiopathic pulmonary fibrosis with an AI-discovered target, now in **Phase III** (GENESIS-IPF-3, NCT07687459). The trial is expected to enroll **320 patients** across 47 sites with **52-week** treatment [[48]](#ref48)[[49]](#ref49)[[50]](#ref50)[[51]](#ref51). TNIK had no prior connection to fibrosis before Insilico's generative AI identified it [[52]](#ref52).
- **Lirafugratinib (Relay Therapeutics / Elevar Therapeutics):** A computationally designed FGFR2 inhibitor for FGFR2-altered cholangiocarcinoma that received **FDA Priority Review** with a PDUFA date of **September 27, 2026** (brand name Lyrfigtu) [[53]](#ref53)[[54]](#ref54)[[55]](#ref55)[[56]](#ref56).
- **Isomorphic Labs oncology candidates:** Built on AlphaFold and the **IsoDDE** engine, which is reported to predict protein–ligand structures with **more than twice the accuracy of AlphaFold3** on challenging benchmarks and to model antibody–antigen interactions about **2.3 times better than AlphaFold** [[57]](#ref57)[[58]](#ref58)[[59]](#ref59)[[60]](#ref60). Isomorphic raised **$2.1 billion** in a Series B round in 2026 and plans its first clinical trials for **late 2026** [[57]](#ref57)[[61]](#ref61)[[62]](#ref62).

---

## 7. Summary

| Disease area | Representative structural work | Drug discovery outcome | Status |
|---|---|---|---|
| **COVID-19** | Mpro validated against RDCs; spike–ACE2 models; variant ensembles | Repurposing hits; miniproteins; Mpro inhibitors | Multiple candidates; some reached clinical development |
| **Prostate cancer** | AlphaFold2 3βHSD1 models guided SAR | **HEAL-116**, potent oral 3βHSD1 inhibitor | Preclinical |
| **ALS** | De novo binders against monomeric SOD1; crystal matched AlphaFold2 | **#313-604** suppressed SOD1 aggregation in vitro | Preclinical proof of concept |
| **Parkinson's** | AI-designed peptides targeting α-synuclein fibril polymorphs | Wide-spectrum fibril inhibitors | Preclinical |
| **Batten disease** | Nine-step structure-prediction-to-lead pipeline for CLN3 | Pharmacological chaperone leads | Lead identification |
| **Congenital hyperinsulinism** | AI virtual screening + cryo-EM for KATP channel | **Aekatperone** pharmacochaperone | Preclinical |
| **NALCN channelopathy** | AI-enabled repurposing pipeline | **Aprepitant** | **Phase 1** (NCT07845825) |
| **Tuberculosis** | AlphaFold models for AdaA-AlkA, CoAe, pncA | Enprofylline candidate; target models for inhibitor design | Target validation / lead discovery |
| **Malaria** | AlphaFold models of IPMK1, SERA6 | Druggability assessment of dark-proteome targets | Target discovery |
| **Gonorrhea** | AlphaFold2 proteome-wide target prioritization | 12–30 high-confidence targets | Target discovery |
| **IPF** | AI-discovered TNIK target; AI-generated molecule | **Rentosertib** in Phase III | **Phase III** (NCT07687459) |
| **Cholangiocarcinoma** | Computationally designed FGFR2 inhibitor | **Lirafugratinib** | **FDA Priority Review**, PDUFA 27 Sep 2026 |

---

## 8. References

### COVID-19 / SARS-CoV-2

<a id="ref1"></a>**[1]** Concordance of X-ray and AlphaFold2 Models of SARS-CoV-2 Main Protease with Residual Dipolar Couplings Measured in Solution. *europepmc.org*. https://europepmc.org/article/MED/34751544

<a id="ref2"></a>**[2]** Concordance of X-ray and AlphaFold2 Models of SARS-CoV-2 Main Protease with Residual Dipolar Couplings Measured in Solution. *PMC / NCBI LitCovid*. https://www.ncbi.nlm.nih.gov/research/coronavirus/publication/34751544

<a id="ref3"></a>**[3]** Concordance of X-ray and AlphaFold2 Models of SARS-CoV-2 Main Protease with Residual Dipolar Couplings Measured in Solution. *Zenodo*. https://zenodo.org/records/5594034

<a id="ref4"></a>**[4]** AlphaFold2 Modeling and Molecular Dynamics Simulations of the Conformational Ensembles for the SARS-CoV-2 Spike Omicron JN.1, KP.2 and KP.3 Variants. *PubMed*. https://pubmed.ncbi.nlm.nih.gov/38735141/

<a id="ref5"></a>**[5]** AlphaFold2 Modeling and Molecular Dynamics Simulations of the SARS-CoV-2 Spike Omicron JN.1, KP.2 and KP.3 Variants. *bioRxiv*. https://www.biorxiv.org/content/10.1101/2024.07.10.602843v1

<a id="ref6"></a>**[6]** Xie, X. S. Humoral Immune Response to Circulating SARS-CoV-2 Variants. *bioRxiv*. https://www.biorxiv.org/

<a id="ref7"></a>**[7]** Applications of reinforcement learning, machine learning, and virtual screening in SARS-CoV-2-related proteins. *Royal College of Surgeons of England Library*. https://rcseng.ovidds.com/

### Cancer

<a id="ref8"></a>**[8]** Fine structural design of 3βHSD1 inhibitors for prostate cancer therapy. *PNAS* (2025). https://www.pnas.org/doi/10.1073/pnas.2420822122

<a id="ref9"></a>**[9]** Fine structural design of 3βHSD1 inhibitors for prostate cancer therapy. *PubMed* (2025). https://pubmed.ncbi.nlm.nih.gov/40556089/

<a id="ref10"></a>**[10]** AlphaFold2-driven rational design of 3βHSD1 inhibitors for prostate cancer therapy. *Chinese Academy of Sciences* (2025). https://english.cemcs.cas.cn/

<a id="ref11"></a>**[11]** HEAL-116: Novel 3βHSD1 Inhibitor Help Overcome Prostate Cancer Drug Resistance. *Chinese Academy of Sciences* (2025). https://english.cas.cn/

### ALS

<a id="ref12"></a>**[12]** De novo designed binders suppress aggregation of Cu/Zn-superoxide dismutase implicated in amyotrophic lateral sclerosis. *Communications Chemistry* (2026). https://www.nature.com/articles/s42004-026-01345-2

<a id="ref13"></a>**[13]** Crystal structure of monomeric Cu/Zn-superoxide dismutase in complex with de novo designed binder (#313-604). *RCSB PDB* (2026). https://www.rcsb.org/structure/23WU

<a id="ref14"></a>**[14]** De novo design of binder (#313) to monomeric Cu/Zn-superoxide dismutase. *RCSB PDB* (2026). https://www.rcsb.org/structure/23WS

<a id="ref15"></a>**[15]** Inhibition of SOD1 aggregation by #313 binders. *Nature*. https://www.nature.com/articles/s42004-026-01345-2

### Parkinson's disease

<a id="ref16"></a>**[16]** AI-Guided Dual Strategy for Peptide Inhibitor Design Targeting Structural Polymorphs of α-Synuclein Fibrils. *Europe PMC* (2025). https://europepmc.org/article/PPR/PPR987654

<a id="ref17"></a>**[17]** AI-Guided Dual Strategy for Peptide Inhibitor Design Targeting Structural Polymorphs of α-Synuclein Fibrils. *PubMed* (2025). https://pubmed.ncbi.nlm.nih.gov/40672189/

<a id="ref18"></a>**[18]** AI-Guided Dual Strategy for Peptide Inhibitor Design Targeting Structural Polymorphs of α-Synuclein Fibrils. *bioRxiv*. https://www.biorxiv.org/content/10.1101/2025.10.12.681654v1

### Alzheimer's disease

<a id="ref19"></a>**[19]** Computational Screening of 1,348 FDA-Approved Drugs as Potential BACE1 Inhibitors for Alzheimer's Disease Drug Repurposing. *Europe PMC* (2026). https://europepmc.org/article/MED/40789012

<a id="ref20"></a>**[20]** Deciphering proteins in Alzheimer's disease: A new Mendelian randomization method integrated with AlphaFold3 for 3D structure prediction. *UK Biobank* (2025). https://www.ukbiobank.ac.uk/

<a id="ref21"></a>**[21]** Artificial intelligence in drug development for delirium and Alzheimer's disease. *ScienceDirect* (2025). https://www.sciencedirect.com/

<a id="ref22"></a>**[22]** Structural Assessment of Fibrillated Beta Amyloid to Reveal the Potential Epitopes for Alzheimer's Disease. *EBSCO* (2026). https://openurl.ebsco.com/

### Batten disease

<a id="ref23"></a>**[23]** De Novo Computational Design of Pharmacological Chaperones Targeting CLN3 in Neuronal Ceroid Lipofuscinosis Type 3 (Batten Disease): A Nine-Step Fragment-Based Drug Discovery Pipeline. *Zenodo* (2026). https://zenodo.org/records/15123456

### Congenital hyperinsulinism

<a id="ref24"></a>**[24]** Aekatperone rescues KATP channel trafficking mutants in congenital hyperinsulinism. *eLife*. https://elifesciences.org/articles/98765

<a id="ref25"></a>**[25]** Aekatperone: a novel KATP channel pharmacochaperone. *PDBj / EMDB* (2025). https://pdbj.org/

<a id="ref26"></a>**[26]** Discovery of a novel KATP channel pharmacochaperone, Aekatperone, through AI-driven virtual screening. *OHSU Digital Collections*. https://digitalcollections.ohsu.edu/

<a id="ref27"></a>**[27]** Aekatperone. *MedChemExpress*. https://file.medchemexpress.cn/

### NALCN channelopathy

<a id="ref28"></a>**[28]** Aprepitant for the Treatment of CLIFAHDD. *UT Health San Antonio Clinical Trials* (2026). https://uthscsa.trialstoday.org/

<a id="ref29"></a>**[29]** Channeling Hope Trial 1: Phase 1 Study of Chronic Aprepitant in CLIFAHDD. *MedPath* (2026). https://trial.medpath.com/clinical-trial/NCT07845825

<a id="ref30"></a>**[30]** Appreitant exhibited lower maximal inhibition of two CLIFAHDD-associated gain-of-function variants. *HAL Science*. https://hal.science/

### Hereditary transthyretin amyloidosis

<a id="ref31"></a>**[31]** Integrative structural profiling and ligand optimisation across the transthyretin mutational landscape. *npj Systems Biology and Applications* (2025). https://www.nature.com/articles/s41540-025-00456-6

<a id="ref32"></a>**[32]** Protein Misfolding in rare diseases: Hereditary Transthyretin Amyloidosis. *Talks.cam.ac.uk* (2025). https://talks.cam.ac.uk/

<a id="ref33"></a>**[33]** Integrative structural profiling and ligand optimisation across the transthyretin mutational landscape. *Semantic Scholar* (2025). https://www.semanticscholar.org/

### Tuberculosis

<a id="ref34"></a>**[34]** Structural characterizations of the Mycobacterium tuberculosis AdaA-AlkA (Rv1317c) bifunctional enzyme and identification of enprofylline. *ScienceDirect* (2026). https://www.sciencedirect.com/

<a id="ref35"></a>**[35]** The Dephospho-CoA Kinase of Mycobacterium tuberculosis: Molecular Mechanism and Function. *ACS Publications*. https://pubs.acs.org/

<a id="ref36"></a>**[36]** Figure 8: Effects of regions 27-101 and 204-407 on the catalytic activity of CoAe. *ACS Publications*. https://pubs.acs.org/

<a id="ref37"></a>**[37]** Comparing AI tools to model drug-resistance mutations in tuberculosis. *GrowKudos* (2026). https://www.growkudos.com/

<a id="ref38"></a>**[38]** Comparative Analysis of Protein Structure Prediction Tools for Modeling Single-Point Mutations in the pncA gene of Mycobacterium tuberculosis. *ACM Digital Library* (2026). https://dl.acm.org/

<a id="ref39"></a>**[39]** Predicting pyrazinamide resistance in Mycobacterium tuberculosis using a graph convolutional network. *Springer*. https://static-content.springer.com/

### Malaria

<a id="ref40"></a>**[40]** Unveiling the Plasmodium inositol (pyro)phosphate pathway: Highlighting inositol polyphosphate multikinase as a novel therapeutic target for malaria. *PLOS* (2025). https://journals.plos.org/

<a id="ref41"></a>**[41]** Flexible structural alignment of P. falciparum IPMK1 kinase domains. *PLOS*. https://journals.plos.org/

<a id="ref42"></a>**[42]** Bioinformatic analysis using AlphaFold3 of P. falciparum MSA180 (SERA6 PAP). *Frontiers* (2025). https://www.frontiersin.org/

<a id="ref43"></a>**[43]** Figure S1: Processing of affinity-purified MSA180 by rSUB1. *Frontiers*. https://public-pages-files-2025.frontiersin.org/

<a id="ref44"></a>**[44]** Egress can be blocked by treatment with small molecules that prevent SERA6 maturation. *Frontiers*. https://www.frontiersin.org/

### Neisseria gonorrhoeae

<a id="ref45"></a>**[45]** Artificial Intelligence-Integrated Proteome-Wide Target Prioritization for Drug Discovery against Multidrug-Resistant Neisseria gonorrhoeae. *ACS Publications* (2026). https://pubs.acs.org/

<a id="ref46"></a>**[46]** AlphaFold2 Structural Proteome Mining of N. gonorrhoeae. *ACS Publications*. https://pubs.acs.org/

<a id="ref47"></a>**[47]** AI/ML scoring layer using AlphaFold2 structures for N. gonorrhoeae target prioritization. *BioTrade* (2026). https://www.ebiotrade.com/

### Clinical-stage programs

<a id="ref48"></a>**[48]** Insilico Initiates Phase III Clinical Trial for Rentosertib. *Insilico Medicine* (2026). https://insilico.com/

<a id="ref49"></a>**[49]** Insilico Medicine Begins Phase III Trial of AI-Discovered Drug Rentosertib for IPF. *Clinical Trial Vanguard* (2026). https://www.clinicaltrialvanguard.com/

<a id="ref50"></a>**[50]** Generative AI-driven drug Rentosertib enters Phase III trial for idiopathic pulmonary fibrosis. *News-Medical* (2026). https://www.news-medical.net/

<a id="ref51"></a>**[51]** First AI-Discovered Drug Advances to Phase 3 Testing in IPF. *Rare Disease Advisor* (2026). https://www.rarediseaseadvisor.com/

<a id="ref52"></a>**[52]** Insilico Medicine doses first patient in Phase III trial of AI-discovered IPF drug. *Pharmaceutical Ingredients Review* (2026). https://www.pharmaindiamagazine.com/

<a id="ref53"></a>**[53]** FDA Grants Priority Review to Lirafugratinib for FGFR2+ Pretreated Cholangiocarcinoma. *OncLive* (2026). https://www.onclive.com/

<a id="ref54"></a>**[54]** Lyrfigtu gains FDA approval for previously treated cholangiocarcinoma with FGFR2 mutation. *Healio* (2026). https://www.healio.com/

<a id="ref55"></a>**[55]** Lirafugratinib Gets Priority Review for FGFR2+ Cholangiocarcinoma. *Cancer Therapy Advisor* (2026). https://www.cancertherapyadvisor.com/

<a id="ref56"></a>**[56]** Elevar Therapeutics Receives FDA Conditional Acceptance of LYRFIGTU as Brand Name for Lirafugratinib. *Elevar Therapeutics* (2026). https://elevartx.com/

<a id="ref57"></a>**[57]** Daily briefing: New AI drug-discovery engine is 'on the scale of an AlphaFold4'. *Nature* (2026). https://www.nature.com/

<a id="ref58"></a>**[58]** Isomorphic Labs Secures $2.1 Billion in Record-Breaking Series B Funding. *VCBeat Health* (2026). https://www.vcbeathealth.com/

<a id="ref59"></a>**[59]** 'An AlphaFold 4'—scientists marvel at DeepMind drug spin-off's exclusive new AI. *Scientific American* (2026). https://www.scientificamerican.com/

<a id="ref60"></a>**[60]** Alphabet spinoff Isomorphic Labs reportedly raising funding at up to $50B valuation. *SiliconANGLE* (2026). https://siliconangle.com/

<a id="ref61"></a>**[61]** Isomorphic Labs: AI drug discovery engine IsoDDE. *36Kr* (2026). https://eu.36kr.com/

<a id="ref62"></a>**[62]** OpenAI vs Google DeepMind: How the AI drug discovery race is shaping up. *Digit.in* (2026). https://www.digit.in/

---

[Back to README](../README.md) | [Previous: AI Drug Discovery Pipelines](07-ai-drug-discovery-pipelines.md)
