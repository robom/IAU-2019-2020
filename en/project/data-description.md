# Dataset information

Dataset comprises records of patients with suspicion for diabetes. Data is separated into two files: personal information about patients and medical information. These files describe the same set of patients.

Patients used for a specified period of time (5-6 days) a device for continuous measurement of glucose and oxygen levels in blood. The device measured these two values in 30 second intervals. All measurements were aggregated across the whole collection period using various aggregation functions: mean, standard deviation, skewness and kurtosis. The dataset contains for every measured variable (blood glucose and oxygen level) results of these aggregation functions. At the same time, the dataset contains various basic information about the patient which could be factors in the development of the disease.

An independent test determined actual presence of the disease. This is stored in the `class` column (the name can vary for various datasets) and we consider it genuine. 

## Attribute information

Dataset contains attributes:
- Aggregated results of blood glucose level measurements using 4 different aggregation functions
- Aggregated results of blood oxygen level measurements using 4 different aggregation functions
- Informations about the patient such as age, date of birth, education level, employment class, marital status, race, sex, income, native country and weekly workload.
- Dependent variable indicating presence of the disease.
