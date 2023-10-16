# Project Overview 

## Problem Area
The problem revolves around the diagnosis of ocular diseases, which can be a time-consuming and expensive process. A delay in diagnosis can lead to irreversible vision loss and decreased quality of life for patients.

## Those Affected
The affected individuals include:

- Patients at risk or suffering from ocular diseases
- Ophthalmologists and healthcare providers
- Medical institutions
- Medical technology companies

## Data Science Solution
The goal is to develop machine learning models to automatically classify fundus images into eight predefined categories of ocular diseases. This will aid in faster and more accurate diagnosis.

## Impact
- Quicker diagnosis and treatment initiation
- Relief in diagnostic workload for healthcare providers
- Opening avenues for remote diagnosis through telemedicine

## Dataset Description
The dataset consists of 5,000 patient records with 14.4k preprocessed fundus images. These are collected from Shanggong Medical Technology Co., Ltd. from various hospitals and medical centers in China and are labeled by trained human readers.

- Fields include:
    - ID: Unique identifier for each record
    - Patient Age: The age of the patient
    - Patient Sex: Gender of the patient
    - Left-Fundus: Left eye fundus image filename
    - Right-Fundus: Right eye fundus image filename
    - Left-Diagnostic Keywords: Diagnostic keywords for the left eye
    - Right-Diagnostic Keywords: Diagnostic keywords for the right eye
    
- Additional Fields:
    - Filepath: Path to the fundus image
    - Labels: List of applicable disease labels
    - Target: Binary vector representing the disease labels
    
- Labels (as separate columns):
    - Normal (N)
    - Diabetes (D)
    - Glaucoma (G)
    - Cataract (C)
    - Age-related Macular Degeneration (A)
    - Hypertension (H)
    - Pathological Myopia (M)
    - Other diseases/abnormalities (O)
    
## Data Dictionary

| Field                    | Type         | Description                                        |
|--------------------------|--------------|----------------------------------------------------|
| ID                       | Numeric      | Unique identifier for each record                  |
| Patient Age              | Numeric      | Age of the patient                                 |
| Patient Sex              | Categorical  | Gender of the patient                              |
| Left-Fundus              | Text         | Filename for the left eye fundus image             |
| Right-Fundus             | Text         | Filename for the right eye fundus image            |
| Left-Diagnostic Keywords | Text         | Keywords for diagnosing the left eye               |
| Right-Diagnostic Keywords| Text         | Keywords for diagnosing the right eye              |
| N, D, G, C, A, H, M, O   | Binary       | One-hot encoded disease labels                     |
| Filepath                 | Text         | Path to the fundus image                           |
| Labels                   | Text         | List of applicable disease labels                  |
| Target                   | Text         | Binary vector representing the disease labels      |

## EDA Notebook
The Initial Exploratory Data Analysis (EDA) offers a thorough look into various aspects of the dataset. It starts by describing the age distribution of the patients, moves on to discuss gender distribution, and provides statistics on the prevalence of different ocular diseases. Correlation was studied to explore the relationships between diseases and patient demographics. Statistical tests, specifically Chi-Squared Tests and Correlation Coefficients, are performed to validate the observed correlations concerning both age and gender. The Data Preprocessing section touches on the handling of outliers in the dataset. The notebook also includes a section presenting sample images from the dataset.
## Models Notebook
It serves as the second part of the project focused on building and evaluating machine learning models. The notebook includes sections on data preprocessing, feature engineering, dimensionality reduction through Principal Component Analysis (PCA), model training and evaluation, model comparison, and hyperparameter tuning. It also compares the key performance metrics of different models before and after hyperparameter tuning, utilizing metrics like accuracy, recall, and F1-score. The most improved model from hyperparamter tuning was Random Forest while the least improved models were the Neural Networks and Gradient Boosting. There was a performance decrease for Logistic Regression and SVM.

## CNN Baseline Notebook
The notebook dives into defining the model architecture and training it, with techniques like early stopping based on validation loss. Data augmentation and transformation techniques are also implemented. For instance, training transformations include random rotations and color jittering. The notebook evaluates the model using metrics of F1 Score, Recall, and Accuracy. It also compares the performance metrics between an augmented baseline CNN model and an initial one. It concludes that the augmented model performs better in terms of F1 Score, indicating more balanced and improved classification performance with Recall and Accuracy bring fairly stable, showing a slight increase from the initial to the augmented model.

## CNN Final Notebook
The notebook's final model displayed mixed results in its performance metrics. While it outperformed the initial baseline model in terms of F1 Score, Recall, and Accuracy, it did not match the efficacy of the previous baseline model. Specifically, the F1 Score for the final model was 0.204, which was better than the initial baseline's 0.168 but inferior to the previous baseline's 0.325. The K-Fold validation results also indicated variability in these metrics.

## Conclusions
The final model showed improvement over the initial baseline but performed less optimally compared to the previous baseline with the K-Fold validation indicating variability in performance metrics.
Given the current metrics and observations, further diagnostic analysis and model refinement are needed. A systematic approach to identifying bottlenecks and areas for improvement will be essential for enhancing the model's performance.