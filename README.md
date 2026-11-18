# BIOL 5340: Cancer RNA-seq Feature Selection Study

**Team:** Harsh Patel, Omkar Juvatkar, Pritesh Das  
**Research question:** Can a small subset of RNA-seq expression features distinguish five tumor types nearly as well as all 20,531 features, and how does feature selection method affect performance?

## Dataset

- Source: Fiorini (2016), UCI Machine Learning Repository, dataset 401: [https\://archive.ics.uci.edu/dataset/401/gene+expression+cancer+rna+seq](https://archive.ics.uci.edu/dataset/401/gene+expression+cancer+rna+seq)  
- DOI: [https\://doi.org/10.24432/C5R88H](https://doi.org/10.24432/C5R88H);  
- 801 samples, 20,531 numeric features, classes BRCA/KIRC/COAD/LUAD/PRAD.  
- Features are anonymized as `gene_0`, etc.; do not claim biological function without validated identifiers.  
- Download using notebook `01_Data_Preparation.ipynb`. **Do not commit the raw expression matrix** (\>200 MB uncompressed).

## Workspace

```
notebooks/
  01_Data_Preparation.ipynb
  02_Pilot_SVM.ipynb
  03_Comparative_Feature_Selection_and_Stability.ipynb
data/                 # generated data and split IDs; raw data excluded from Git
results/              # output tables
results/figures/      # plot images
report/               # draft and final report
README.md
AI_Usage.md
requirements.txt
.gitignore
```

Reproduce (Google Colab)

1. Open this folder in Google Drive, then each notebook in Colab.  
2. Run `01_Data_Preparation.ipynb`: download from UCI and save the fixed stratified split (`random_state=42`) to Drive.  
3. Run `02_Pilot_SVM.ipynb`: ANOVA \+ linear SVM with short feature grid, 3-fold stratified CV on **training only**.  
4. Save all figures and tables under `results/` and update draft status/report. Document package versions printed by notebooks.

## Methods and leakage control

- 20% stratified test holdout reserved at the start.  
- All supervised feature selection, scaling and training are fitted within CV folds.  
- Same CV splits are reused for paired method comparisons.  
- Primary metric: macro-F1; secondary metrics: balanced accuracy, per-class recall, runtime and feature selection stability (Jaccard).  
- Holdout test scores are not used to select the final configuration.  
- The complete full-feature model is the baseline; a reduced feature set is considered competitive if mean CV macro-F1 is within one percentage point of the baseline (a preregistered criterion, not a guaranteed result).

## Report and references

Use the instructor's provided `Project Report Template.docx`; draft: 3–5 pages, Arial 12 pt, single-spaced, **no abstract**. Include a GitHub repo URL, results/progress, group member role paragraphs, APA citations.

## License and citation

Fiorini, S. (2016). *gene expression cancer RNA-Seq* \[Data set\]. UCI Machine Learning Repository. [https\://doi.org/10.24432/C5R88H](https://doi.org/10.24432/C5R88H)

&nbsp;
