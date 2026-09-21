# Low-cost AI-assisted diabetic retinopathy screening designed around the equipment and referral constrains of Ethiopian Primary Healthcare

This project is designed to address equipment and resource constraints in primary healthcare settings. It uses adaptale and opensource repository to test feasibility and generalizability of model performance aganist local preproccessed retinal images. 

## 📌 Objectives

- Asses performance light weight ML models like EffcientNetB3 and MobilenetV2 applicability and generalizability in resource constrained settings compared to heavyweight ML architectures like CNN

- Sensitivity, Specificity, Positive Predictive Value, and Negative Predictive Value of the AI-assisted system compared to the reference standard

- Asses ungradable image rates and the factors contributing to them

## 📊 Dataset

- Kagle eye disease dataset: preprocessed 
 as training, validation and test dataset 

- Local image dataset: kaggle repository of Gondar University eye disease preprocessed and labeled dataset, to test generalizability 

## 🔬 Methods

### 1. Data Preprocessing

standardization and normalization.
Feature encoding for categorical variables.

### 2. Exploratory Data Analysis (EDA)

Distribution of eye disease.

### 3. Modeling


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
  
### Overall Model performance across methods: EffB3

- Resize + CLAHE + NLM:
 
Accuracy: 0.8617424242424242

Balanced accuracy: 0.8598583091252455

- Resize + CLAHE:

Accuracy: 0.875
Balanced accuracy: 0.8732523365485955



The machine learning model achieved an AUC of 0.920, indicating strong overall performance in predicting deterioration.
  
### Model Comparison (EffcientNetB3 Vs MobilenetV2)

- MobileNetV2

Classification Report

Accuracy: 0.75

Balanced accuracy: 0.7464499708432975

Diabetic predictability up to 97% accuracy on sample images, on the other hand performed poorly in other eye disease datasets.


- EffcientNetB3

Accuracy: 0.875

Balanced accuracy: 0.8732523365485955

Over all, better performance than MobileNet, but poor generalizability in diabetic retinopathy scoring in local image file.
 
  
## 🧩 Conclusion 

- The second method (removing NLM) showed higher accuracy (0.875 vs 0.8617). This highlights either the noise wasn't overly detrimental, or the NLM denoising might have inadvertently removed some subtle features that the model found useful.

- Glaucoma and Cataract in MobilenetV2, showed lower F1 Score, recall and accuracy, suggesting there might be Subtlety/Variability

- On the other hand, diabetic retinopathy showed best performance, which could explained by MobileNetV2 architecture (which excels at feature extraction) to identify distinct features such as hemmorhages, micro aneurysm compared to other conditions.

## Limitation

- Dataset small sample size

- Image quality and variability in augmentation and normalization techniques 

## 🚀 How to Run

Requirements

Python 3.x

pandas, numpy, matplotlib, seaborn

scikit-learn, Tensorflow 

## Author

Yonatan Yotora, MD

Adare General Hospital ,Hawassa, Ethiopia

