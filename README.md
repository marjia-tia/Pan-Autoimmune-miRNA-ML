# Pan-Autoimmune miRNA-mRNA Dysregulation Network Analysis and ML-Based Classification of Immune Gene Signatures

A computational framework identifying shared microRNA-mRNA regulatory architecture across four autoimmune diseases named Vitiligo, Systemic Lupus Erythematosus (SLE), Rheumatoid Arthritis (RA), and Type 1 Diabetes (T1D), integrating differential expression analysis, network biology, machine learning classification, SHAP interpretability, and RNAi therapeutic target identification, with cross-validation against GWAS-confirmed risk loci.

**Manuscript:** preprint archived via Zenodo (DOI: 10.5281/zenodo.21498964)
**Author:** Marjia Islam Tia — Asian University for Women, Bangladesh
**Contact:** marjia.tiaaa@gmail.com

---

## Key Findings

| Finding | Result |
|---|---|
| Pan-autoimmune shared miRNA regulators | 289 miRNAs shared across Vitiligo, SLE, and RA networks |
| Top hub miRNA | hsa-miR-124-3p (69 target genes) |
| RNAi therapeutic candidate | hsa-miR-181a-5p → PTPN22 (validated Functional MTI) |
| Disease classification accuracy | 98.8% (Random Forest, held-out test set) |
| GWAS validation — PTPN22 | Confirmed across all 4 diseases |
| GWAS validation — NLRP1 | Confirmed in Vitiligo and T1D |
| Novel SHAP biomarker candidates | IRF6, S100A16 (RA); SERPINB5 (Vitiligo) |

---

## Pipeline

| Step | Notebook | Description |
|---|---|---|
| 1 | `01_data_collection.ipynb` | GEO dataset retrieval, probe-to-gene mapping, preprocessing |
| 2 | `02_differential_expression.ipynb` | DEG analysis (t-test + Benjamini-Hochberg correction) |
| 3 | `03_miRNA_network.ipynb` | miRNA-mRNA network construction (miRTarBase, NetworkX) |
| 4 | `04_feature_engineering.ipynb` | Feature matrix construction for ML |
| 5 | `05_ML_classification.ipynb` | Random Forest, XGBoost, SVM classification |
| 6 | `06_SHAP.ipynb` | SHAP interpretability analysis |
| 7 | `07_RNAi_therapeutic.ipynb` | RNAi therapeutic target identification |
| 8 | `08_GWAS_validation.ipynb` | Cross-validation against GWAS Catalog |

---

## Datasets

All expression data profiled on Affymetrix HG-U133 Plus 2.0 (GPL570) via NCBI GEO, ensuring platform consistency for cross-disease comparison:

| Disease | GEO Accession | Cases / Controls |
|---|---|---|
| Vitiligo | [GSE65127](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE65127) | 30 / 10 |
| SLE | [GSE318067](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE318067) | 41 / 41 |
| Rheumatoid Arthritis | [GSE93272](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE93272) | 232 / 43 |
| Type 1 Diabetes | [GSE55098](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE55098) | 12 / 10 |

miRNA-mRNA interactions: [miRTarBase](https://mirtarbase.cuhk.edu.cn) (Functional MTI only). Download `hsa_MTI.csv` and place in `data/raw/`.

---

## Installation

```bash
git clone https://github.com/marjia-tia/Pan-Autoimmune-miRNA-ML.git
cd Pan-Autoimmune-miRNA-ML
python3 -m venv mirna_env
source mirna_env/bin/activate
pip install -r requirements.txt
```

Run notebooks sequentially (01 → 08). Raw and processed data are excluded via `.gitignore` and regenerate automatically on execution.

---

## Repository Structure

```
Pan-Autoimmune-miRNA-ML/
├── notebooks/ 8-step analysis pipeline
├── scripts/ reusable utility functions
├── results/figures/ publication-ready figures
├── requirements.txt
└── README.md
```

---

## Limitations

T1D analysis was underpowered (n=22) and yielded no significant DEGs under strict correction; it was accordingly excluded from network construction. Classification accuracy reflects both disease-specific biology and cohort-level technical variation across independent studies. Full discussion in the accompanying manuscript.

---

## Citation

If referencing this work, please cite:

> Tia, M. I. (2025). *Shared miRNA-mRNA Regulatory Architecture Across Autoimmune Diseases: A Computational Framework Integrating Network Analysis, Machine Learning Classification, and RNAi Therapeutic Target Identification.* Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX

---

## References

- Huang, H.Y., et al. miRTarBase update: experimentally validated microRNA-target interactions. *Nucleic Acids Research.*
- Thomas, G. & Veerabathiran, R. (2025). PTPN22 polymorphism and autoimmune disease susceptibility: a meta-analysis. *Immunologic Research.*
- Sollis, E., et al. (2023). The NHGRI-EBI GWAS Catalog: knowledgebase and deposition resource. *Nucleic Acids Research*, 51(D1), D977–D985.

---

## License

Copyright (c) 2025 Marjia Islam Tia. All Rights Reserved. See `LICENSE` for full terms.
