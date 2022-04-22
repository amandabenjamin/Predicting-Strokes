# Predicting-Strokes

Americans are overwhelmingly at risk for stroke! 

According to the CDC (1), the leading causes of stroke include "age, high blood pressure, high cholesterol, smoking, obesity, and diabetes". Cumulativly, more than 795,000 people in the USA have reported having had a stroke (1) - of which approximatly 185,000 individuals repoted having multiple strokes. Nearly $53 billion was spent on stroke-related costs in the US alone (1)! 

Thus, there is a need to predict the likelyhood of stroke occurance for the american population (based on easily accessible patient information (aka clinical features)) to not only reduce the final impact of strokes on US healthcare but, most importantly, improve the livleyhood of the american population. 

The dataset used in this investigation can be found here: https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset
This dataframe contains 5110 observations with 12 features (11 clinical features and 1 patient identification method). The 11 clinical features including but not limited to: patient gender, age, residence, average glucose level, bmi, smoking status, heart disease status, and hypertension status. Additionally, it includes our predictive feature: stroke status. For the purpose of this project, We predict the likleyhood of stroke occurance for a patient given their reported clinical features. 

Data pre-processing included: 

1. Removing unnecessary columns such as anything 'unique' to identify the patient. Removing unique identifiers prohibits the unintended consequence of overtraining our eventual classification model. 
2. Checking for and removing any duplicated values. 
3. Addressing missing (NAN) values. 
   We determined only 201 values were missing from the dataset and they only came from the BMI feature. As a rule of thumb learned from this course, its okay to drop missing data as long as its less than 10% of the total dataset. Since 201 values only comprise ~4% of the dataset - I dropped these features from the dataset. It was easier to drop them than try to 'fill them' in using a guessing method such as back fill or forward fill that could have resulted in incorrect bmi values and thus an incorrect predictive model. 
4. Addressing inconsitant categorical values. 
5. Ensuring numerical data made sense (i.e. Age featured in the study was greater than 0 and less than 100). 

We found a moderate correlation between 'bmi' and 'age' features, and week correlation between the remaining variables. 'Average glucose levels' and 'bmi' displayed non-gaussian distrobutions asserting a need to scale the data prior to fitting the model. 

1: (https://www.cdc.gov/stroke/facts.htm)
