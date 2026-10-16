# Changelog

## v0.1.3
- Expanded SEC-HPLC purity from 4 to **82 biosimilars**, from the full supplier CoA vault
  (coa.ichor.bio), with lot numbers and concentrations.
- For 68 of them, recorded the **exact monomer %** read from the CoA chromatogram peak table
  (280 nm main peak), replacing the earlier ">95%" placeholder; the other 14 keep the CoA's
  >95%/≥95% specification where no chromatogram is provided.

## v0.1.2
- Added the first SEC-HPLC purity values from supplier Certificates of Analysis for 4 biosimilars
  (Selicrelumab, Farletuzumab, Bococizumab, Romosozumab).
- Added a SEC-HPLC method (`M-SEC-HPLC`) and filled lot number + concentration on sample rows.

## v0.1.1
- Column and formatting cleanup of the antibodies table.
- Set `expression_system` to `CHO` for all antibodies.

## v0.1.0
- Seed release: 480 antibodies with sequences + identity; 960 computed values (MW, theoretical pI).
- Structure established (Antibodies/Samples/Methods/Measurements + data dictionary).
