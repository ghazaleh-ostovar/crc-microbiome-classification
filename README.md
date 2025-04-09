# Colorectal Cancer Classification Using Microbiome OTU Data

## Overview  
This project aims to classify **colorectal cancer (CRC)** using **gut microbiome profiles**.  
Using OTU (Operational Taxonomic Unit) abundance data from a publicly available dataset, I applied feature selection and machine learning to distinguish CRC from healthy samples with high accuracy.

**Dataset:** Baxter et al., 2016, *Genome Medicine*  
🔗 [Available here](https://genomemedicine.biomedcentral.com/articles/10.1186/s13073-016-0290-3)

### Sample Breakdown:
- **Healthy:** 172  
- **Colorectal Cancer (CRC):** 120  
- **nonCRC (e.g., adenomas):** 198  
- **Features:** ~9,000 OTUs representing microbial abundances per sample

---

##  Preprocessing

1. **Abundance Filtering** – Removed low-abundance OTUs to reduce noise  
2. **Normalization** – Scaled each sample to account for differences in sequencing depth  
3. **Variance Thresholding** – Removed features with low variability across samples  
4. **Dimensionality Estimation** – Used PCA and domain knowledge to estimate the number of informative features

- Reduced features from ~9,000 to **385**

---

##  Feature Selection & Modeling

- Compared **LASSO** and **Random Forest** for selecting predictive OTUs  
- Final selection reduced the feature set to **<100** OTUs for better interpretability  
- Trained and evaluated **SVM**, **Random Forest**, and **XGBoost** classifiers  
- Performed **GridSearchCV** with 5-fold cross-validation  
- Evaluation metrics: **ROC-AUC**, **accuracy**, **precision**, **recall**

---

##  Results (CRC vs Healthy, LASSO-selected Features)

| **Model**              | **Accuracy** | **AUC-ROC** | **Precision (Cancer)** | **Recall (Cancer)** |
|------------------------|--------------|-------------|-------------------------|----------------------|
| **SVM (LASSO) ✅**      | **87.9%**    | **0.877**   | **95%**                 | **75%**              |
| XGBoost (LASSO)        | 84.5%        | 0.842       | 83%                     | 79%                  |
| Random Forest (LASSO)  | 82.8%        | 0.825       | 85%                     | 71%                  |

---

##  Key Insights  
- **LASSO**-selected features improved model generalization and interpretability  
- **SVM** with an RBF kernel achieved the best overall performance  
- CRC and healthy samples are distinguishable via microbiome profiles  
- Classifying nonCRC vs healthy remains more difficult due to biological similarity  

---

##  Setup & Requirements

Clone the repository and install dependencies with:

```bash
pip install -r requirements.txt
