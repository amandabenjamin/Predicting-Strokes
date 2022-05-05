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

We found a moderate correlation between 'bmi' and 'age' features, and week correlation between the remaining variables (figure 1). 'Average glucose levels' (figure 2 and figure 3) and 'bmi' (figure 4 and figure 5) displayed non-gaussian distrobutions asserting a need to scale the data prior to fitting the model. 

Figure 1: Correlation heat map for 'numerical' features
![image](https://user-images.githubusercontent.com/99859350/166622150-fc83c7cf-251e-4953-b8cd-622c56738254.png)

Figure 2: Histogram plot for 'Average glucose levels' (clinical feature included in dataset) 
![image](https://user-images.githubusercontent.com/99859350/166622353-a864f47b-5981-417d-88e4-d9c5d0d9cf1b.png)

Figure 3: Boxplot for 'Average glucose levels' (clinical feature included in dataset) 
![image](https://user-images.githubusercontent.com/99859350/166622370-72f42932-9128-4eaf-a868-a2a8ca709146.png)

Figure 4: Histogram plot for patient 'BMI' (clinical feature included in dataset) 
![image](https://user-images.githubusercontent.com/99859350/166622393-85dd9bee-b305-4c90-92f2-5a33dac63626.png)

Figure 5: Boxplot for patient 'BMI' (clinical feature included in dataset) 
![image](https://user-images.githubusercontent.com/99859350/166622409-625ab1df-ba3a-4d99-a8f7-b1fd8e815da7.png)

Final model: 
I assesed the preformance of three models before deciding on a final 'production' model. The three models tested were: a decision tree, knn tree, and logistic (log.) regression model. Each model included PCA where 95% of the variation in the dataset was captured to help reduce unnecessary run time for the clinitian intended to use this model. Basis models were first utalised to assess performance on both the training dataset and testing dataset (data unseen to the model during its development) as well as the rate of false positive and false negative prediction. 

The log. regression model (with no tuning) was selected as 'production' model as it provided the highest accuracy on the testing dataset in combination with the least amount of fine tuning required by the clinitian - something benefitial for a user who may not have the highest python knowledge. 

1: (https://www.cdc.gov/stroke/facts.htm)
