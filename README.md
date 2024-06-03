# Health Data Gen

Health Data Gen is a Python library for generating synthetic health datasets. This can be useful for testing, prototyping, and training machine learning models when real-world data is not available or cannot be used due to privacy concerns.

## Features

- Generates a dataset with attributes related to demographics, medical history, vital signs, treatments, complication risks, and readmission outcomes.
- Easy to customize and extend with additional attributes.

## Installation

To use this script, you need to have `pandas` installed. You can install it using pip:

```bash
pip install pandas
```

## Usage

Here's an example of how to generate a dataset with 50,000 rows:

```python
import pandas as pd
import random

def generate_dataset(num_rows):
    # Define lists of possible values for each attribute
    demographics_values = {
        "Age": range(18, 101),
        "Gender": ["Male", "Female"],
        "Ethnicity": ["Caucasian", "African American", "Hispanic", "Asian", "Other"],
        "Socioeconomic_Status": ["Low", "Middle", "High"]
    }
    
    medical_history_values = {
        "Medical_Conditions": ["Hypertension", "Diabetes", "Asthma", "Heart Disease", "Obesity", "None"],
        "Chronic_Diseases": ["Arthritis", "Cancer", "Chronic Kidney Disease", "Stroke", "Chronic Obstructive Pulmonary Disease", "None"],
        "Family_Medical_History": ["Heart Disease", "Diabetes", "Cancer", "Alzheimer's Disease", "Stroke", "None"]
    }
    
    vital_signs_values = {
        "Blood_Pressure": [(random.randint(90, 140), random.randint(60, 90)) for _ in range(num_rows)],
        "Heart_Rate": [random.randint(60, 100) for _ in range(num_rows)],
        "Body_Temperature": [round(random.uniform(36.0, 37.5), 1) for _ in range(num_rows)],
        "Respiratory_Rate": [random.randint(12, 20) for _ in range(num_rows)],
        "BMI": [round(random.uniform(18.5, 35.0), 1) for _ in range(num_rows)]
    }
    
    treatment_values = {
        "Rehabilitation_Services": ["Physical Therapy", "Occupational Therapy", "Speech Therapy", "None"],
        "Follow-up_Appointments": ["Cardiology", "Endocrinology", "Pulmonology", "Primary Care", "None"],
        "Discharge_Summary": ["Stable condition, discharged home", "Transferred to rehabilitation facility", "Transferred to long-term care facility", "None"],
        "Prescribed_Medical_Equipment": ["Wheelchair", "Walker", "CPAP Machine", "None"],
        "Consultation_Notes": ["Recommend lifestyle modifications", "Refer to specialist for further evaluation", "Continue current treatment plan", "None"]
    }
    
    complication_risk_values = {
        "Cardiac_Risk_Factors": ["Hypertension", "Coronary Artery Disease", "Smoking", "None"],
        "Respiratory_Risk_Factors": ["Chronic Obstructive Pulmonary Disease", "Asthma", "Smoking", "None"],
        "Renal_Risk_Factors": ["Chronic Kidney Disease", "Diabetes", "Hypertension", "None"],
        "Coagulation_Risk_Factors": ["Deep Vein Thrombosis", "Pulmonary Embolism", "Bleeding Disorders", "None"],
        "Psychosocial_Risk_Factors": ["Depression", "Anxiety", "Substance Abuse", "None"]
    }
    
    readmission_outcome_values = {
        "Readmission_Within_30_Days": ["Yes", "No"],
        "Reason_for_Readmission": ["Complication related to initial condition", "New medical issue", "Social factors", "None"]
    }
    
    # Create DataFrame for each table
    demographics_df = pd.DataFrame({attr: random.choices(values, k=num_rows) for attr, values in demographics_values.items()})
    medical_history_df = pd.DataFrame({attr: random.choices(values, k=num_rows) for attr, values in medical_history_values.items()})
    vital_signs_df = pd.DataFrame(vital_signs_values)
    treatment_df = pd.DataFrame({attr: random.choices(values, k=num_rows) for attr, values in treatment_values.items()})
    complication_risk_df = pd.DataFrame({attr: random.choices(values, k=num_rows) for attr, values in complication_risk_values.items()})
    readmission_outcome_df = pd.DataFrame({attr: random.choices(values, k=num_rows) for attr, values in readmission_outcome

_values.items()})
    
    # Combine DataFrames
    dataset = pd.concat([demographics_df, medical_history_df, vital_signs_df, treatment_df, complication_risk_df, readmission_outcome_df], axis=1)
    
    return dataset

# Example usage:
dataset = generate_dataset(50000)  # Generate a dataset with 50000 rows
print(dataset.head())  # Display the first few rows of the dataset
```

## Contributing

Feel free to submit issues or pull requests if you have suggestions for improvements or new features.

## License

This project is licensed under the MIT License.

