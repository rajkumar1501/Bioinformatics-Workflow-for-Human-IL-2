# Bioinformatics Workflow: Human IL-2 Expression Strategy

[![Project Status](https://img.shields.io/badge/Status-Complete-success)]()
[![Language](https://img.shields.io/badge/Python-3.9%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green)]()

**Live Report:** [View the Project on GitHub Pages](https://rajkumar1501.github.io/Bioinformatics-Workflow-for-Human-IL-2/)

## 🧬 Project Overview
This repository contains a comprehensive bioinformatics workflow designed to engineer **Human Interleukin-2 (IL-2)** for high-yield expression in the **Baculovirus Expression Vector System (BEVS)** using *Spodoptera frugiperda* (Sf9) insect cells. 

The workflow automates sequence verification, codon optimization, physicochemical profiling, and structural rational design to address solubility and aggregation issues.

## 🎯 Objectives
1.  **Expression Strategy:** Design a shuttle vector construct for secretion in silkworms/Sf9 cells.
2.  **Sequence Engineering:** Optimize codons for *S. frugiperda* and remove the native human signal peptide.
3.  **Rational Design:** Identify aggregation-prone regions and propose specific point mutations to improve solubility.
4.  **Structural Analysis:** Model the protein (using Boltz/AlphaFold) to map hydrophobic hotspots.

## 🚀 Workflow Steps

The Jupyter Notebook (`.ipynb`) in this repository covers the following modules:

### 1. Sequence Verification
-   **Input:** Raw FASTA sequence of Target-X (Human IL-2 Precursor).
-   **Validation:** Automated BLAST search against the NCBI database to confirm identity (NP_000577.2).

### 2. Codon Optimization & Vector Construction
-   **Tool:** `DNA Chisel`
-   **Host:** *Spodoptera frugiperda* (TaxID: 7108).
-   **Construct Design:**
    -   **Signal Peptide:** Replaced native signal with **Honeybee Melittin (HBM)** for efficient insect secretion.
    -   **Tags:** Added C-terminal **6xHis tag** for purification.
    -   **Constraints:** Enforced GC content (30-70%) and removed internal BamHI/XhoI sites.

### 3. Computational Analysis
-   **Physicochemical Profiling:** Calculated MW (15.65 kDa), pI (7.92), GRAVY (-0.17), and Instability Index.
-   **Aggregation Scan:** Sliding window analysis (Kyte-Doolittle) identified a hydrophobic cluster at residues 90-92.

### 4. Structural Modeling & Rational Design
-   **Modeling:** 3D structure prediction using **Boltz** (pLDDT > 85%).
-   **Surface Scan:** Mapped surface hydrophobicity using SASA (Solvent Accessible Surface Area).
-   **Mutation Selection:** Targeted **Valine 92 (V92)**, a surface-exposed hydrophobic residue.
    -   **Action:** Mutated to **Asparagine (V92N)** based on evolutionary consensus (39.1% frequency in homologs).

## 📊 Key Results

| Feature | Details |
| :--- | :--- |
| **Final Construct** | `[BamHI] - [Kozak] - [HBM Signal] - [Mature IL-2 (V92N)] - [Linker] - [6xHis] - [XhoI]` |
| **Mutation** | **V92N** (Solubility enhancement) |
| **Purification** | IMAC (Ni-NTA) followed by Cation Exchange (pH 6.5) |
| **GC Content** | Optimized to 56.4% |

## 🛠️ Tools & Libraries Used
* **Biopython:** Sequence parsing, BLAST, ProtParam, PDB analysis.
* **DNA Chisel:** Genetic algorithm for codon optimization.
* **Boltz / AlphaFold:** 3D protein structure prediction.
* **py3Dmol:** Interactive 3D visualization within the notebook.
* **Matplotlib:** Plotting hydrophobicity profiles and confidence scores.
