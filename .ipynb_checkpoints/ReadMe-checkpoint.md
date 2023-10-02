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

## The work in progress
1. Data Preprocessing
- *DONE* Deal with outliers, specifically the low-age records that could be considered outliers.
    - It has been shown that the low age records are not statisticall significant in skewing the data and will be left in as they are also likely medically significant in this study. 
- *WIP* Address class imbalance using techniques learned in later classes or by finding a supplementary dataset that could be added to this one to balance the classes.
    - The data was sorted using significant labels to ensure that diseases that were not as commonly represented in the data were evenly distributed in the training and test sets. 
    - An supplementary dataset was not found to bolster the images in this set. Additional efforts will have to be taken to balance the data before final model is built out. 
2. Feature Engineering
- *NOT REQUIRED* One-hot encode categorical variables like Patient Sex.
    - Because we are doing image recognition this was not done.
    
- The images were flattened and normalized to run some baseline models. In addition to this PCA was performed on the training set to some minor success. 
- The images were all scalled to the same size

- *NOT REQUIRED* Address the filepath and filename columns. They will likely not be needed in the models. filename seems to be redundant. 
    - Because we are doing image recognition this was not done.
3. Hypothesis for Further Analysis
- *DONE* Upon the first pass it seems clear that a hypothesis can be made that as age progresses the likelihood of ocular disease increases. 
    - H0: An increase in age has no relation to an increase in ocular disease. *REJECTED*
    - H1: An increase in age comes with an increased likelihood of ocular disease. 
    - The null-hypothesis was rejected and it was show that as age increases it has a statistical significance on the increased likelihood of ocular disease. 
4. Extended EDA
- *DONE* Perhaps text analysis of the diagnostic keywords columns or more complex interaction effects between variables.
    - The diagnostic keyword columns are represented in the labeled disease columns. 
- *DONE* Further dive into the age and gender relationships with disease.
    - It was thought that a thorough exploration of this was completed in the previous sprint. 
5. Baseline Models
- *DONE* Identify a set of baseline models to train such as logistic regression. 
    - A series of baseline models were run to give an idea of which models will be persued in future sprints. 
    - These include: 
        - Logistic Regression
        - Random Forest 
        - Basic CNN
6. Model Evaluation
- *DONE* Define the metrics to be used for model evaluation. Accuracy or perhaps more advanced evaluation techniques will need to be used to evaluate potential models. 
    - Metrics were defined that will be used to evaluate models going forward. 
    - These include:
        - Accuracy
        - Confusion Matrix
        - F1-score, Precision, Recall
        - AUC-ROC
        - Training/Validation Loss
- *DONE* Identify if it is more important to have a high recall to identify as many disease cases as possible, even at the risk of false positives. Likely better to err on the safe side when it comes to the medical field and allow for doctor intervention (Doctor intervention should be done regardless). 
    - It is definitely more important to potentially misdiagnose a disease rather than have a disease not be diagnosed as early detection of many diseases leads to better outcomes of health. 
## Next Steps 
1. Advanced Model Building
- Deepen CNN Architecture: Add more convolutional layers to capture intricate features in the images.
- Use Transfer Learning: Incorporate pre-trained models like VGG, ResNet, or Inception to leverage features learned from similar tasks.
- Ensemble Models: Combine predictions from different models, such as CNNs, Random Forests, and SVMs, to improve overall prediction accuracy.
2. Optimization 
- Hyperparameter Tuning: Use techniques like grid search or random search to optimize hyperparameters for each model.
- Regularization: Implement dropout and L1/L2 regularization to control overfitting.
- Learning Rate Scheduling: Apply adaptive learning rate techniques to improve the training process.
- Data Augmentation: Employ techniques like image rotation, scaling, and flipping to make the model more robust.
    - This will have to be done with care as we do not know if having a more robust model that can interpret rotated images will be as beneficial as a model that is really good at interpretting a predetermined output that most OCT machine will provide a model. 
3. Evaluation
- Cross-Validation: Use k-fold cross-validation to get a more reliable evaluation metric for model performance.
- Use Multiple Metrics: Besides accuracy, also evaluate the models using F1-score, AUC-ROC, and confusion matrices for a comprehensive assessment.
- Class-specific Metrics: If classes are still imbalanced, focus on class-specific metrics like precision, recall, and F1-score for each class to mitigate this imbalance.
4. Interpretation.
- Analysis of Misclassifications: Examine instances where the model performs poorly to gain insights into its limitations.
5. New Notebook
- I think it would be beneficial to split the notebook up as it is getting unduely large and hard to find all of the information. 
