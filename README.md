# Cancer Classification with RNA-Seq Data 🧬✨

![Cancer Research Banner](https://img.shields.io/badge/Project-Cancer%20Classification-brightgreen?style=for-the-badge)  
![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat-square&logo=python)  
![Status](https://img.shields.io/badge/Status-In%20Progress-orange?style=flat-square)

Welcome to my journey into computational biology and machine learning! This project uses bulk RNA-sequencing (RNA-seq) data from The Cancer Genome Atlas (TCGA) to classify three cancer types—**Breast Invasive Carcinoma (BRCA)**, **Lung Adenocarcinoma (LUAD)**, and **Prostate Adenocarcinoma (PRAD)**—with a simple yet powerful machine learning approach. As a recent medical graduate, I’m blending my clinical knowledge with data science to explore cancer at the molecular level. Let’s fight cancer with data together! 🚀

---

## 🌟 Project Overview

### **Goal**
Build a machine learning model to classify BRCA, LUAD, and PRAD based on gene expression profiles, laying the groundwork for personalized medicine insights.

### **Why This Matters**
- **Clinical Impact**: Molecular classification can enhance cancer diagnosis and treatment strategies.
- **Learning Journey**: My first machine learning project—stepping into a new field with enthusiasm!
- **Open Science**: Sharing my process to inspire collaboration and learning.

### **Dataset**
- **Source**: [TCGA Pan-Cancer Atlas](https://xenabrowser.net/datapages/?cohort=TCGA%20Pan-Cancer%20(PANCAN)) via UCSC Xena.
- **Data**: Batch effects normalized RNA-seq (11,060 samples, 20,531 genes).
- **Focus**: Filtered to BRCA, LUAD, PRAD (2,311 samples after preprocessing).

---

## 🛠️ Project Steps

### **Step 1: Learn the Basics** ✅
- Mastered Python, pandas, and machine learning fundamentals.
- Resources: Andrew Ng’s Machine Learning course, pandas tutorials.

### **Step 2: Get the Data** ✅
- Loaded RNA-seq data and metadata in Google Colab.
- Merged gene expression with cancer type labels (`primary_disease`).
- Output: 11,060 samples across 33 cancer types.

### **Step 3: Explore and Preprocess** ✅ *Completed*
- **Filtering**: Narrowed to BRCA, LUAD, PRAD.
- **Cleaning**: Removed 33 PRAD samples with 1,443 missing gene values.
- **Feature Selection**: Selected top 100 most variable genes.
- **Splitting**: 80% training (1,848 samples), 20% testing (463 samples).
- **Next**: Train the model in Step 4!

### **Step 4: Build and Train Model** ⏳
- Plan: Train a logistic regression model on preprocessed data.

### **Step 5: Evaluate and Improve** ⏳
- Assess accuracy and explore gene importance.

---

## 📊 Current Progress

### **Preprocessed Data Snapshot**
- **Initial Shape**: (11,060, 20,533) – 11,060 samples, 20,531 genes + metadata.
- **Filtered Shape**: (2,344, 20,535) – After selecting BRCA, LUAD, PRAD.
- **Cleaned Shape**: (2,311, 20,535) – After removing 33 PRAD samples.
- **Preprocessed Shape**: (2,311, 102) – 100 genes + `sample` + `primary_disease`.
- **Training Set**: (1,848, 100) – 80% of samples.
- **Testing Set**: (463, 100) – 20% of samples.

### **Sample Counts (After Cleaning)**
- **BRCA**: 1,218
- **LUAD**: 576
- **PRAD**: 517 (originally 550, reduced by 33)

### **Top 5 Most Variable Genes**
| Gene    | Variance  |
|---------|-----------|
| KLK3    | 54.47     |
| SFTPB   | 46.26     |
| KLK2    | 42.90     |
| SCGB2A2 | 35.46     |
| SFTPA1  | 34.84     |

### **Preprocessed Data Example**


### **Code Snippet**
```python
# Cleaning and Feature Selection
cleaned_data = filtered_data.dropna(subset=gene_cols)
top_genes = X.var().nlargest(100).index
X_selected = X[top_genes]
preprocessed_data = pd.concat([cleaned_data[['sample', 'primary_disease']], X_selected], axis=1)
Cancer-Classification-Project/
├── dataset_info.txt         # Dataset details and preprocessing notes
├── Step2_DataLoading.ipynb  # Data loading and merging
├── Step3_Preprocessing.ipynb # Preprocessing script
└── README.md                # Project overview (you’re here!)

git clone https://github.com/morshedik/Cancer-Classification-Project.git
