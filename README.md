Single Cell and Spatial Analytics

MSc Cancer Genomics and Data Science
Queen Mary University of London, 2025–2026

This repository contains three coursework assignments from the Single Cell and Spatial Analytics module. The module covers single-cell RNA-seq analysis, 
trajectory inference, spatial transcriptomics technologies, and cell-cell communication methods.

---

Assignment 1 — scRNA-seq Analysis of Cutaneous Squamous Cell Carcinoma

File: `Ka Yi Chan CAN7034 Single Cell Analytics Assignment Q1.ipynb`

Dataset: 10 single-cell RNA-seq samples from 4 patients (P2–P5) — 4 cutaneous squamous cell carcinoma (cSCC) tumour 
samples and 4 matched normal skin samples (31,456 cells total)

Methods:
- Quality control, filtering and normalisation
- Dimensionality reduction (PCA)
- Harmony batch correction for patient-level integration
- Leiden graph-based clustering with resolution comparison 
  (0.2 to 0.9)
- UMAP visualisation with and without integration
- Differential gene expression analysis
- Cell type annotation of skin cell populations including 
  keratinocytes, fibroblasts, endothelial cells and immune cells
- Tumour microenvironment analysis comparing normal vs cSCC 
  cell composition
- Immune cell population analysis (T cells, B cells, 
  myeloid cells)

Tools:Python, Scanpy, Harmony, matplotlib, seaborn

---

Assignment 2 — Haematopoiesis Trajectory Analysis

File: `Ka Yi Chan CAN7034 Single Cell Analytics Assignment Q2.ipynb`

Dataset: 61,122 murine bone marrow cells from 8 samples (Dahlin et al., Blood, 2018), representing haematopoietic 
stem cell differentiation into erythroid, myeloid and lymphoid lineages

Methods:
- Preprocessing and dimensionality reduction
- Leiden clustering and cell type annotation (HSCs, 
  erythroids, neutrophils, monocytes, megakaryocytes, 
  basophils, B cells, mast cells)
- Differential gene expression analysis per cluster
- Diffusion pseudotime (DPT) trajectory analysis using 
  haematopoietic stem cells as root
- UMAP visualisation coloured by cluster and cell type

Tools: Python, Scanpy, matplotlib
