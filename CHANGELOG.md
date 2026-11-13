# Changelog

## v0.1.5
- Wording updates in `methods.csv`, the SEC-HPLC measurement notes, `ichorbio_bsr.json`,
  `data_dictionary.csv` and this changelog. No data values changed.
- Removed a column from `samples.csv` that held the same value (ichorbio) on every row.
- The ten entries listed under v0.1.4 are still being re-checked; their corrections follow in
  the next release.

## v0.1.4
- Added a **published reference developability table** (`developability_published_jain2017.csv`):
  the Jain et al. 2017 (PNAS, doi:10.1073/pnas.1616408114) assay panel — Fab Tm, HIC, AC-SINS, PSR
  and more — for 137 clinical-stage antibodies, 135 matched to ichorbio catalogue numbers. Kept in
  a separate file and labelled as published literature (re-made HEK293 IgG1), not ichorbio-measured.
- Added `jain2017_sequence_check.csv` recording Jain VH/VL vs the ichorbio listing
  (108 match, 23 no sequence on our listing, 4 differ).
- Added **Thera-SAbDab cross-reference links** (`thera_sabdab_url`) for the 458 antibodies with a
  Thera-SAbDab entry (by INN search link).
- **Removed** `host` (duplicated/ambiguous against `expression_system`), `sequence_source`
  (single-valued: IMGT/mAb-DB for all rows), and `imgt_url` (IMGT/mAb-DB has no per-drug link that
  can be derived from the INN; it uses an internal record ID, so only a generic homepage link was
  possible — dropped rather than kept as a non-specific link).
- Added a Hugging Face dataset-card `configs:` block so the viewer renders each file as its own
  table instead of failing on mismatched columns.
- **Ten entries are being re-checked** against IMGT: pertuzumab, ranibizumab, idarucizumab,
  abrezekimab, glenzocimab, lampalizumab, rivabazumab, tadocizumab, girentuximab and
  zenocutuzumab. Their sequences, format, target and computed values are unchanged from
  v0.1.3 in this release; the corrections will follow in v0.1.5.

## v0.1.3
- Expanded SEC-HPLC purity from 4 to **82 biosimilars**, from the full ichorbio CoA vault
  (coa.ichor.bio), with lot numbers and concentrations.
- For 68 of them, recorded the **exact monomer %** read from the CoA chromatogram peak table
  (280 nm main peak), replacing the earlier ">95%" placeholder; the other 14 keep the CoA's
  >95%/≥95% specification where no chromatogram is provided.

## v0.1.2
- Added the first SEC-HPLC purity values from ichorbio Certificates of Analysis for 4 biosimilars
  (Selicrelumab, Farletuzumab, Bococizumab, Romosozumab).
- Added a SEC-HPLC method (`M-SEC-HPLC`) and filled lot number + concentration on sample rows.

## v0.1.1
- Column and formatting cleanup of the antibodies table.
- Set `expression_system` to `CHO` for all antibodies.

## v0.1.0
- Seed release: 480 antibodies with sequences + identity; 960 computed values (MW, theoretical pI).
- Structure established (Antibodies/Samples/Methods/Measurements + data dictionary).
