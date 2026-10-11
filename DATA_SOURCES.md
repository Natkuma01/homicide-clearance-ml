# Data Sources

This document records the provenance, intended use, and current status of the datasets considered for the Homicide Clearance Prediction project.

Dataset coverage dates describe when the underlying events occurred. They are separate from access or download dates. Where an exact access date cannot be verified, it is reported as unknown rather than estimated.

## 1. National Incident-Based Reporting System, 2023

**Current primary dataset**

| Field | Details |
|---|---|
| Dataset title | *National Incident-Based Reporting System, 2023: Extract Files* |
| Organization and publisher | U.S. Bureau of Justice Statistics; FBI Uniform Crime Reporting Program; distributed by ICPSR |
| Dataset page | [ICPSR Study 39270](https://www.icpsr.umich.edu/web/NACJD/studies/39270) |
| DOI | [10.3886/ICPSR39270.v2](https://doi.org/10.3886/ICPSR39270.v2) |
| Years covered | 2023 |
| Access or download date | Exact date not verified; available locally by October 2026 |
| Access conditions | Public-use data; ICPSR terms of use apply |
| Exact source file used | DS3 Incident-Level File, `39270-0003-Data.tsv` |
| Derived project file | `data/processed/nibrs_2023_homicides.csv` |
| Project status | Currently used for data-quality analysis, exploratory analysis, feature selection, and target investigation |

The original incident-level file contains 12,351,550 records and 391 columns. The project reads the approximately 11 GB source file in chunks and extracts 14,860 incidents whose first UCR offense code is murder or nonnegligent manslaughter (`V20061 == 91`).

The raw and derived datasets are not distributed in this GitHub repository. They must be obtained or regenerated in accordance with the source provider's terms.

## 2. Phoenix Homicide Clearance Initiative, 2003–2005

**Downloaded reference material; planned for a later phase**

| Field | Details |
|---|---|
| Dataset title | *Evaluation of the Phoenix, Arizona, Homicide Clearance Initiative, 2003–2005* |
| Principal investigator | J. Thomas McEwen, Institute for Law and Justice |
| Funding | National Institute of Justice |
| Distributor | ICPSR |
| Dataset page | [ICPSR Study 26081](https://www.icpsr.umich.edu/web/NACJD/studies/26081) |
| DOI | [10.3886/ICPSR26081.v1](https://doi.org/10.3886/ICPSR26081.v1) |
| Years covered | July 1, 2003–June 30, 2005 |
| Access or download date | Exact date not verified |
| Access conditions | Public-use files; ICPSR terms of use apply |
| Exact data file available | DS1 Homicide Cases Data, `26081-0001-Data.tsv` |
| Supporting file | `26081-0001-Codebook.pdf` |
| Project status | Reference material; no modeling use yet |

DS1 contains 404 Phoenix homicide cases. Its variables include investigators, patrol officers, witnesses, evidence categories, arrest type, and whether a case was open or closed.

This single-city evaluation study differs from the nationwide NIBRS data in population, time period, purpose, and variable definitions. Its records will not be combined directly with NIBRS without a documented compatibility assessment.

## 3. Murder Accountability Project Amplified Supplementary Homicide Reports

**Example/reference material; planned for a later phase**

| Field | Details |
|---|---|
| Dataset title | Amplified Supplementary Homicide Report data |
| Organizations | FBI Uniform Crime Reporting Program; compiled and expanded by the Murder Accountability Project |
| Dataset page | [Murder Accountability Project Data & Docs](https://www.murderdata.org/p/data-docs.html) |
| DOI | No verified DOI for this compilation |
| Years covered | The example filename suggests 1976–2025; the exact full-dataset version must be verified before analysis |
| Access or download date | Exact date not verified |
| Access conditions | Publicly downloadable files are available; reuse and redistribution terms should be confirmed before distributing data |
| Exact file available | `SHR76_25a-2-spreadsheet-example.txt` |
| Project status | Example/reference file; no modeling use yet |

The available file is a small spreadsheet example rather than a confirmed copy of the complete dataset. Its fields include `Solved`, `Year`, `VicAge`, `OffAge`, `Weapon`, `Relationship`, and `Circumstance`.

The MAP `Solved` field indicates whether an offender was identified when the report was made. That definition is not automatically equivalent to the NIBRS concept of clearance by arrest or exceptional means.

## Cross-dataset use

The three sources cover different time periods, populations, geographic scopes, observation units, and outcome definitions. They will not be appended or joined row by row merely because they all concern homicide.

Before any later cross-dataset analysis, the project will document:

- The unit of observation in each source
- The operational definition of cleared or solved
- The time at which the outcome was measured
- Comparable and non-comparable variables
- Missing-value and unknown-value conventions
- Geographic and temporal limitations
- Applicable access and redistribution terms

NIBRS 2023 remains the primary modeling dataset during the current phase. The Phoenix study may support a separate investigation of investigative factors, while MAP/SHR may support a separate historical comparison if the complete dataset and its version are verified.
