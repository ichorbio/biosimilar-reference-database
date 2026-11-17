---
license: cc-by-4.0
pretty_name: ichorbio Biosimilar Reference Database
tags:
- biology
- antibodies
- biosimilars
- developability
- proteins
size_categories:
- n<1K
configs:
- config_name: antibodies
  data_files: antibodies.csv
- config_name: samples
  data_files: samples.csv
- config_name: methods
  data_files: methods.csv
- config_name: measurements
  data_files: measurements.csv
- config_name: summary_wide
  data_files: summary_wide.csv
- config_name: developability_published_jain2017
  data_files: developability_published_jain2017.csv
- config_name: jain2017_sequence_check
  data_files: jain2017_sequence_check.csv
- config_name: data_dictionary
  data_files: data_dictionary.csv
---

# ichorbio Biosimilar Reference Database — v0.1.7

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23350140.svg)](https://doi.org/10.5281/zenodo.23350140)

Open, citable developability & biophysical data for ichorbio's research-grade biosimilars.
Structured as Antibodies / Samples / Methods / Measurements, one row per value,
plus a separate published-reference developability table.

> **Viewer note:** each file is declared as its own config above, so the Hugging Face dataset
> viewer shows one table at a time from the dropdown (Antibodies, Samples, Measurements, the
> published developability set, and so on) instead of trying to merge files with different columns.

## What is in v0.1.7
- **478 antibodies** — identity, target + UniProt, isotype/format, heavy + light chain
  sequences (from IMGT/mAb-DB), ichorbio SKU, product URL, RRID where assigned, and a
  **Thera-SAbDab cross-reference link** for the 456 that have a Thera-SAbDab entry.
- **956 theoretical measurements** — molecular weight and theoretical pI, **computed from the
  sequence** (clearly marked as theoretical in `methods.csv`, not laboratory values).
- **SEC-HPLC purity for 81 biosimilars**, taken from ichorbio Certificates of Analysis
  (coa.ichor.bio). 67 are the **exact monomer % read from the CoA chromatogram peak table**
  (280 nm main peak); the remaining 14 are reported against a >95% specification where the CoA
  gives no chromatogram.
- **Published reference developability (Jain et al. 2017)** — see below.

## Published reference developability (Jain et al. 2017)
`developability_published_jain2017.csv` holds the biophysical assay panel from
Jain T, et al. *Biophysical properties of the clinical-stage antibody landscape.*
PNAS 2017;114(5):944–949. doi:[10.1073/pnas.1616408114](https://doi.org/10.1073/pnas.1616408114).

- 137 clinical-stage antibodies; **133 match an ichorbio catalogue number**, 110 of which are
  also in the sequence table above (the other 23 are catalogue items we do not yet list a
  sequence for).
- Assays include **Fab Tm (DSF), HIC, AC-SINS, PSR** (the priority four) plus SMAC, SGAC-SINS,
  accelerated-stability slope, CIC, CSI-BLI, ELISA, BVP-ELISA and HEK titre.
- These values are **not measured on ichorbio product**. The authors (Adimab) re-made every
  antibody in HEK293 cells in a common human IgG1 format, so every row is labelled
  `developability_source = "Published: Jain et al. 2017"` with the DOI, and the data is kept in a
  **separate file** from ichorbio-measured values. ichorbio's own Tm/HIC/AC-SINS/PSR testing on a
  first set of biosimilars is expected around the end of 2026 and will sit alongside this set, not
  overwrite it.
- Clinical status is recorded as **`clinical_status_2017`** (status at the time of the paper; many
  have since changed).
- Two assay conventions are carried through from the paper: an **HIC or SMAC retention time of
  25 min means the antibody did not elute**, and **AC-SINS Δλmax near 29.6 nm is at the top of the
  assay range**; both are called out in `special_value_notes`.

`jain2017_sequence_check.csv` records, per antibody, whether Jain's VH/VL matches our listing
(109 match; 23 have no sequence on our listing yet; 1 differs — omalizumab, where Jain et al.
document an unintended CDR-H2 mutation in their own construct).

## Added as ichorbio's own assays arrive (no rebuild needed)
Further **ichorbio-measured** developability — Tm (DSF), HIC, AC-SINS, PSR, and more SEC-HPLC lots —
plus raw assay traces. Each new ichorbio-measured assay is added as rows in `measurements.csv`
(and a protocol in `methods.csv`), never as new columns. Published third-party data such as Jain
2017 stays in its own file.

## Files
antibodies.csv · samples.csv · methods.csv · measurements.csv · summary_wide.csv ·
developability_published_jain2017.csv · jain2017_sequence_check.csv · data_dictionary.csv ·
sequences.fasta · ichorbio_bsr.json · dataset.jsonld · CITATION.cff · LICENSE.txt · llms.txt ·
README.md · CHANGELOG.md

(ichorbio_bsr.parquet is generated at build time with pyarrow — not included in this source drop.)

## How to cite
ichorbio (2026). ichorbio Biosimilar Reference Database (version 0.1.7) [Data set].
Zenodo. https://doi.org/10.5281/zenodo.23350140

The concept DOI above always resolves to the latest version; each release also has its own version DOI on Zenodo.
When using the Jain 2017 developability columns, please also cite the original paper (doi:10.1073/pnas.1616408114).

## Licence
CC BY 4.0. Data may be reused, including commercially, with attribution to ichorbio.

## Notes
- All ichorbio antibodies are expressed in CHO.
- Heavy/light chain sequences are the ichorbio product sequences (from IMGT/mAb-DB). A small number
  of multi-chain formats (bispecifics, T-cell engagers) list one representative heavy and light
  chain only; the `format` field flags these, and the full chain complement is noted there.
- SEC-HPLC values are the monomer purity from the ichorbio CoA; exact figures are read from the
  chromatogram peak table (280 nm main peak). Where a CoA reports only a >95% specification, that
  is recorded with a note.
- Bispecific / fragment / IgM weights are theoretical sums of the construct chains; verify multivalent formats.
