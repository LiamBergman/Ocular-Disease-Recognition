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

## Next Steps 
1. Data Preprocessing
- Deal with outliers, specifically the low-age records that could be considered outliers.
- Address class imbalance using techniques learned in later classes or by finding a supplementary dataset that could be added to this one to balance the classes.
2. Feature Engineering
- One-hot encode categorical variables like Patient Sex.
- Address the filepath and filename columns. They will likely not be needed in the models. filename seems to be redundant. 
3. Hypothesis for Further Analysis
- Upon the first pass it seems clear that a hypothesis can be made that as age progresses the likelihood of ocular disease increases. 
    - H0: An increase in age has no relation to an increase in ocular disease. 
    - H1: An increase in age comes with an increased likelihood of ocular disease. 
- We could also take a look at the relationship between gender on ocular diseases. 
4. Extended EDA
- Perhaps text analysis of the diagnostic keywords columns or more complex interaction effects between variables.
- Further dive into the age and gender relationships with disease.
5. Baseline Models
- Identify a set of baseline models to train such as logistic regression. 
6. Model Evaluation
- Define the metrics to be used for model evaluation. Accuracy or perhaps more advanced evaluation techniques will need to be used to evaluate potential models. 
- Identify if it is more important to have a high recall to identify as many disease cases as possible, even at the risk of false positives. Likely better to err on the safe side when it comes to the medical field and allow for doctor intervention (Doctor intervention should be done regardless). 
