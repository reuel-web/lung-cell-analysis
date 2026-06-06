# Lung Cell Gene Expression Analysis

Visualising the transcriptomic differences between healthy lung tissue 
and non-small cell lung cancer (NSCLC) using RNA-seq data.

## Biological question

Which genes are differentially expressed between normal alveolar lung 
cells and lung adenocarcinoma? What pathways are gained or lost in 
the transition to cancer?

## Dataset

- **Source:** NCBI GEO — GSE40419
- **Publication:** [Nature Genetics, 2012](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE40419)
- **Samples:** 87 NSCLC tumour + 77 adjacent normal lung tissue
- **Measurement:** RNA-seq, RPKM normalised

## Key findings

- **PCA** shows clear separation between cancer and normal samples 
  along PC1, confirming fundamentally different transcriptional programs
- **Heatmap** reveals surfactant genes (SFTPC, SFTPA1) retained in 
  adenocarcinoma; invasion markers (MMP1, S100P) upregulated; 
  normal lung identity markers (AGER, CLDN18) silenced
- **Volcano plot** identifies thousands of statistically significant 
  genes; CEACAM5 and IL6 strongly upregulated in cancer
- **Pathway enrichment** confirms E2F targets, G2M checkpoint, and MYC 
  programs are the dominant cancer signatures; TNF-Alpha/NF-κB and 
  complement pathways are silenced in tumour tissue

## Figures

| Figure | Description |
|--------|-------------|
| `figures/01_pca.png` | PCA of all 164 samples coloured by condition |
| `figures/02_heatmap.png` | Top 50 most variable genes across samples |
| `figures/03_volcano.png` | Differential expression: fold change vs significance |
| `figures/04_pathways_cancer.png` | ORA — pathways enriched in NSCLC |
| `figures/05_pathways_normal.png` | ORA — pathways silenced in cancer |
| `figures/06_gsea_summary.png`    | GSEA summary — NES scores across Hallmark pathways |

## How to reproduce

### 1. Clone this repository
git clone https://github.com/reuel-web/lung-cell-analysis.git
cd lung-cell-analysis

### 2. Create the conda environment
conda env create -f environment.yml
conda activate lungcell

### 3. Download the data
Follow the data download instructions in notebooks/01_load_data.ipynb

### 4. Run the analysis
Open notebooks/02_analysis.ipynb and run all cells

## Project structure

lungcell-analysis/
├── notebooks/
│   ├── 01_load_data.ipynb
│   └── 02_analysis.ipynb
├── figures/
│   ├── 01_pca.png
│   ├── 02_heatmap.png
│   └── 03_volcano.png
├── environment.yml
└── README.md

## Tools used

- Python 3.11, pandas, numpy, matplotlib, seaborn
- scikit-learn (PCA), scipy (t-test), GEOparse
- scanpy (single-cell analysis toolkit)