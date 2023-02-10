# PCOS-detection-using-Random-Forest-Classifier
## Introduction

PCOS or Polycystic Ovarian Syndrome is a gender specific disorder that has become very prevalent among the females of reproductive age. Till date, no uniform set of symptoms have been identified in the patients suffereing from PCOS and shows heterogeneity among patients. The exact cause of PCOS is stil not clear but it is believed to be due to different interactions between genetic and environmental factors. The main aim of this project is to help with the classification of PCOS using the most prominent symptoms that have been documented in 541 patients across 10 different hospitals in Kerala, India. The dataset used contains 41 physical and clinical parameters to decide whether a patient has PCOS.

## Materials and Methods

There are two files which have been used for the project. The first file is in CSV format and contains data which involves the infertility information of the patients and the second file is an excel sheet that contains all the other parameters of the patients. To get the complete information about all the parameters, the two files were sorted and merged based on “Patient File No.” column and the extra columns due to the merge were dropped.

The next step was to check the type of data present in all the columns across the dataframe. This was done using “dropped_pcos.info()” which gave the information about the non-null count and dtype. Two columns - “II beta-HCG(mIU/ml)” and “AMH (ng/ml)” were found to be object type which was converted to numeric type.

Next, the columns were check for NaN values and it was found that a total of 4 NaN values were present in 4 different columns each. Hence, the rows with NaN values were removed.

## Exploratory Data Analysis

To check the correlation between all the features, a correlation matrix heat map was generated. The correlation matrix heat map scale is between 1 to -1 where 1 is marked by dark turquoise color showing high correlation and -1 is marked by dark orange showing no correlation. Some of the visible correlation from the heat map are - BMI & Weight, Follicle No. (L/R) & PCOS, weight gain/hair growth/skin darkening & PCOS, among other. To check the most important features that are related to PCOS, correlation values were checked for each of the columns and around 31 features were positively related and 10 features were negatively related to PCOS. To see the relation between the top two features (Follicle No. L/R) with PCOS, lmplot was used.

## Model building using Random Forest Classifier

Random Forest is a machine learning model that can be used for both regression and classification tasks. Since the problem at hand falls under classification category, Random Forest Classifier was used for the model building. The top 6 features were chosen for the model building and the target was “PCOS (Y/N)”. The data was split into 80% for training and 20% for testing purposes.

An instance for the Random Forest Classifier was created with the following parameters -

● criterion = “gini”

● N_estimators = 10

● Max_depth = 2

● Max_features = “auto”

● N_jobs = -1

After fitting the training data to the model, 85% accuracy score was obtained. To understand the importance of the features and which one contributes the most in the model, “feature_importance_” was used and it was found that follicle no. on the right ovary has the biggest impact on the decision, followed by follicle no. on the left ovary, hair growth, skin darkening, weight gain and cycle pattern.

A classification report was generated with the target names “PCOS Not Detected” and “PCOS Detected”. Two of the important information about the model that can be obtained from the classification report are precision and recall values. Precision is defined as the ability of the classifier not to label an instance as positive which was actually negative and recall is the ability of the classifier to find all the positive instances. The precision and recall values for “PCOS Not Detected” instances were 0.89 and 0.89 whereas for “PCOS Detected” instance the values were 0.77 and 0.77.

To fine tune the results, hyperparameter tuning was performed using GridSearchCV. The parameters chosen were ‘n_estimators’, ‘max_features’, ‘max_depth’, ‘criterion’, ‘n_jobs’ and ‘random_state’ which were passed to GridSeachCV() and the scoring was set to ‘accuracy’.

## Conclusion

After getting the best values for the hyperparameters, those values were passed to the classifier and the training data was fit accordingly. This resulted in the increase in accuracy of the model by 5% (from 85% to 90%). From the model, some day to day activities to decrease the effects of PCOS are weight loss, decrease in fast food consumption, regular exercise, etc. This model is efficient for early detection of PCOS which is a common problem nowadays as most of the women are undiagnosed.
