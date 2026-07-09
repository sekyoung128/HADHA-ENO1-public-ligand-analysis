# HADHA–ENO1 Public Ligand Analysis

This repository contains an exploratory cheminformatics project developed as a follow-up to earlier dissertation work on HADHA and ENO1 in hepatocellular carcinoma.

The project began from a structure-based interpretation in which HADHA appeared more compatible than ENO1 with lipophilic madecassic-acid-like scaffolds. It follows up that question using public ChEMBL-derived ligand bioactivity data, RDKit descriptor analysis, and simple fingerprint-based modelling.

## Project question

Do public ligand bioactivity data support a meaningful difference between HADHA and ENO1, and can baseline ligand-based machine-learning methods recover predictive signal for these targets?

## Why these targets?

- **HADHA** and **ENO1** were chosen because they were directly relevant to the earlier structure-based comparison.
- **ABL1** was included as a positive-control target with a substantially larger public ligand dataset, allowing the same workflow to be observed under less data-constrained conditions.

## Repository contents

- `notebooks/HADHA-ENO1-public-ligand-analysis.ipynb` — final analysis notebook
- `data/` — public bioactivity datasets used in the notebook
- `README.md` — project overview

## Workflow

- Curated public bioactivity data from ChEMBL
- Filtered and standardised ligand records
- Calculated molecular descriptors and fingerprints using RDKit
- Compared ligand property profiles across targets
- Built baseline machine-learning models for bioactivity prediction
- Used ABL1 as a positive-control target for benchmarking

## Key Findings
- Public ligand data for HADHA were extremely limited
- ENO1 showed weak or near-random predictive performance in the current ligand-only setting
- ABL1 provided a clearer positive-control example with recoverable signal
- Sparse public data constrained strong conclusions for under-characterised metabolic targets

## Main interpretation

This project is exploratory rather than confirmatory. The available HADHA ligand dataset remained too small for strong statistical or predictive conclusions, but the descriptor comparison was broadly consistent with the earlier structure-based idea that HADHA may be more compatible than ENO1 for lipophilic madecassic-acid-like scaffolds.

A central aim of the project was to extend a biological question from dissertation work through public-data analysis in Python, while being explicit about what the data could and could not support.

## Running locally

To run the notebook locally, Python, Jupyter Notebook, and the required packages such as pandas, numpy, matplotlib, seaborn, scikit-learn, and RDKit are needed.
