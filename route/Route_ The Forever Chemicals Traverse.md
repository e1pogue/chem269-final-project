# **Route ∞: The Forever Chemicals Traverse: PFAS Suspect Screening & Homologous Series Analysis in Environmental HRMS Data**

* ## Route ID: ∞

* Wall: Outdoors – First Ascents  
* Grade: 5.9  
* Routesetter: Elizabeth Pogue  
* Time:  
* Dataset: NORMAN list, environmental foam sample HRMS, underlying water sample HRMS, blank HRMS 

## **Why this route exists**

Per‑ and polyfluoroalkyl substances (PFAS) are environmentally persistent contaminants with diverse structures and wide industrial use. Their chemical diversity and low concentrations make manual identification in complex HRMS spectra impractical. Computational workflows enable systematic screening and pattern discovery.

This route guides students through building a computational workflow for nontargeted PFAS analysis using high‑resolution mass spectrometry (HRMS) data. The workflow emphasizes suspect screening and homologous series discovery, followed by a stretch comparison of surface foam and water samples.

---

## **Exercise 0 — The Knot Check**

**Goal:** Make data usable

* Load mzML files: [Foam sample](https://drive.google.com/file/d/1pMrlSOLAbiBwIekTIy3NpCNQ_OIDeYsR/view?usp=drive_link), [Underlying water sample](https://drive.google.com/file/d/11gIeZFYEsco-g8TouCeqX2OUQUcPCA5F/view?usp=drive_link), [Blank sample](https://drive.google.com/file/d/14KtKFzUTsuDFxcGV55HjSxxcs8DLJcSg/view?usp=drive_link)   
* Extract MS1 features from each file separately  
  * m/z   
  * RT   
  * intensity  
* Basic cleaning  
  * Remove low intensity (\<103) noise peaks  
  * Subtract peak intensities present in blank peaks  
  * Retain high-confidence features

**Questions:** How many peaks are in raw data compared to noise filtered data? Compared to noise filtered and blank subtracted data? Is the difference in number of peaks before and after blank intensity subtraction surprising?

**Checkpoint:** Cleaned data has fewer peaks than raw data

---

## **Exercise 1 — Feature Engineering**

**Goal:** Turn spectra into analyzable data

* Build feature table for each sample  
  * Rows \= detected peaks  
  * Columns \= samples  
  * Cells \= peak intensities

* Align features across samples  
  * Match by m/z tolerance ± 10 ppm  
  * Match by RT tolerance ± 0.2 min

* Normalize intensities  
  * Total ion current (TIC) normalization

* Visualize data quality  
  * TIC plots for foam and water  
  * Peak intensity distributions

**Output:** Aligned and normalized feature matrix for foam and water

---

## **Exercise 2 — Suspect Screening** 

**Goal:** Identify likely PFAS candidates

* Load [PFAS suspect list](https://zenodo.org/records/13808949?) (NORMAN database)  
  * Exact mass  
  * Formula   
  * Compound name  
* Perform exact-mass matching  
  * Set tolerance to 20 ppm  
  * Compare observed m/z to suspect masses

* Flag candidate peaks  
  * Compute mass error (ppm)  
  * Link to suspect identity  
* Summarize hits per sample  
  * Number of suspects per sample  
  * Most intense suspects

**Output:** Table of suspect PFAS features for each sample.

---

## **Exercise 3 — Homologous Series Discovery**

**Goal:** Use Kendrick Mass Defect to find fluorinated series in each sample.

* Compute Kendrick mass (CF2 base)  
* Compute Kendrick mass defect (KMD)  
* Plot KMD vs Kendrick mass  
* Detect aligned feature series  
* Group features into homologous families  
* Compare series members with suspect hits

**Output:**

* List of homologous series  
* Visual evidence of repeating fluorinated patterns

---

## **Exercise 4 — Optional: Foam vs Water Comparison**

**Goal:** Compare enrichment patterns

* Subset PFAS suspect features  
* Compare foam versus water intensities  
* Compute similarity or distance metrics  
* Build feature intensity matrix  
* Generate heatmap  
* Cluster samples  
* Visualize enrichment patterns

**Output:** Heatmap comparing PFAS feature intensities in foam vs water.

---

## **Deliverables**

* Suspect PFAS feature table  
* Homologous series list  
* Kendrick Mass Defect plot  
* m/z vs RT visualization  
* Foam vs water heatmap (stretch)  
* Reproducible notebook and code

---

## **End of Route**

Students completing this route will build a practical PFAS screening workflow and produce interpretable visualizations suitable for environmental HRMS analysis.

