# MRI Safety Thesis — Analysis Code & Data

**Author:** Daniel Juarez Luna
**Institution:** Creighton University, MSc Physics
**Advisor:** Michael G. Nichols, PhD.

## Overview

This repository contains the Jupyter notebooks, raw data, and generated figures
supporting my MSc thesis on MRI safety — specifically the characterization of
translational force and torque exerted by a 3T MRI scanner on implantable or
nearby objects, as a function of magnetic field gradient and field strength.

---

## Repository Structure

### `JupyterLab/Translational/` 
Contains the translational force experiment:
raw angle measurements, cleaned datasets, and the main analysis notebook.
- **`FitSus.ipynb`** — Main analysis: susceptibility fitting, tan(α) vs dB₀/dz,
  uncertainty propagation via standard error formulas. Referenced in the
  methodology section of the thesis.
- **`AppendixB.ipynb`** — Appendix material and supplementary analysis.
- `cleanData.csv`, `RawMeasurments.csv`, etc. — Processed and raw experimental data.
- `Assests/` — Final publication-quality figures.

### `JupyterLab/Torque/`
Custom torque sensor development and MRI torque measurements.
- **`Calibration/`** — Sensor calibration notebooks and data. The sensor was
  custom-built from different materials as a strain detector; calibration involved
  applying known weights to convert voltage readings to force (mg). Multiple rods
  and trial sets included.
  - Key notebooks: `Torque-plots.ipynb`, `Upright-Torque-plots.ipynb`, `data_compiler.ipynb`
- **`MRIForces/`** — Actual torque experiments in the lab.
  - **`Torque Presentation.ipynb`** — Helmholtz coil trials (controlled B field).
  - **`Torque_again.ipynb`** — Neodymium magnet trials with increasing B field.
  - Note: angle-dependent measurements were ultimately inconclusive due to
    precision limitations; the B-field magnitude experiments are the reported results.

### `JupyterLab/ClinicalData/`
Real magnetic flux density measurements taken inside and around the 3T MRI scanner
using a gaussmeter mounted on a custom radial fixture. Grid labels (e.g. G3, G6,
A3, D3) refer to fixture coordinates.
- **`Map_translational.ipynb`** — Main data manipulation and field mapping notebook.
- **`GaussmeterReps.ipynb`** — Analysis of repeated field measurements; work in
  progress being continued by junior students.
- `DataCollectionFolderMRIProject/` — Raw CSV files per grid position and trial.

### `JupyterLab/BfieldSIM/`
Numerical simulation of the static magnetic field of a solenoid, used to generate
the background field plot in Section 2.1.1 of the thesis. Not experimental data —
purely a theoretical illustration.

### `JupyterLab/FindSampleRateMagFieldMap.ipynb`
Exploratory notebook testing the gaussmeter's data acquisition rate under low
magnetic flux conditions. Result: 0.25 s sampling interval was selected for that
run, though subsequent analysis (see ClinicalData) suggested 0.5 s would have
been more appropriate.

### `JupyterLab/Poster1/`
Early notebook used to reproduce figures from a prior student's thesis on RF
heating, created while learning Python/Jupyter at the start of the project.
Included for completeness.

---

## Dependencies

Core libraries used across notebooks:
```
pandas, numpy, scipy, matplotlib
```

To install:
```bash
pip install pandas numpy scipy matplotlib
```

---

## Repository Structure

mri-translational-force-n-torque-analysis/
├── README.md
├── MapField/                          # Raw gaussmeter acquisition runs (.dat, .csv)
│   ├── FindSampleRate.csv
│   ├── FindSampleRate_run1-4.dat
│   ├── FindSampleRate2.csv
│   ├── FindSampleRate2_run1-5.dat
│   ├── FindSampleRate3.csv
│   └── FindSampleRate3_run1-2.dat
└── JupyterLab/
    ├── FindSampleRateMagFieldMap.ipynb  # Gaussmeter sampling rate test
    ├── Translational/                   ⭐ PRIMARY ANALYSIS
    │   ├── FitSus.ipynb                 # Main: susceptibility fit, tan(α) vs dB₀/dz
    │   ├── AppendixB.ipynb              # Supplementary analysis
    │   ├── RawMeasurments.csv           # Raw angle measurements
    │   ├── RawMeasurmentsMagneticfield.csv
    │   ├── RawMeasurmentsMagneticfieldGrad.csv
    │   ├── cleanData.csv                # Cleaned dataset
    │   ├── cleanDatawstdsem.csv         # With std and SEM
    │   ├── FitSus.html                  # Exported notebook
    │   ├── FitSus_files/                # Inline figures from notebook export
    │   ├── Assests/                     # Publication figures
    │   └── Mini Project exploration/    # Early vector potential exploration
    ├── Torque/
    │   ├── Calibration/                 # Custom strain sensor calibration
    │   │   ├── Torque-plots.ipynb
    │   │   ├── Torque-plots-Copy1.ipynb
    │   │   ├── Upright-Torque-plots.ipynb
    │   │   ├── Upright-Torque-plots-Copy1.ipynb
    │   │   ├── Upright-Torque-plots-Copy2.ipynb
    │   │   ├── data_compiler.ipynb
    │   │   ├── dataTorque/              # First calibration dataset
    │   │   ├── dataTorque.zip
    │   │   ├── New_dataTorque/          # Updated calibration dataset
    │   │   ├── New_dataTorque.zip
    │   │   └── plots/                   # Calibration fit figures
    │   └── MRIForces/                   # Actual torque experiments
    │       ├── Torque Presentation.ipynb  # Helmholtz coil trials
    │       ├── Torque_again.ipynb         # Neodymium magnet + increasing B field
    │       ├── Helmholtz-Torque-*.csv
    │       ├── TorqueMeasurement_SR_*.csv
    │       └── torqueangles_*.csv
    ├── ClinicalData/                    # 3T MRI scanner measurements
    │   ├── Map_translational.ipynb      # Main field mapping analysis
    │   ├── GaussmeterReps.ipynb         # Repeatability study (WIP)
    │   ├── DataCollectionFolderMRIProject/  # Raw CSVs per fixture position
    │   ├── DataCollectionFolderMRIProject.7z
    │   └── plots/                       # Per-position flux plots
    ├── BfieldSIM/                       # Solenoid B-field simulation (Section 2.1.1)
    │   ├── Bfield.ipynb
    │   ├── BfieldMapping.ipynb
    │   ├── FieldMapping.ipynb
    │   └── BfieldMapData/               # Gaussmeter mapping data
    └── Poster1/
        └── Brights Thesis/
            └── RescaleFigures.ipynb     # Figure reproduction from prior RF thesis
            
---

## Citing This Work

> Juarez Luna, D. (2025). *Magnetically Induced Forces on Epicardial Leads:
> Experimental Device Development and Clinical Testing — Analysis Code & Data*.
> MSc Physics, Creighton University.
> https://github.com/Zslw/mri-translational-force-n-torque-analysis
