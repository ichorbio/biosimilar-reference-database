# ichorbio Biosimilar Reference Database — v0.1.3

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23350140.svg)](https://doi.org/10.5281/zenodo.23350140)

Open, citable developability & biophysical data for ichorbio's research-grade biosimilars.
Structured per the Developer Brief (Antibodies / Samples / Methods / Measurements; one row per value).

## What is in v0.1.3 (seed release)
- **480 antibodies** — identity, target + UniProt, isotype/format, heavy + light chain
  sequences (from IMGT/mAb-DB), ichorbio SKU, product URL and RRID where assigned.
- **960 theoretical measurements** — molecular weight and theoretical pI, **computed from the
  sequence** (clearly marked as theoretical in `methods.csv`, not laboratory values).
- **SEC-HPLC purity for 82 biosimilars**, taken from supplier Certificates of Analysis
  (coa.ichor.bio). 68 are the **exact monomer % read from the CoA chromatogram peak table**
  (280 nm main peak); the remaining 14 are reported against a >95% specification where the CoA
  gives no chromatogram.

## Added as the supplier's assays arrive (no rebuild needed)
Further developability data — Tm (DSF), HIC, AC-SINS, PSR, and more SEC-HPLC lots — plus
raw assay traces. Each new assay is added as rows in `measurements.csv`
(and a protocol in `methods.csv`), never as new columns.

## Files
antibodies.csv · samples.csv · methods.csv · measurements.csv · summary_wide.csv ·
data_dictionary.csv · sequences.fasta · ichorbio_bsr.json · dataset.jsonld ·
CITATION.cff · LICENSE.txt · llms.txt · README.md · CHANGELOG.md

(ichorbio_bsr.parquet is generated at build time with pyarrow — not included in this source drop.)

## How to cite
ichorbio (2026). ichorbio Biosimilar Reference Database (version 0.1.3) [Data set].
Zenodo. https://doi.org/10.5281/zenodo.23350140

The concept DOI above always resolves to the latest version; each release also has its own version DOI on Zenodo.

## Licence
CC BY 4.0. Data may be reused, including commercially, with attribution to ichorbio.

## Notes
- All antibodies are expressed in CHO.
- SEC-HPLC values are the monomer purity from the supplier CoA; exact figures are read from the
  chromatogram peak table (280 nm main peak). Where a CoA reports only a >95% specification, that
  is recorded with a note.
- Bispecific / fragment / IgM weights are theoretical sums of the construct chains; verify multivalent formats.
