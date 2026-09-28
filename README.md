# Evaluation and external validation of resource-efficient deep-learning models for retinal disease classification in resource-constrained healthcare settings

## Model Design 


                         ┌──────────────────────┐
                         │ Public Kaggle Dataset │
                         └──────────┬───────────┘
                                    │
                              development set
                                    │
                     ┌──────────────┴──────────────┐
                     │                             │
                   Train                         Validation
                     │
                     ▼
              Model development
                     │
                     ▼
               Locked model
                     │
                     │
                     ▼
        ┌─────────────────────────────┐
        │ Completely untouched local  │
        │ Ethiopian/Gondar dataset    │
        └──────────────┬──────────────┘
                       │
                External validation
                       │
                       ▼
          Generalization performance



The study evaluates resource-efficient convolutional neural networks for retinal image classification and investigates generalizability using an independent local dataset.

## 📌 Research Questions 

1. How accurately can EfficientNetB3 and MobileNetV2 classify retinal diseases images?

2. How do preproccessing affect model performance

3. How well do model trained on the public development dataset generalize to an independent local dataset?

4. what computational characteristics affect deployment feasibility in resource-constrained settings?

## 📊 Dataset and Study design

Kagle eye disease dataset:

- Preprocessing

- train/validation/test

- modeldevelopment

- locked model

- independent local external validation

## 🔬 Methods and Models

### Data Preprocessing
- Resize

- CLAHE

- NLM denoising

- Normalization

- Training augmmentation

### Model Evaluation
- Accuracy

- Balanced Accuracy

- Macro-F1

- Per-class sensitivity

- Per-class specificity

- ROC-AUC

- Confusion matrix

- 95% confidence interval

- Model size

- Parameter count

- Inference time

### Reproducibility
All experiments use fixed random seeds and version-pinned dependence.

## Data Availability
The Public dataset is available from: https://www.kaggle.com/datasets/gunavenkatdoddi/eye-diseases-classification

The local dataset: https://www.kaggle.com/datasets/esubalewasmare/retinal-disease-fundus-images-datasets

## 📈 Key Results

### Dataset characteristics 

Public Dataset: A total of 4217 images containing four eye diseases classes: 

- Diabetic retinopathy    1098

- Normal                  1074
- Cataract                1038
- Glaucoma                1007

Local dataset: University of Gondar Referral Hospital (UOGRH) Eye Clinic in Ethiopia. The final dataset consisted of 3,848 labeled images, partitioned into four distinct clinical categories: 

- Diabetic Retinopathy (DR) (31% or 1,192 images),

- Normal (29% or 1,116 images),

- Glaucoma (26% or 999 images), and

- Age-related Macular Degeneration (AMD) (14% or 541 images).

NB: For analysis purpose the dataset containing cataract from the public and AMD were excluded prior to cross validation
  
### Model performance across methods

#### Experiment 1: EfficientNetB3 Baseline
17/17 ━━━━━━━━━━━━━━━━━━━━ 34s 2s/step

Accuracy: 0.8882575757575758

Balanced accuracy: 0.88601454625216

Classification report:

                      precision    recall  f1-score   support

            cataract     0.9302    0.9302    0.9302       129
            
diabetic_retinopathy     0.9424    0.9493    0.9458       138

            glaucoma     0.9126    0.7460    0.8210       126
            
              normal     0.7898    0.9185    0.8493       135

            accuracy                         0.8883       528
            
           macro avg     0.8938    0.8860    0.8866       528
           
        weighted avg     0.8933    0.8883    0.8875       528

#### Experiment 2: NLM 
17/17 ━━━━━━━━━━━━━━━━━━━━ 119s 6s/step

Accuracy: 0.8522727272727273

Balanced accuracy: 0.8493633674119012

Classification report:

                      precision    recall  f1-score   support

            cataract     0.8992    0.8992    0.8992       129
            
diabetic_retinopathy     0.9333    0.9130    0.9231       138

            glaucoma     0.8750    0.6667    0.7568       126

              normal     0.7381    0.9185    0.8185       135

            accuracy                         0.8523       528
            
           macro avg     0.8614    0.8494    0.8494       528
           
        weighted avg     0.8612    0.8523    0.8508       528

#### Experiment 3: MobileNetV2 Architecture Comparison
17/17 ━━━━━━━━━━━━━━━━━━━━ 22s 1s/step

Accuracy: 0.6893939393939394

Balanced accuracy: 0.6861009463891163

Classification report:

                      precision    recall  f1-score   support

            cataract     0.7308    0.5891    0.6524       129
            
diabetic_retinopathy     0.8492    0.7754    0.8106       138

            glaucoma     0.5920    0.5873    0.5896       126
            
              normal     0.6185    0.7926    0.6948       135

            accuracy                         0.6894       528
            
           macro avg     0.6976    0.6861    0.6869       528
           
        weighted avg     0.6999    0.6894    0.6896       528


#### Experiment 4: Locked-Model External Validation (Gondar Dataset)
Gonder Dataset Summary (Post-Filtering)

Total valid images loaded: 3323

label

- diabetic_retinopathy: 1204

- normal: 1112

- glaucoma: 1007

Name: count, dtype: int64

104/104 ━━━━━━━━━━━━━━━━━━━━ 13s 77ms/step

--- Gonder Locked Model External Validation Report ---

                      precision    recall  f1-score   support

diabetic_retinopathy       0.91      0.92      0.91      1204

            glaucoma       0.80      0.79      0.80      1007
            
              normal       0.81      0.77      0.79      1112

           micro avg       0.84      0.83      0.84      3323
           
           macro avg       0.84      0.82      0.83      3323
           
        weighted avg       0.84      0.83      0.84      3323

#### Experiment 5: Computational & Deployment Analysis

Computational Profiling Results:

- Model Size (MB): 9.28
  
- Total Parameters: 2268228
  
- Trainable Parameters: 7684
  
- Single-Image CPU Latency (ms): 292.82
  
- Throughput (FPS): 3.42

## 🧩 Conclusion 

- In the third experiment removing no-local means denoising was associated with higher validation/test performance than the preprocessing pipeline incorporating denoising. This finding does not establish that denoising removes clinically relevant feature; the difference may reflect interaction between preprocessing, augmentation, model architecture, and dataset characterstics.

- Glaucoma and Cataract in MobilenetV2, showed lower F1 Score, recall and accuracy, suggesting there might be Subtlety/Variability

- MobileNetV2 demonstrated comparatively higher performance for the diabetic-retinopathy class in the evaluated test set. However,class-specificperformance varied across datasets,and the observed results don't establish that the architecture specifically detects individual retinal lesions such as microaneurysms or hemorrhages.

## Limitation
### Dataset Limitations
- Relatively Small datset

- Public dataset may not represet Ethiopian primary-care populations

- Possible class imbalance

- Possible difference in image acquisation devices
### ExternalValidation Limitaion

- Local dataset size

- Whether images are truly independet

- preprocessing differences

### Clinical Limitaions
- No prospective clinical evaluation

### Generalizability

These findings provide preliminary evidence regarding computational feasibility and cross-dataset generalizability

## 🚀 How to Run

Requirements

Python 3.x

pandas, numpy, matplotlib, seaborn

scikit-learn, Tensorflow 

## Author

Yonatan Yotora, MD

Adare General Hospital ,Hawassa, Ethiopia

