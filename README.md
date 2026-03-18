# The Forever Chemicals Traverse
PFAS Suspect Screening & Homologous Series Analysis in Environmental HRMS Data

**Project Summary:** This project develops a computational workflow for nontargeted analysis of per- and polyfluoroalkyl substances (PFAS) in environmental samples using high-resolution mass spectrometry (HRMS). The workflow integrates feature detection, alignment, suspect screening, and homologous series discovery to systematically identify PFAS signatures in complex spectra. A comparative analysis of surface foam and underlying water samples highlights enrichment patterns and demonstrates the value of computational tools for environmental contaminant screening.


**Biological Problem and Motivation:** Per- and polyfluoroalkyl substances (PFAS), often called “forever chemicals,” are highly persistent environmental contaminants linked to ecological and human health risks. Their structural diversity, wide range in environmental concentrations, and occurrence in complex mixtures make manual spectral interpretation impractical. Advanced computational workflows are essential to detect, prioritize, and interpret PFAS signals in HRMS data, particularly in emerging contamination scenarios such as marine surface foam enrichment.


**Data Sources:**

- Environmental samples from the Tijuana River
  - [Surface foam HRMS data](https://drive.google.com/file/d/1pMrlSOLAbiBwIekTIy3NpCNQ_OIDeYsR/view?usp=sharing)
  - [Underlying water HRMS data](https://drive.google.com/file/d/11gIeZFYEsco-g8TouCeqX2OUQUcPCA5F/view?usp=sharing)
  - [Laboratory blank HRMS data](https://drive.google.com/file/d/14KtKFzUTsuDFxcGV55HjSxxcs8DLJcSg/view?usp=sharing)
- Reference database
  - [NORMAN Suspect List Exchange PFAS suspect list](https://zenodo.org/records/13808949?) (4,777 compounds)
    - Exact masses
    - Molecular formulas
    - Compound names

   
**Computational Approach & Workflow Overview:** 

The analysis pipeline combines mass spectrometry preprocessing with cheminformatics and statistical visualization:

  1. Data Preparation
     
    - mzML file import
    
    - MS1 feature extraction (m/z, retention time, intensity)
    
    - Noise filtering and blank subtraction

  3. Feature Engineering
     
    - Cross-sample feature alignment (m/z and RT tolerance)
    
    - Total Ion Current normalization
    
    - Feature matrix construction

  5. Suspect Screening
     
    - Exact mass matching to PFAS suspect database
    
    - ppm error calculation
    
    - Candidate feature annotation

  7. Homologous Series Discovery
     
    - Kendrick Mass Defect (CF₂ base) transformation
    
    - Series detection via aligned KMD patterns
    
    - Homologous family grouping

  9. Comparative Analysis
      
    - PFAS feature subsetting
    
    - Foam vs water intensity comparison
    
    - Hierarchical clustering and heatmap visualization


**Route Design and Completion:**
This project was structured as a guided computational “climbing route”:

Route ∞ — Outdoors: First Ascents
Grade: 5.9
Routesetter: Elizabeth Pogue

Exercises Completed

✅ Exercise 0 — Data cleaning and blank subtraction

✅ Exercise 1 — Feature alignment and normalization

✅ Exercise 2 — PFAS suspect screening

✅ Exercise 3 — Kendrick Mass Defect homologous series discovery

✅ Exercise 4 — Foam vs water comparative enrichment analysis

All route objectives were successfully completed, producing interpretable PFAS screening outputs and visualizations.


**Results Summary:**

Key outputs from the workflow include:

  - Suspect PFAS Feature Table- [Foam](results/tables/foam_suspects.csv) and [Water](results/tables/water_suspects.csv): 
Annotated candidate PFAS detected in foam and water samples.

  - Homologous Series List- [Foam](results/tables/foam_homologue_table.csv) and [Water](results/tables/water_homologue_table.csv):
Identified fluorinated series consistent with PFAS structural patterns.

  - Kendrick Mass Defect Plot- [Foam](results/figures/foam_kmd_plot.png) and [Water](results/figures/water_kmd_plot.png):
Visual evidence of repeating CF₂ units across detected features.

  - [m/z vs Retention Time Visualization](results/figures/TIC.png):
Overview of feature distribution and clustering.

  - Foam vs Water PFAS Heatmap- [unclustered](results/figures/heatmap.png) and [clustered]((results/figures/heatmap_clustered.png)):
Comparative visualization of enrichment patterns across sample types.


**Interpretations, Limitations, and Next Steps:**

- Interpretations
  - Surface foam shows enriched PFAS signal relative to underlying water.
  - Homologous series patterns support the presence of fluorinated compound families.
  - Suspect screening effectively prioritizes features for targeted validation.
 
- Limitations
  - Suspect screening provides putative identifications only (no MS/MS confirmation).
  - Matrix effects and ion suppression may influence relative intensities.
  - Alignment tolerances may merge near-isobaric species.

- Next steps:
  - MS/MS validation of high-priority suspects
  - Quantitative calibration for targeted PFAS
  - Expanded suspect libraries
  - Time-series monitoring for environmental trends


**Reproducibility Instructions:**

- Environment
  - Python ≥ 3.10
  - Google Colab–compatible

- Required Packages

'''bash

pip install pymzml pyopenms pandas numpy matplotlib seaborn

- How to Run
  - Clone this repository
  - Open the main notebook in Google Colab or Jupyter
  - Install dependencies
  - Run cells sequentially from top to bottom
