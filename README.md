# Single-Cell RNA-seq Analysis of Healthy Human Lung

This project performs a full scRNA-seq analysis pipeline on healthy lung tissue samples using **Seurat** in R. The dataset is sourced from [GSE132771](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE132771) and includes three normal lung samples (NML1, NML2, NML3).

## Pipeline Overview

1. **Data Loading** — Load 10X Genomics data for three normal lung samples and create Seurat objects
2. **Merging** — Merge all three samples into a single Seurat object
3. **Quality Control** — Filter low-quality cells based on:
   - Number of detected features (500–4000)
   - Total RNA count (< 20,000)
   - Mitochondrial gene percentage (< 10%)
4. **Normalization** — Log-normalization with a scale factor of 10,000
5. **Feature Selection** — Identify 2,000 highly variable genes using VST
6. **Scaling** — Scale expression across all genes
7. **Dimensionality Reduction** — PCA followed by UMAP (first 20 PCs)
8. **Clustering** — Graph-based clustering (Louvain, resolution = 0.3)
9. **Marker Gene Identification** — Differential expression analysis to find top markers per cluster
10. **Cell Type Annotation** — Manual annotation of 18 cell types

## Identified Cell Types

| Cluster | Cell Type |
|---------|-----------|
| 0 | Monocytes |
| 1 | Alveolar Macrophages |
| 2 | Alveolar Epithelial |
| 3 | Vascular Endothelial |
| 4 | Alveolar Type 2 |
| 5 | Fibroblasts |
| 6 | Dendritic Cells |
| 7 | T Cells |
| 8 | NK Cells |
| 9 | Smooth Muscle |
| 10 | Mesothelial |
| 11 | Macrophages |
| 12 | Rare Epithelial |
| 13 | B Cells |
| 14 | Mast Cells |
| 15 | Proliferating |
| 16 | Stromal |
| 17 | Ciliated/Lymphatic |

## Key Marker Genes

| Cell Type | Markers |
|-----------|---------|
| Alveolar Epithelial | SFTPA2 |
| T Cells | CD3D |
| Monocytes | S100A8 |
| Vascular Endothelial | ACKR1 |
| NK Cells | KLRF1 |
| Fibroblasts | LUM |
| Alveolar Macrophages | APOE |
| Smooth Muscle | ACTG2 |

## Requirements

- R (>= 4.0)
- [Seurat](https://satijalab.org/seurat/)
- tidyverse

## Files

- `ScRNA_Analysis.Rmd` — Main analysis notebook
- `ScRNA_Analysis.nb.html` — Rendered HTML output with all plots and results
