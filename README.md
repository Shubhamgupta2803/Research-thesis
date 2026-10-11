# Research-thesis
Addressed clonotyping and sample demultiplexing for single-cell data from neonatal sepsis PBMC samples from 10 donors, sequenced on the 10x Genomics Chromium X, with a focus on B-cell receptor.
# Overview: Donor Demultiplexing and TCR Clonotype Analysis

## Project Overview

This workflow integrates donor identification, T-cell receptor (TCR) clonotype reconstruction, and clonal distribution analysis in single-cell sequencing data. The three scripts address complementary aspects of the analysis.

### Script 1: Donor Demultiplexing Using HTO and SNP Information

**Purpose:** Identify the donor of origin for each cell by integrating hashtag oligonucleotide (HTO)-based and single-nucleotide polymorphism (SNP)-based donor assignments.

This script reconciles donor labels from the two approaches, evaluates assignment consistency, and identifies potential doublets or cells with ambiguous donor assignments. It generates intermediate tables containing donor assignments and related metadata.

**Main outputs:** `step1.csv`, `step_2.csv`, and `rest.csv`.

### Script 2: TCR Clonotype Reconstruction and Matching

**Purpose:** Reconstruct TCR clonotypes from V(D)J sequencing annotations by combining information from T-cell receptor alpha (TRA) and beta (TRB) chains.

This script generates clonotype identifiers, calculates their frequencies, identifies cells with duplicate or multiple receptor-chain assignments, and attempts to match related clonotypes using graph-based relationships. It also generates intermediate and filtered tables for further clonotype matching.

**Main outputs:** `clonotype.csv`, `clonotype_results.csv`, `duplicated_barcodes.csv`, `triplets.csv`, `Quadruplets.csv`, `matching_cells.csv`, `matching_cells_4x.csv`, and `final.csv`, alongside additional intermediate files.

### Script 3: Clonotype Distribution and Clonal Expansion Analysis

**Purpose:** Characterize the frequency and distribution of TCR clonotypes across donors and cell populations using clonotype annotations and a Seurat single-cell object.

This script integrates clonotype information into the cell metadata, classifies clonotypes according to their observed frequencies, and examines their distribution across donors and clusters. It also generates visualizations to explore donor-level clonotype patterns and clonotype sharing.

**Main outputs:** `upset_donor.png`, `donor_clonotype.png`, and the in-memory object `C2_PLOTbcell`.

## How the Three Scripts Fit Together

1. **Script 1 — Donor assignment:** Establishes donor identities and identifies potentially ambiguous or doublet cells.
2. **Script 2 — Clonotype reconstruction:** Uses V(D)J annotations to identify TCR clonotypes and investigate receptor-chain combinations.
3. **Script 3 — Clonotype distribution:** Examines clonotype frequencies and their distribution across donors and cell populations.

Together, the scripts provide a framework for linking donor identity with TCR clonotype composition and clonal expansion in single-cell data.

**Important:** This describes the intended analytical roles of the scripts. They should not be assumed to form a fully automated pipeline without confirming that their input files, cell barcodes, donor labels, and clonotype identifiers are compatible. The clonotype frequency calculations and receptor-chain matching also require validation before interpreting biological results.
