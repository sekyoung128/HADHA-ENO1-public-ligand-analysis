# Public ChEMBL Evidence Audit for a HADHA-ENO1-Madecassic Acid Hypothesis

This repository contains public-data audit of ChEMBL records associated with HADHA and ENO1.

The analysis evaluates whether publicly available ligand-associated records are numerous and chemically diverse to support target-specific ligand-based inference relevant to a madecassic-acid hypothesis.

This is a data-provenance and feasibility audit. It does not establish direct binding, enzyme inhibition, selectivity, cellular target engagement, or an anticancer mechanism for madecassic acid or related compounds.

## Background

HADHA and ENO1 were selected because of their biological relevance in the broader hepatocellular carcinoma context. Earlier structure-based work generated the hypothesis that HADHA may provide a more favourable binding environment than ENO1 for madecassic-acid-like compounds. This repository does not revisit receptor structures, biological assemblies, binding pockets, docking poses, docking scores, or binding free energies. Instead, it asks whether public ligand-associated records provide an independent and sufficiently robust basis for ligand-based modelling.

## Research question

> Are the public ChEMBL records associated with HADHA and ENO1 sufficiently defined and chemically diverse to justify target-specific ligand-based modelling?

## Workflow

The notebook performs the following steps:

1. Records input-file provenance, export date, and SHA-256 checksums.
2. Checks target identity using ChEMBL target identifiers.
3. Audits assay and measurement context, including assay type, endpoint, units, relation operators, and source documents.
4. Validates SMILES and standardises multi-component entries by retaining the largest organic parent fragment for descriptive structural analysis.
5. Preserves record-to-structure provenance before deduplicating structures.
6. Deduplicates structures using stereo-preserving canonical SMILES.
7. Calculates RDKit descriptors, Morgan fingerprints, Tanimoto similarity, and Murcko scaffolds.
8. Makes decision on whether the available data support target-specific ligand-based modelling.
9. Compares madecassic acid descriptively with the retained HADHA- and ENO1-associated structures using two-dimensional fingerprint similarity.

## Data provenance

The repository retains two raw ChEMBL bioactivity exports downloaded on **2026-06-23**.

| Target label | ChEMBL target ID | Target name | Raw ChEMBL records |
|---|---:|---|---:|
| HADHA | CHEMBL4295759 | Trifunctional enzyme subunit alpha, mitochondrial | 7 |
| ENO1 | CHEMBL3298 | Alpha-enolase | 39 |

The notebook calculates SHA-256 checksums for the input CSV files so that the exact analysed exports can be traced.

## Main findings

- The retained HADHA set contains only **4 unique structures**, which is insufficient for a meaningful train/test split or internal validation strategy.
- Therefore, this project does **not** train a HADHA-specific ligand-based model.
- The ENO1 set contains **18 unique structures**, but its records span heterogeneous endpoint types and experimental contexts, including IC50, Kd, ED50, fold-change, ratio, and generic activity entries.
- Because those records are not a single harmonised bioactivity dataset, this project does **not** train an ENO1 potency model, a binary activity classifier, or a model of HADHA-versus-ENO1 target preference.
- Madecassic acid is used solely as a predefined chemical reference for descriptive two-dimensional similarity analysis.
- The similarity comparison includes **all retained unique structures associated with HADHA or ENO1 in the selected ChEMBL exports**. It is **not restricted to compounds classified as active**, because no activity labels or cross-assay potency filters were created.
- The observed similarities are limited and do not demonstrate direct binding, a shared binding mode, potency, selectivity, target preference, or therapeutic relevance.

## Interpretation

The limited public HADHA dataset reflects restricted public data availability and assay coverage. It should **not** be interpreted as evidence that madecassic acid does not bind HADHA.

Although more structures are available for ENO1, assay-context heterogeneity prevents the direct comparison, ranking, or modelling of bioactivity values. Differences in molecular descriptors or two-dimensional similarity should not be interpreted as differences in affinity, potency, selectivity, ligandability, or biological relevance.

Rather than forcing a predictive model from unsuitable data, this audit identifies the limits of the available public evidence and defines the conditions needed for a more rigorous next stage.

## Suggested next steps

Any future structure-based or experimental study should pre-specify:
1. **Receptor state:** protein construct, biological assembly, cofactors, bound ligands, protonation states, and structural source.
2. **Controls:** positive controls with independently supported activity, chemically related lower-priority analogues, and procedural negative controls.
3. **Readouts:** appropriate direct biochemical or biophysical assays, concentration range, replication plan, acceptance criteria, and interpretation rules.
4. **Decision rule:** a structural hypothesis should be considered supported only if it is reproducible under pre-defined computational controls and agrees with an independent experimental method.

## Methods

RDKit was used to perform SMILES parsing, parent-fragment standardisation, descriptor calculation, Morgan fingerprint generation, Tanimoto similarity calculation, and Murcko scaffold extraction. Morgan fingerprints were generated with radius 2 and 2,048 bits. Tanimoto similarity is used only as a broad two-dimensional structural-resemblance measure.

## References

Full references for ChEMBL, RDKit, Morgan fingerprints, Murcko scaffolds, PubChem, and the biological background are listed in the final notebook.
