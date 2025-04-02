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

## 📊 Results (CRC vs. Healthy)

- **Best Model:** SVM (RBF Kernel)  
- **Selected Features:** 87 OTUs (via LASSO)  
- **Test Accuracy:** 86.2%  
- **AUC-ROC:** 0.856  
- **Precision (Cancer):** 90%  
- **Recall (Cancer):** 75%

---

##  Key Insights
- **LASSO-based feature selection** outperformed RF-selected features  
- **SVM** achieved the best balance between precision and recall for CRC classification  
- Classification between **nonCRC and Healthy** was weak, possibly due to microbiome similarity

