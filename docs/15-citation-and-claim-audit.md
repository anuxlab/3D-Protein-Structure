# 15 — Citation and Claim Audit

[Back to README](../README.md) · [Reading list](14-reading-list-and-resources.md)

This repository contains a mixture of foundational science, rapidly changing model releases, company announcements, and disease-area examples. These categories require different standards of evidence.

## Source hierarchy

1. **Primary peer-reviewed research:** supports claims about methods and results within the paper's stated design and evaluation.
2. **Official dataset / model documentation:** supports access methods, release details, licensing, and intended usage.
3. **Regulatory agency and clinical-trial registry:** preferred for approval status, trial design, and official study records.
4. **Company filings and official announcements:** useful for company-reported pipeline status, clearly labeled as such.
5. **Reputable reporting and reviews:** useful context, but trace strong claims to primary evidence when possible.
6. **Social posts, search snippets, unattributed summaries:** discovery aids, not adequate sole citations for scientific claims.

## Claim checklist

Before merging a statement, ask:

- Does the source directly support the exact wording and number?
- Is the claim about a model benchmark, an experiment, a clinical trial, or a marketed medicine?
- Was the result retrospective or prospective? What was the comparator and test set?
- Does the paper report a mean, median, confidence interval, subgroup result, or a single example?
- Is the source peer-reviewed, a preprint, a company claim, or secondary reporting?
- Is the claim time-sensitive? If yes, what is the “as of” date?
- Are model weights, code, datasets, and results available under the stated terms?
- Could the claim be confused with proof of safety, efficacy, or clinical benefit?

## Legacy chapter review queue

The original chapters 01–08 were preserved to retain the project's existing scope. Before citing them in a paper, audit the following:

- **Chapters 01–07:** legacy tokens such as `[reference:0]` are not valid source links. Replace each with an inline DOI or canonical URL that directly supports the adjacent claim.
- **Chapter 03 and Chapter 07:** company funding, product/model releases, pipeline stages, trial status, and future milestones are time-sensitive. Verify each against a dated company filing, official announcement, trial registry, or regulator page. Attribute company-reported benchmark comparisons explicitly.
- **Chapter 08:** inspect every numbered reference and ensure that it links to a stable, specific source (paper, trial record, regulator, or article), rather than only a publisher homepage. Distinguish mechanistic evidence from clinical evidence.
- **All chapters:** remove or qualify superlatives such as “best,” “first,” “breakthrough,” and exact percentage improvements unless a clearly defined benchmark and comparator support them.

## Citation format examples

Markdown citations are simple and GitHub-native:

- Primary paper: `[Abramson et al. (2024), Nature](https://doi.org/10.1038/s41586-024-07487-w)`
- Database paper: `[Varadi et al. (2024), Nucleic Acids Research](https://doi.org/10.1093/nar/gkad1011)`
- Dataset portal: `[ChEMBL](https://www.ebi.ac.uk/chembl/)` (accessed YYYY-MM-DD)
- Mutable trial status: `[ClinicalTrials.gov record](https://clinicaltrials.gov/)` (checked YYYY-MM-DD; include the actual NCT link in the final claim)

## Suggested metadata for a source register

| Field | Purpose |
|---|---|
| `claim_id` | Stable identifier for the statement being supported |
| `claim_text` | Exact wording used in the docs |
| `source_url` / DOI | Canonical source |
| `source_type` | Primary paper, database, regulator, company, review |
| `publication_date` | Date of the source |
| `checked_date` | Date the URL and claim were checked |
| `evidence_scope` | What the source does and does not establish |
| `status` | Verified, needs review, outdated, disputed |

This audit page is intentionally conservative: it flags where source verification is required rather than implying that an unverified claim has been independently confirmed.
