# Colorectal Cancer Classification Using Microbiome OTU Data

##  Overview  
This project aims to classify **colorectal cancer (CRC)** using **gut microbiome profiles**.  
Using OTU (Operational Taxonomic Unit) abundance data from a publicly available dataset, I apply feature reduction and machine learning to distinguish CRC from healthy samples with high accuracy.

**Dataset:** Baxter et al., 2016, *Genome Medicine*  
🔗 [Available here](https://genomemedicine.biomedcentral.com/articles/10.1186/s13073-016-0290-3)


### Sample Breakdown:
- **Healthy:** 172  
- **Colorectal Cancer (CRC):** 120  
- **nonCRC (e.g., adenomas):** 198  
- **Features:** ~9,000 OTUs representing microbial abundances per sample

---

###  Methods

### **Preprocessing**
- Filtered low-abundance and low-variance OTUs  
- Normalized OTU abundances per sample  
- Reduced features from ~9,000 to **385**

### **Feature Selection**
- Compared **LASSO** and **Random Forest** for selecting predictive OTUs
-  Final selection reduced the feature set to **<100** OTUs for better interpretability and reduced overfitting

### **Modeling**
- Trained and evaluated **SVM**, **Random Forest**, and **XGBoost** classifiers  
- Performed **GridSearchCV** with 5-fold cross-validation  
- Evaluation metrics: **ROC-AUC**, **accuracy**, **precision**, **recall**

---

## 📊 Results (CRC vs Healthy)

| Model               | Accuracy | AUC-ROC | Precision (Cancer) | Recall (Cancer) |
|--------------------|----------|---------|---------------------|------------------|
| **SVM (LASSO)** ✅ | **86.2%** | **0.856** | **90%**             | **75%**          |
| Random Forest       | 82.8%    | 0.824   | 85%                 | 71%              |
| XGBoost             | 84.5%    | 0.842   | 83%                 | 79%              |

---

## 🔍 Key Insights  
- **LASSO**-selected features outperformed RF-selected ones  
- **SVM** (RBF kernel) achieved the best balance of precision and recall  
- CRC and healthy samples are separable, but **nonCRC vs healthy** is harder—likely due to microbiome similarity  

---

##  Setup & Requirements

Clone the repository and install dependencies using:

```bash
pip install -r requirements.txt
