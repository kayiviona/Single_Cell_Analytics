# Single Cell and Spatial Analytics

MSc Cancer Genomics and Data Science
Queen Mary University of London, 2025–2026

This repository contains two long answer assignments from the 
Single Cell and Spatial Analytics module, plus short answer 
questions on spatial transcriptomics and cell-cell communication. 
Both LAQs use real patient or published datasets and include full 
biological interpretation of results.

---

## Assignment Q1 — scRNA-seq Analysis of Cutaneous Squamous 
Cell Carcinoma

**File:** `Ka Yi Chan CAN7034 Single Cell Analytics 
Assignment Q1.ipynb`

**Dataset:** 10 single-cell RNA-seq samples from 4 patients 
(P2–P5) — 4 cutaneous squamous cell carcinoma (cSCC) tumour 
samples and 4 matched normal skin samples (31,456 cells total)

**Pipeline:**
- Quality control, filtering and normalisation
- Highly variable gene selection and PCA
- Harmony batch correction integrating 10 samples across 
  4 patients while preserving tumour vs normal biological signal
- UMAP visualisation before and after integration confirming 
  patient mixing without loss of tumour/normal separation
- Leiden clustering tested across resolutions 0.2 to 0.9

**Key analytical decision — clustering resolution:**  
Resolution 0.2 produced 16 clusters and resolution 0.4 produced 
18 clusters, both insufficient to resolve biologically distinct 
populations. Tumour keratinocytes and normal keratinocytes share 
overlapping transcriptional profiles but are functionally and 
clinically distinct; lower resolutions merged them into a single 
cluster. Resolution 0.5 (19 clusters) was selected as it 
separated these populations while avoiding the artificial 
oversplitting seen at resolutions 0.6–0.9 (22–26 clusters). 
This decision was driven by prior knowledge of the expected 
cell type composition of cSCC-inflamed skin tissue.

**Cell type annotation:**  
Clusters annotated to skin cell populations including 
keratinocytes (tumour and normal), fibroblasts, endothelial 
cells, and immune cells (T cells, B cells, myeloid cells). 
Tumour microenvironment immune cell composition compared 
between cSCC and matched normal tissue.

**Tools:** Python, Scanpy, Harmony, matplotlib, seaborn

---

## Assignment Q2 — Haematopoiesis Trajectory Analysis

**File:** `Ka Yi Chan CAN7034 Single Cell Analytics 
Assignment Q2.ipynb`

**Dataset:** 61,122 murine bone marrow cells from 8 samples 
(GSM2877127–GSM2877134; Dahlin et al., Blood, 2018), 
representing haematopoietic stem cell differentiation into 
erythroid, myeloid and lymphoid lineages

**Pipeline:**
- Data concatenation and normalisation (normalize_total, 
  log1p transformation)
- Highly variable gene selection (1,336 HVGs retained), 
  scaling and PCA (20 principal components)
- Neighbourhood graph and UMAP computation
- Leiden clustering tested at resolutions 0.2 (11 clusters), 
  0.4 (13 clusters), 0.6 (18 clusters) and 0.8 (22 clusters)
- Wilcoxon rank sum differential expression per cluster
- Cell type annotation using established haematopoietic 
  marker genes
- Diffusion map and DPT pseudotime trajectory analysis

**Key analytical decision — clustering resolution:**  
Resolution 0.4 (13 clusters) was selected based on biological 
reasoning: haematopoiesis produces approximately 9 known cell 
types, so 13 clusters provides enough granularity to capture 
subtypes and maturation stages without oversplitting. Multiple 
clusters representing the same lineage at different maturation 
stages is biologically expected given that haematopoiesis is 
a continuous process.

**Cell type annotation:**  
Clusters annotated using marker genes including Procr (HSCs), 
Gata1/Klf1/Hba-a2 (Erythroids), Elane/Mpo (Neutrophils), 
Irf8/Csf1r (Monocytes), Itga2b/Pbx1 (Megakaryocytes), 
Ms4a2/Cpa3 (Mast cells and Basophils). 13 clusters resolved 
to 6–7 broad cell types, consistent with haematopoietic 
biology.

**Trajectory analysis:**  
Cluster 0 was identified as the HSC root population based on 
Procr expression, consistent with the known rarity of 
long-term HSCs in the bone marrow niche. Diffusion map 
analysis (DC2/DC3) placed HSCs at the undifferentiated root. 
Three lineages were identified: Neutrophil/Monocyte (clusters 
3 and 7), and two Erythroid branches (clusters 5/6 and 
cluster 4). DPT pseudotime assigned each cell a value from 0 
(root HSCs) to 1 (most differentiated terminal state).

**Limitations discussed:**  
Pseudotime is a single-timepoint snapshot and may miss 
short-lived intermediate states; manual root selection 
introduces analyst dependency; diffusion maps are sensitive 
to cell density imbalances across lineages; limited sample 
size reduces statistical power.

**Tools:** Python, Scanpy, matplotlib, pandas, numpy

---

## Technologies Used

- **Language:** Python
- **Key libraries:** Scanpy, AnnData, Harmony, 
  matplotlib, seaborn, pandas, numpy
- **Infrastructure:** QMUL Apocrita HPC cluster
