# Diabetes Prediction System  
This project implements a **Diabetes Prediction System** using the **PIMA Diabetes Dataset**. It detects whether a patient is **diabetic** or **non-diabetic** based on several health metrics. 

> **Note:** The dataset contains information for **females only**, so the model may not generalize well for other demographics. 

---

## Table of Contents
- [Overview](#overview)
- [Dataset Description](#dataset-description)
- [Model Performance](#model-performance)
- [Usage](#usage)

---

## Overview  
The **Diabetes Prediction System** uses **Support Vector Machine (SVM)** to classify patients as **diabetic or non-diabetic** based on 8 features. The dataset is relatively small, so the model isn’t highly robust but still provides decent accuracy.

---

## Dataset Description  
This system uses the **PIMA Diabetes Dataset**, which contains the following features:
- **Pregnancies**: Number of times pregnant  
- **Glucose**: Plasma glucose concentration  
- **BloodPressure**: Diastolic blood pressure (mm Hg)  
- **SkinThickness**: Triceps skinfold thickness (mm)  
- **Insulin**: 2-Hour serum insulin (mu U/ml)  
- **BMI**: Body mass index (weight in kg/(height in m)^2)  
- **DiabetesPedigreeFunction**: Diabetes pedigree function  
- **Age**: Age in years  
- **Outcome**: 0 (non-diabetic), 1 (diabetic)  

Example of the dataset:

| Pregnancies | Glucose | BloodPressure | SkinThickness | Insulin | BMI | DiabetesPedigreeFunction | Age | Outcome |
|-------------|---------|---------------|---------------|---------|-----|-------------------------|-----|---------|
| 6           | 148     | 72            | 35            | 0       | 33.6| 0.627                   | 50  | 1       |
| 1           | 85      | 66            | 29            | 0       | 26.6| 0.351                   | 31  | 0       |
| 8           | 183     | 64            | 0             | 0       | 23.3| 0.672                   | 32  | 1       |
| 1           | 89      | 66            | 23            | 94      | 28.1| 0.167                   | 21  | 0       |
| 0           | 137     | 40            | 35            | 168     | 43.1| 2.288                   | 33  | 1       |

---

## Model Performance  
Here are the accuracy results for the **SVM model**:

- **Training Accuracy:** 78.66%  
- **Testing Accuracy:** 77.27%  

---

## Usage  
To predict whether a patient is diabetic or non-diabetic, use the following code:

```python
# Example input data: 8 health metrics for a patient
input_data = (6, 148, 72, 35, 0, 33.6, 0.627, 50)

# Convert input data to a NumPy array for faster processing
input_data_as_numpy_array = np.asarray(input_data)

# Reshape the data for a single prediction (1 sample, 8 features)
input_data_reshaped = input_data_as_numpy_array.reshape(1, -1)

# Define feature names (same as during model training)
columns = ['Pregnancies', 'Glucose', 'BloodPressure', 'SkinThickness', 
           'Insulin', 'BMI', 'DiabetesPedigreeFunction', 'Age']

# Create a DataFrame with input data and corresponding feature names
input_df = pd.DataFrame(input_data_reshaped, columns=columns)

# Standardize the input data (same scaling as during model training)
std_data = scaler.transform(input_df)

print(std_data)  # View the standardized input

# Make a prediction using the trained model
prediction = classifier.predict(std_data)

if prediction[0] == 1:
    print('Patient is Diabetic')
else:
    print('Patient is Non-diabetic')
```

Feel free to reach out if you have any questions or suggestions!
