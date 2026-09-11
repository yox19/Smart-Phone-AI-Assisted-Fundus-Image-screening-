# Low-cost AI-assisted diabetic retinopathy screening designed around the equipment and referral constrains of Ethiopian Primary Healthcare

This project is designed to address equipment and resource constraints in primary healthcare settings. It uses adaptale and opensource repository to test feasibility and generalizability of model performance aganist local preproccessed retinal images. 

## 📌 Objectives

## 📊 Dataset

## 🔬 Methods

### 1. Data Preprocessing

Handling missing values and normalization.
Feature encoding for categorical variables.
### 2. Exploratory Data Analysis (EDA)

Distribution of risk factors.
Correlation analysis between clinical variables and stroke.
### 3. Modeling

Logistic Regression
Random Forest Classifier
Evaluation with Accuracy, Precision, Recall, F1-score, ROC-AUC.
### 4. Model Refinement

Train/test split to avoid overfitting.
Hyperparameter tuning.
Comparison of performance across models.

## 📈 Key Results

### Exploratory Data anlysis

- Demographics:
  
- Age group:
  
- Comorbidities:
  
### Overall Model AUC: 
The machine learning model achieved an AUC of 0.920, indicating strong overall performance in predicting deterioration.

### Subgroup Analysis: Performance varied across different patient subgroups:

- Pneumonia Only (no HF): AUC of 0.939
  
- Pneumonia + Heart Failure: AUC of 0.881
  
- Pneumonia + HF + Anemia: AUC of 0.809
  
- HIV Positive: AUC of 0.894
  
- Age > 60: AUC of 0.911
  
### Model Comparison (ML Model vs. NEWS2 Alone):

- NEWS2 Alone AUC: 0.898
  
- ML Model AUC: 0.920
  
The ML model showed an improvement of 0.021 AUC (+2.4%) over NEWS2 alone.

### Time to Deterioration by Subgroup: 
The mean time to deterioration across subgroups ranged from 30 to 32 hours from admission.

## 🧩 Clinical Relevance

## Limitation

## 🚀 How to Run

Requirements

Python 3.x

pandas, numpy, matplotlib, seaborn

scikit-learn

## Author

Yonatan Yotora, MD

Adare General Hospital ,Hawassa, Ethiopia

