# MRI Safety Thesis -- Analysis Code & Data

**Author:** Daniel Juarez Luna  
**Institution:** Creighton University, MSc Medical Physics  
**Advisor:** Michael G. Nichols, PhD  
**Thesis title:** Magnetically Induced Forces on Temporary Epicardial Leads: Experimental Device Development and Clinical Testing  
**Status:** Completed -- pending committee approval for formal submission (April 2026)

---

## Overview

This repository contains all Jupyter notebooks, raw experimental data, and generated
figures supporting the above MSc thesis. The work quantifies magnetically induced
translational forces and torques on retained post-surgical epicardial pacing leads
in the static field of a 3T MRI scanner, using three custom non-magnetic fixtures
developed and validated in the lab before clinical deployment at CHI Health
CUMC-Bergan Mercy, Omaha NE.

The clinical analysis pipeline follows ASTM F2052-15 (Standard Test Method for
Measurement of Magnetically Induced Displacement Force on Medical Devices in the
MR Environment) and draws conceptually from ASTM F2213-17 (Standard Test Method
for Measurement of Magnetically Induced Torque).

All code, data, and notebooks live inside the JupyterLab/ subfolder. This mirrors
the local working directory structure. Navigate there first.

---

## A note on notebook organization

Each experimental folder contains a mix of notebooks reflecting the actual
development process -- early attempts, working drafts, and final analyses often
sit side by side. The notes below identify which notebooks produced the reported
results and figures, and which are working history kept for transparency.

Figure files are currently stored alongside notebooks within each folder. Moving
figures into dedicated subfolders is noted as a future cleanup task and will be
done after formal thesis submission. Any such commit will be documentation only
and will not affect the analysis code or data.

---

## Repository Structure

All paths below are relative to JupyterLab/.

---

### BfieldSIM/ -- Magnetic field simulation and solenoid mapping

| Notebook | Role |
|---|---|
| FieldMapping.ipynb | PRIMARY MODEL. Finite solenoid simulation using the Biot-Savart approach. Produces the background chapter field profile figure and the chi/rho scaling table. |
| BfieldAnalysis.ipynb | PRIMARY ANALYSIS. Step-by-step processing of gaussmeter data from the lab solenoid. Produces results chapter figures (B vs z, dB/dz, B times grad B). |
| Bfield.ipynb | First attempt at solenoid simulation. Superseded by FieldMapping.ipynb, kept for reference. |
| BfieldMapping.ipynb | First attempt at visualizing solenoid field data. Superseded by BfieldAnalysis.ipynb, kept for reference. |

Thesis figures: combined_figure41.png and combined_gradients42.png correspond to
Figures 4.1 and 4.2 in the thesis. Other .png files in this folder are intermediate
or exploratory outputs.

Raw data: BfieldMapData/ contains gaussmeter CSV files (gm2_set_5 through
gm2_set_10) and landmark Excel files used for spatial registration.

---

### Translational/ -- Lab translational force experiment

| Notebook | Role |
|---|---|
| FitSus.ipynb | PRIMARY. Full pipeline: susceptibility fitting, tan(alpha) vs B times grad B, uncertainty propagation, chi_m extraction. Referenced in thesis methodology Chapter 3 and results Chapter 4. |
| AppendixB.ipynb | Lab report appendix submitted for PHY797 DIR (Direct Independent Research), written alongside the FitSus work during that course. Not part of the thesis itself. |
| Mini Project exploration/ | Early vector potential exploration in Mathematica and notebook form. Background reading, not part of reported results. |

Raw data: RawMeasurments.csv, RawMeasurmentsMagneticfield.csv,
RawMeasurmentsMagneticfieldGrad.csv  
Processed data: cleanData.csv, cleanDatawstdsem.csv  
Publication figures: Assests/ folder contains Residuals_Plot.png and related
final figures  
3D print file: smaller-optimized-honycombCard for MRI.stl -- hexagonal mesh basket
used to hold test objects on the pendulum fixture (Figure 3.9 in thesis)

---

### Torque/ -- Torque sensor development and lab measurements

#### Torque/Calibration/

This folder has no single primary notebook. Reported content is spread across
multiple notebooks reflecting how the calibration developed iteratively.

| Notebook | Role |
|---|---|
| Torque-plots.ipynb | First attempt at calibration curves. Glass and plastic sensor curves from this notebook appear in Appendix E of the thesis. |
| Torque-plots-Copy1.ipynb | Contains the final calibration slope for the aluminum sensor, noise level measurement, and the reported detection limit. Closest to a primary notebook in this folder. |
| Upright-Torque-plots.ipynb | First attempt at upright sensor orientation -- exploratory only, nothing reported. |
| Upright-Torque-plots-Copy1.ipynb | Tests and visualization attempts for upright orientation data. |
| Upright-Torque-plots-Copy2.ipynb | Better visualization pass. Contains the 1/r fit and sensor position optimization plots that appear in Appendix E. |
| data_compiler.ipynb | Compiles raw .dat run files into merged dataframes for the calibration notebooks. |

Raw data: dataTorque/ (first calibration session) and New_dataTorque/ (updated
session). Each contains per-rod, per-orientation CSV files.  
Key output figures: inverseRfitFr.png, powerFitFr.png, table_min_detect_mass_alt.png

#### Torque/MRIForces/

| Notebook | Role |
|---|---|
| Torque_Analysis_v2.ipynb | PRIMARY. Structured final analysis of lab torque measurements. Covers Helmholtz coil trials (long rod) and neodymium magnet trials (short rod), fits the tau proportional to B squared dependence, and produces all reported torque figures and summary CSVs. |
| Torque_again.ipynb | Second attempt focused on what was measurable. Some material went to a poster presentation but nothing carried into the thesis. Kept for reference. |
| Torque Presentation.ipynb | First attempt -- exploratory fits and interpretation. Superseded, kept for reference. |

Raw data: Helmholtz long-rod and short-rod trial CSVs, neodymium short-rod trial
CSVs, and angle-dependent measurement files.  
Publication figures: fig_torque_LR.png (Figure 4.12), fig_torque_SR_neo.png
(Figure 4.13)  
Output data: torque_mindetectable.csv, torque_results_summary.csv

---

### ClinicalData/ -- Primary clinical analysis

Real magnetic flux density measurements taken at the bore entrance of the 3T
Siemens Magnetom scanner at CUMC-Bergan Mercy, Omaha NE. Grid coordinate labels
(00, A3, A6, D3, G3, G6) refer to positions on the custom PVC mapping fixture
described in thesis Chapter 3. Analysis follows ASTM F2052-15.

#### How the three notebooks connect

ClinicalBfieldAnalysis.ipynb and Translational_F2052.ipynb are upstream notebooks
that each handle one half of the F2052-15 analysis -- field characterization and
pendulum deflection respectively. Both notebooks contain partial prediction attempts
that are intentionally incomplete on their own. Each saves its results to a .pkl
file. MRI_F2052_Comparison.ipynb loads both .pkl files and produces the full
compliance report, allowable gradient extrapolation, and cross-coordinate
predictions.

To reproduce: run ClinicalBfieldAnalysis.ipynb and Translational_F2052.ipynb
first (in either order), then run MRI_F2052_Comparison.ipynb.

```
ClinicalBfieldAnalysis.ipynb          Translational_F2052.ipynb
   (MappingBField/)                      (TranslationalExperiment/)
         |                                         |
         |  outputs/clinical_summary.pkl           |  outputs/mean_results.pkl
         +------------------+-----------------------+
                            |
                            v
                 MRI_F2052_Comparison.ipynb
                  (cross-analysis and F2052-15 report)
```

#### MappingBField/

| Notebook | Role |
|---|---|
| ClinicalBfieldAnalysis.ipynb | PRIMARY. Full multi-coordinate pipeline: load CSVs, remove outliers, crop static ends, split sub-runs, convert time to position, compute B and dB/dz and B times grad B via central differences, produce summary table. Saves outputs/clinical_summary.pkl for downstream use. |
| G6ClinicalBfieldAnalysis.ipynb | Earlier G6-only analysis. Superseded by the full pipeline above, kept for reference. |
| GaussmeterReps.ipynb | Repeatability study. Work in progress -- being continued by junior lab members. |

Raw data: DataCollectionFolderMRIProject/ contains 15 CSV files, one per coordinate
per pass direction (forward and backward). Also archived as .7z.  
Per-coordinate figures: betterPlots/ contains B, dB/dz, and B times grad B vs
position for each grid point.  
Summary figures: allCoords_betterPlots/ contains summary_B.png, summary_dBdz.png,
summary_BgradB.png, and summary_vertical_overlay_clean.png.

#### TranslationalExperiment/

| Notebook | Role |
|---|---|
| Translational_F2052.ipynb | PRIMARY. ASTM F2052-15 pendulum protocol: parse CSV, compute alpha and tan(alpha), average across trials, compute force ratio FR, run Appendix X3 extrapolation. Saves outputs/mean_results.pkl for downstream use. |

Raw data: Translational Data taken around G6 - Sheet1.csv -- hand-recorded pendulum
displacement measurements for Ti coil, Medtronic STREAMLINE 6492 unipolar epicardial
lead, Ti straight rod, and 316L stainless steel.  
Publication figures: F2052_FR_vs_position_pub.png (Figure 4.7),
F2052_max_FR_comparison_pub.png (Figure 4.8)

#### ClinicalData/ root level

| Notebook | Role |
|---|---|
| MRI_F2052_Comparison.ipynb | PRIMARY. Links both upstream pipelines. Loads .pkl outputs, identifies test location per ASTM F2052-15 section 8.1, extracts measured B0 and grad B from the field map, runs Appendix X3 extrapolation for all devices at 1.5T and 3.0T, produces consolidated compliance report. |
| Map_translational.ipynb | Earlier combined notebook that attempted to do everything in one place. Superseded by the split pipeline above, kept for reference. |

Publication figures: comparison_FR_per_coordinate_pub.png (Figure 4.10),
comparison_allowable_gradient_pub.png (Figure 4.9)

---

### MapField/ -- Gaussmeter sampling rate raw data

Raw .csv and .dat files from the sampling rate characterization experiment
described in FindSampleRateMagFieldMap.ipynb at the JupyterLab/ root level.
This tested the gaussmeter acquisition rate under low-flux conditions. Result:
0.25 s sampling interval was used in the clinical session; subsequent analysis
suggested 0.5 s would have been more appropriate. This is discussed in thesis
Chapter 3.

---

### Poster1/ -- Early learning material

Brights Thesis/RescaleFigures.ipynb was created at the start of the project to
reproduce figures from a prior student's RF heating thesis while learning Python
and Jupyter. Included for completeness, not part of reported results.

---

### SmallestTorquecalcs.xlsx

Spreadsheet backing the sample calculations in thesis Appendix B.3 (Smallest
measurable torque on fixture). Shows worked numerical examples for the cantilever
beam strain equations and detection limit estimation. This is not a final result --
the reported minimum detectable torque comes from the calibration notebook.

---

## Full Repository Tree

```
mri-translational-force-n-torque-analysis/
├── README.md
├── LICENSE
├── .gitignore
└── JupyterLab/
    ├── .gitignore
    ├── FindSampleRateMagFieldMap.ipynb        # Gaussmeter sampling rate test
    ├── SmallestTorquecalcs.xlsx               # Appendix B.3 sample calculations
    ├── MapField/                              # Raw data for sampling rate test
    │   ├── FindSampleRate.csv
    │   ├── FindSampleRate2.csv
    │   ├── FindSampleRate2_run1.dat
    │   ├── FindSampleRate2_run2.dat
    │   ├── FindSampleRate2_run3.dat
    │   ├── FindSampleRate2_run4.dat
    │   ├── FindSampleRate2_run5.dat
    │   ├── FindSampleRate3.csv
    │   ├── FindSampleRate3_run1.dat
    │   ├── FindSampleRate3_run2.dat
    │   ├── FindSampleRate_run1.dat
    │   ├── FindSampleRate_run2.dat
    │   ├── FindSampleRate_run3.dat
    │   └── FindSampleRate_run4.dat
    ├── BfieldSIM/
    │   ├── FieldMapping.ipynb                 # PRIMARY MODEL: solenoid simulation
    │   ├── BfieldAnalysis.ipynb               # PRIMARY ANALYSIS: solenoid data
    │   ├── Bfield.ipynb                       # First attempt (reference)
    │   ├── BfieldMapping.ipynb                # First attempt (reference)
    │   ├── combined_figure41.png              # Thesis Figure 4.1
    │   ├── combined_gradients42.png           # Thesis Figure 4.2
    │   ├── [intermediate figures]
    │   └── BfieldMapData/
    │       ├── gm2_set_5.csv
    │       ├── gm2_set_6.csv
    │       ├── gm2_set_7.csv
    │       ├── gm2_set_8.csv
    │       ├── gm2_set_8_landmarked.csv
    │       ├── gm2_set_9.csv
    │       ├── gm2_set_9_landmarked.csv
    │       ├── gm2_set_10.csv
    │       ├── landmarked.xlsx
    │       └── landmarks.xlsx
    ├── Translational/
    │   ├── FitSus.ipynb                       # PRIMARY: susceptibility fit
    │   ├── AppendixB.ipynb                    # PHY797 DIR lab report appendix
    │   ├── RawMeasurments.csv
    │   ├── RawMeasurmentsMagneticfield.csv
    │   ├── RawMeasurmentsMagneticfieldGrad.csv
    │   ├── cleanData.csv
    │   ├── cleanDatawstdsem.csv
    │   ├── curve_fit_plot.png
    │   ├── linear_fit.png
    │   ├── FitSus.html
    │   ├── FitSus_files/
    │   ├── smaller-optimized-honycombCard for MRI.stl
    │   ├── Assests/                           # Publication figures
    │   │   ├── Residuals_Plot.png
    │   │   ├── Angle_vs_Field.png
    │   │   ├── Displacement_vs_Current.png
    │   │   ├── Force_vs_Field.png
    │   │   ├── Uncertainty_Propagation_Plot.png
    │   │   └── magField_behavior_SI.png
    │   └── Mini Project exploration/
    │       ├── MRI_Safety_Phase1_VectorPotential.ipynb
    │       └── demo4.nb
    ├── Torque/
    │   ├── Calibration/
    │   │   ├── Torque-plots.ipynb             # Glass and plastic curves (Appendix E)
    │   │   ├── Torque-plots-Copy1.ipynb       # Aluminum sensor final calibration
    │   │   ├── Upright-Torque-plots.ipynb     # First upright attempt (reference)
    │   │   ├── Upright-Torque-plots-Copy1.ipynb
    │   │   ├── Upright-Torque-plots-Copy2.ipynb  # 1/r fit and position plots (Appendix E)
    │   │   ├── data_compiler.ipynb
    │   │   ├── df_merged.csv
    │   │   ├── compiled_torque_july4.dat
    │   │   ├── compiled_torque_july11.dat
    │   │   ├── compiled_upright_torque_july4.dat
    │   │   ├── compiled_upright_torque_july11.dat
    │   │   ├── inverseRfitFr.png
    │   │   ├── powerFitFr.png
    │   │   ├── table_min_detect_mass_alt.png
    │   │   ├── rod_characteristics_table.png
    │   │   ├── rod_characteristics_table.tex
    │   │   ├── 1stTrials_50_90.png
    │   │   ├── dataTorque/                    # First calibration session
    │   │   ├── dataTorque.zip
    │   │   ├── New_dataTorque/                # Updated calibration session
    │   │   └── New_dataTorque.zip
    │   └── MRIForces/
    │       ├── Torque_Analysis_v2.ipynb       # PRIMARY: final torque analysis
    │       ├── Torque_again.ipynb             # Second attempt (poster, reference)
    │       ├── Torque Presentation.ipynb      # First attempt (reference)
    │       ├── Helmholtz-Torque-Data1-73025.csv
    │       ├── Helmholtz-Torque-Data1-80425.csv
    │       ├── Helmholtz-Torque-Data2LR-73025.csv
    │       ├── Helmholtz-Torque-DataLR-73125.csv
    │       ├── TorqueMeasurement_SR_120825.csv
    │       ├── TorqueMeasurement_SR_120825_cont.csv
    │       ├── TorqueMeasurement_SR_120825_all.csv
    │       ├── torqueangles_0to45.csv
    │       ├── torqueangles_30to150.csv
    │       ├── fig_torque_LR.png              # Thesis Figure 4.12
    │       ├── fig_torque_SR_neo.png          # Thesis Figure 4.13
    │       ├── torque_SR_neoFits.png
    │       ├── torque_LR_fits.png
    │       ├── torque_SR_helm.png
    │       ├── torque_angle_check.png
    │       ├── torque_clinical_projection.png
    │       ├── fig_torque_projection.png
    │       ├── torque_mindetectable.csv
    │       └── torque_results_summary.csv
    ├── ClinicalData/
    │   ├── MRI_F2052_Comparison.ipynb         # PRIMARY: cross-analysis and report
    │   ├── Map_translational.ipynb            # Earlier combined notebook (reference)
    │   ├── comparison_FR_per_coordinate.png
    │   ├── comparison_FR_per_coordinate_pub.png   # Thesis Figure 4.10
    │   ├── comparison_allowable_gradient.png
    │   ├── comparison_allowable_gradient_pub.png  # Thesis Figure 4.9
    │   ├── MappingBField/
    │   │   ├── ClinicalBfieldAnalysis.ipynb   # PRIMARY: full field mapping pipeline
    │   │   ├── G6ClinicalBfieldAnalysis.ipynb # Earlier G6-only (reference)
    │   │   ├── GaussmeterReps.ipynb           # Repeatability study (WIP)
    │   │   ├── repeated_flux_analysis.png
    │   │   ├── DataCollectionFolderMRIProject/    # Raw CSVs: 00, A3, A6, D3, G3, G6
    │   │   ├── DataCollectionFolderMRIProject.7z
    │   │   ├── betterPlots/                   # Per-coordinate B, dB/dz, B times grad B
    │   │   ├── allCoords_betterPlots/         # Summary figures across all coordinates
    │   │   │   ├── summary_B.png
    │   │   │   ├── summary_dBdz.png
    │   │   │   ├── summary_BgradB.png
    │   │   │   └── summary_vertical_overlay_clean.png
    │   │   ├── G6betterPlots/                 # Earlier G6-only figures (reference)
    │   │   └── outputs/
    │   │       └── clinical_summary.pkl
    │   └── TranslationalExperiment/
    │       ├── Translational_F2052.ipynb      # PRIMARY: F2052-15 pendulum protocol
    │       ├── Translational Data taken around G6 - Sheet1.csv
    │       ├── F2052_FR_vs_position.png
    │       ├── F2052_FR_vs_position_pub.png   # Thesis Figure 4.7
    │       ├── F2052_max_FR_comparison.png
    │       ├── F2052_max_FR_comparison_pub.png    # Thesis Figure 4.8
    │       └── outputs/
    │           ├── mean_results.pkl
    │           └── translational_summary.pkl
    └── Poster1/
        └── Brights Thesis/
            └── RescaleFigures.ipynb           # Early learning notebook (reference)
```

---

## Dependencies

```
pandas  numpy  scipy  matplotlib
```

```bash
pip install pandas numpy scipy matplotlib
```

No additional libraries required. Inter-notebook data exchange uses Python's
built-in pickle module. No parquet engine needed.

---

## Appendix F -- Repository Archive Record

This section is the timestamp record referenced in Appendix F of the thesis. It
documents the state of this repository at the time of thesis completion. Because
this repository remains publicly editable after submission, this printed record
serves as the authoritative reference for what existed at the time of publication.
Any content added after commit 8435c9b is supplementary and not part of the
reported work.

| Field | Value |
|---|---|
| Repository | https://github.com/Zslw/mri-translational-force-n-torque-analysis |
| Branch | main |
| Thesis sync commit | 8435c9b |
| Commit message | Final thesis sync: updated notebooks, publication figures, and appendix calculations |
| Date of sync | April 23, 2026 |
| Scanner | Siemens Magnetom 3T at CHI Health CUMC-Bergan Mercy, Omaha NE |
| Device tested | Medtronic STREAMLINE 6492 unipolar temporary epicardial lead |
| Standards followed | ASTM F2052-15, ASTM F2213-17 |
| Primary result | Force ratio FR = 0.093 (alpha = 5.32 degrees) -- passes F2052-15 threshold (FR less than 1.0) |

All notebooks, raw data CSVs, and publication figures present at commit 8435c9b
represent the complete computational record of the experimental work reported in
the thesis. No analysis code changes are anticipated after this point. Any future
commits will be documentation or formatting only.

---

## Citing This Work

Juarez Luna, D. (2026). Magnetically Induced Forces on Temporary Epicardial Leads:
Experimental Device Development and Clinical Testing. MSc Medical Physics,
Creighton University.  
Code and data: https://github.com/Zslw/mri-translational-force-n-torque-analysis
