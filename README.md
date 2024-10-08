# Dementia Prediction Using R

## Project Overview
This project involves data analysis of a dementia dataset, using machine learning algorithms to predict dementia diagnoses. The goal is to explore whether patterns in the dataset can reveal insights about dementia and help classify individuals based on cognitive and physiological data.

## Dataset Description
The dataset contains records from **150 individuals** aged between **60 and 98**, who underwent multiple assessments over time. Each individual has a varying number of assessments, and the dataset includes **373 scans** in total. Out of the 150 individuals:
- **72** are healthy.
- **64** are diagnosed with dementia.
- **14** initially diagnosed as healthy were later diagnosed with dementia.

### Key Features
The dataset includes the following features:
- **SubjectId**: Unique identifier for each patient.
- **MRI ID**: Identifier for each MRI scan.
- **Group**: Dementia diagnosis (Demented/Non-Demented).
- **Age, Gender**: Demographic information.
- **CDR**: Clinical Dementia Rating, a key measure of dementia severity.
- **MMSE**: Mini-Mental State Examination score for cognitive function.
- **SES**: Socio-economic status.
- **eTIV, nWBV, ASF**: Physiological brain measurements obtained through MRI.

## Analyzing Steps

### 1. **Preprocessing**:
   - **Removing uninformative columns**: Columns such as **MRI ID**, **Visit**, and **Handedness** were removed to reduce data complexity.
   - **Handling missing data**: Removed records with missing socio-economic status (8 patients, 19 scans in total).
   - **Label Adjustment**: For individuals who were initially healthy but later diagnosed with dementia, intermediate records were removed, leaving only the first healthy record and the final dementia diagnosis.
   - Final dataset: **345 scans**.

### 2. **Feature Selection**:
   - **Correlation Analysis**: A correlation matrix was used to identify highly correlated features, such as **ASF** and **eTIV**. Features with a correlation above 0.75 were removed to reduce redundancy.

<img src="https://github.com/user-attachments/assets/85817e70-7c11-4274-9586-9f3d650a8aa4" alt="image" width="500"/>

   - **Rank by Importance**: Using **Random Forest**, the most important features for predicting dementia were identified:
     - **CDR** (Clinical Dementia Rating)
     - **MMSE** (Mini-Mental State Examination)
     - **nWBV** (Normalised Whole Brain Volume)
     - **ASF** (Atlas Scaling Factor)


### 3. **Machine Learning Models**:

- **K-Nearest Neighbors (KNN)**:
  - **Normalization**: The data was normalized using Min-Max scaling to improve performance.
  - **Train-Test Split**: 80% of the data was used for training, and 20% for testing.
  - **Results**:
    - **Accuracy for non-demented individuals**: 100%.
    - **Accuracy for demented individuals**: 76%.

- **Random Forest**:
  - Random Forest was applied to classify the dataset, leveraging its ability to handle high-dimensional data and rank feature importance.
  - **Feature Importance**: The most significant features were **CDR**, **MMSE**, **nWBV**, and **ASF**.
  - **Results**: Random Forest produced competitive results, offering another perspective for classifying dementia.

- **Support Vector Machine (SVM)**:
  - SVM was used as a comparison to the other models, given its effectiveness in binary classification.
  - **Kernel Function**: A linear kernel was applied.
  - **Results**: SVM achieved a balanced accuracy, though performance varied depending on the parameter tuning.


## Results and Conclusion

- **K-Nearest Neighbors (KNN)**:
  - The model successfully classified **non-demented individuals** with 100% accuracy.
  - For **demented individuals**, the model achieved a classification accuracy of 76%, indicating room for improvement in identifying dementia cases.

  <div style="display: flex;">
  <img src="https://github.com/user-attachments/assets/0a103788-dec2-4f2b-aa06-c0c55fadce3c" alt="image" width="300"/>
  <img src="https://github.com/user-attachments/assets/995d9035-7e0e-44c3-9b6b-183e0ceac5fa" alt="image" width="300"/>
  </div>


- **Random Forest**:
  - Random Forest provided robust results, particularly excelling in feature importance analysis.
  - The most critical features identified were **CDR**, **MMSE**, **nWBV**, and **ASF**.
  - The model showed an improvement over KNN, with a higher overall accuracy, especially in classifying demented individuals.

- **Support Vector Machine (SVM)**:
  - Using a linear kernel, SVM offered balanced results across both demented and non-demented categories.
  - The model performed similarly to Random Forest but showed sensitivity to parameter tuning, indicating the potential for further optimization.

### Conclusion:
- **Random Forest** and **SVM** performed better overall compared to KNN, especially in classifying individuals with dementia.
- The analysis confirmed that cognitive scores (**CDR**, **MMSE**) and brain volume measurements (**nWBV**, **ASF**) are significant predictors of dementia.
- The data supported the positive correlation between higher education and improved cognitive function, reaffirming that education may play a protective role against dementia.

### Future Work:
- Further optimize the **SVM** and **Random Forest** models by tuning parameters.
- Compare the models using cross-validation techniques.
- Apply **PCA** for dimensionality reduction and explore clustering with **K-Means** to improve classification accuracy.

---

## Contributors
- **Reut Lev** (reutlev98)
- **Ye'ela Granot** (yeela8g)
- **Shir Ohayon** (shir677)
