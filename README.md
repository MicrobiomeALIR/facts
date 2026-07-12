# facts
FACTS: Fungal Airway Colonization and Translocation Study
# FACTS: Fungal Airway Colonization and Translocation Study

## *Candida* in the lower respiratory tract induces barrier disruption in mice and predicts poor outcomes in mechanically ventilated humans

**Kitsios Lab | University of Pittsburgh**

---

### Overview

This repository contains the R analysis code for the manuscript:

> Tolman NJ*, Choi W*, Coulter R, Snyder ME, Sharma L, Qin S, Morrell ED, Mikacenic C, Alder JK, Wang X, Tabary M, Zhang Y, Inman K, Britton N, Methe B, Benos PV, Bon J, Robinson K, Dela Cruz C, Nguyen MH, Morris A, Biswas P, Bain W†, Kitsios GD†. *Candida* in the lower respiratory tract induces barrier disruption in mice and predicts poor outcomes in mechanically ventilated humans. *Under revision

The code is provided for transparency and reproducibility. 

---

### Repository Structure

```
FACTS/
├── README.md
├── analysis_humans.Rmd          # Human cohort analyses (UPMC + UW)
├── analysis_invivo.Rmd          # Murine in vivo experimental analyses
└── outputs/                     # Generated figures and tables (not tracked)
```

---

### Analysis Scripts

#### 1. `analysis_humans.Rmd` — Human Clinical Cohort Analyses

Analyses of two independent prospective cohorts of mechanically ventilated patients with acute respiratory failure:

- **UPMC Cohort** (n=583 with culture data; n=201 with ITS sequencing)
  - ITS sequencing-based fungal profiling and *C. albicans* dominance thresholds
  - Clinical respiratory culture classification (hierarchical: *Candida* > bacterial pathogen > NRF)
  - Respiratory physiology (driving pressure, PaO2/FiO2 ratio, RALE scores)
  - Lung injury biomarkers (sRAGE, GDF-15, SPD, sST2, neutrophil elastase, IL-8, IL-6, sTNFR1, CRP)
  - Clinical outcomes (ventilator-free days, liberation from mechanical ventilation, 90-day survival)
  - Multivariable Cox proportional hazards models
  - Integrated 16S-ITS bacterial-fungal community clustering (Similarity Network Fusion)
  - Culture–sequencing overlap analysis

- **University of Washington Cohort** (n=155)
  - BAL quantitative culture results in suspected VAP
  - Respiratory physiology and clinical outcomes by culture group
  - BAL IL-8 concentrations

**Required input files:**
- `factsalir_12.23.25.csv` — Main UPMC cohort dataset
- `ITS_absolute_abundance.csv` — ITS sequencing absolute read counts
- `ITS_relative_abundance.csv` — ITS sequencing relative abundances
- `Mbiome_SampleMetadata_2.24.23.csv` — Microbiome sample metadata
- `MultiCompMbio_all_clusters_allCohorts_2.csv` — SNF cluster assignments
- `ALIR_EDTAPlasma_ELISA_Combined.xlsx` — Plasma CRP measurements
- UW cohort data (separate files, see script)

#### 2. `analysis_invivo.Rmd` — Murine Experimental Analyses

All murine intratracheal *C. albicans* models including:

- **Figure 2:** Single-hit CAN6 vs Vehicle (Day 1 and Day 2)
- **Figure 3:** Neutrophil depletion (PMN^DTR vs PMN^WT)
- **Figure 4:** Live vs heat-killed *C. albicans* (SC5314 and clinical isolate)
- **Figure 5:** Yeast-lock (TT21 vs TNRG1)
- **Figure 6:** Two-hit models (CAN+LPS and CAN+*P. aeruginosa*)
- **Supplemental:** Candidalysin mutants, histology scoring, yeast-lock + PA two-hit, CFU recovery

Data processing includes normalized lung weight calculation, weight loss trajectories, BAL neutrophil quantification, and log-transformed CFU analyses. All figures are generated programmatically with shared theme functions for consistent formatting.

**Required input files:**
- `FACTS_rawdata_allExp_06.29.26.xlsx` — Master experimental dataset (all experiments)
- `FACTS_histologyScores_12.5.24_merged.xlsx` — Histology scoring data
- `humanInvitroData.xlsx` — Human in vitro cytotoxicity and TEER data

---

### R Environment

Analyses were performed in R (version 4.3.1) with RStudio. Key packages:

| Package | Purpose |
|---------|---------|
| `tidyverse` | Data manipulation and visualization |
| `survival` / `survminer` | Survival analysis and Kaplan-Meier curves |
| `ggpubr` | Statistical annotations on figures |
| `ggbeeswarm` | Beeswarm overlay on boxplots |
| `patchwork` | Multi-panel figure assembly |
| `tableone` | Baseline characteristics tables |
| `readxl` | Excel file import |
| `pheatmap` | Heatmap generation |
| `nlme` | Linear mixed-effects models (histology) |

---

### Data Availability

- **Sequencing data:** Bulk RNA-seq deposited at GEO (GSE286207, GSE286208). ITS and 16S sequencing data available at SRA (PRJNA726955, PRJNA595346).
- **Clinical data:** D De-identified datasets are available upon reasonable request to the corresponding author (kitsiosg@upmc.edu) and will be released upon publication
- **Experimental data:** Raw experimental measurements supporting all murine figures are included in the master dataset.

---

### Contact

Georgios D. Kitsios, MD, PhD
Division of Pulmonary, Allergy, Critical Care and Sleep Medicine
University of Pittsburgh School of Medicine
Email: kitsiosg@upmc.edu

---

### License

This code is provided for academic and research purposes. Please cite the manuscript if you use or adapt this code.
