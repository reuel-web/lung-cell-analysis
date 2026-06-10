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
- **HEXIM1** is the strongest survival-associated gene (p < 0.0001) — 
  high expression predicts significantly better outcomes, consistent 
  with its role as a transcriptional brake on cancer growth programs
- **CHEK1** and **RAD54L** (DNA repair genes) associate with worse 
  survival when highly expressed — tumours that upregulate DNA repair 
  survive treatment more effectively
- **AGER** (p = 0.024) — normal lung identity marker — retaining 
  expression associates with better prognosis
- Genome-wide scan identified 20 genes with p < 0.002, predominantly 
  tissue identity markers (high = better) vs DNA repair genes (high = worse)


## Figures

| Figure | Description |
|--------|-------------|
| `figures/01_pca.png` | PCA of all 164 samples coloured by condition |
| `figures/02_heatmap.png` | Top 50 most variable genes across samples |
| `figures/03_volcano.png` | Differential expression: fold change vs significance |
| `figures/04_pathways_cancer.png` | ORA — pathways enriched in NSCLC |
| `figures/05_pathways_normal.png` | ORA — pathways silenced in cancer |
| `figures/06_gsea_summary.png`    | GSEA summary — NES scores across Hallmark pathways |
| `figures/07_km_curves.png` | KM curves for 6 key cancer genes |
| `figures/08_km_top_genes.png` | KM curves for top genome-wide scan hits |
| `figures/09_survival_scan.png` | Summary of top 20 survival-associated genes |

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
Open notebooks/02_analysis.ipynb and run all cells (so on...)

## Project structure


## Tools used

- Python 3.11, pandas, numpy, matplotlib, seaborn
- scikit-learn (PCA), scipy (t-test), GEOparse
- scanpy (single-cell analysis toolkit)