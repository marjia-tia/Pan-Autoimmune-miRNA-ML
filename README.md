# Pan-Autoimmune miRNA-mRNA Dysregulation Network Analysis and ML-Based Classification

## Overview
A computational framework identifying shared miRNA-mRNA regulatory patterns across four autoimmune diseases — Vitiligo, SLE, Rheumatoid Arthritis, and Type 1 Diabetes — with machine learning-based disease classification and RNAi therapeutic implications.

## Key Findings
- 289 shared pan-autoimmune miRNA regulators identified across Vitiligo, SLE, and RA
- hsa-miR-124-3p identified as top hub miRNA (69 target genes)
- hsa-miR-181a-5p identified as RNAi therapeutic candidate targeting PTPN22
- 98.8% disease classification accuracy using Random Forest
- PTPN22 and NLRP1 validated as pan-autoimmune anchor genes via GWAS

## Pipeline
| Step | Notebook | Description |
|------|----------|-------------|
| 1 | 01_data_collection | GEO data download and processing |
| 2 | 02_differential_expression | DEG analysis (t-test + BH correction) |
| 3 | 03_miRNA_network | miRNA-mRNA network construction |
| 4 | 04_feature_engineering | ML feature preparation |
| 5 | 05_ML_classification | Random Forest, XGBoost, SVM |
| 6 | 06_SHAP | Interpretability analysis |
| 7 | 07_RNAi_therapeutic | Therapeutic target identification |
| 8 | 08_GWAS_validation | GWAS cross-validation |

## Datasets
All datasets from NCBI GEO, Affymetrix GPL570 platform:
- GSE65127 — Vitiligo
- GSE318067 — SLE
- GSE93272 — Rheumatoid Arthritis
- GSE55098 — Type 1 Diabetes

## Data Requirements
Download hsa_MTI.csv from miRTarBase v10.0 (https://mirtarbase.cuhk.edu.cn) and place in data/raw/

## Installation
```bash
python3 -m venv mirna_env
source mirna_env/bin/activate
pip install -r requirements.txt
```

## References
- miRTarBase 2025: Nucleic Acids Research, 2025
- Thomas & Veerabathiran (2025): Immunologic Research
- GWAS Catalog: https://www.ebi.ac.uk/gwas

## Author
Marjia Islam Tia
