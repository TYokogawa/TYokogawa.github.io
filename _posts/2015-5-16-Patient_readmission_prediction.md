---
layout: post
title: Hospitalied patient readmission prediction
---

### Machine learning to pridict hospital patient readmission

Readmission rate is one of the key indicators for the hospitals to maintain their quality.
In 2014, Medicare fined a record number of 2,610 hospitals  for having too many patients return within a month for additional treatments.
[reference](http://kaiserhealthnews.org/news/medicare-readmissions-penalties-2015/)

Predicting readmission within 30 days is very critical not only for the hospitals. If a patient can see his readmission risks, he and his family can prepare and prevent unwanted readmission.

<img src="{{ '/assets/img/readmission.jpg' | prepend: site.baseurl }}">

###Objective: Predict three readmission class of patient discharged to home.

1. Readmitted within 30 days of discharge
2. Readmitted after 30 days of discharge
3. No readmittion record (between 1999-2008)


###Data Source

* 101,766 patients hospitalization records.
* Health Facts database (Cerner Corporation, Kansas City, MO)
* The Health Facts data we used was an extract representing 10 years (1999–2008) of clinical care at 130 hospitals

Reference:
Beata Strack, Jonathan DeShazo, Chris Gennings, Juan Olmo, Sebastian Ventura, Krzysztof Cios, and John Clore
BioMed Research International Volume 2014 (2014)
[Link to the original paper](http://www.hindawi.com/journals/bmri/2014/781670/)


###Machine Learning

I used these 24 features to train readmission prediction algorithm. 
'race', 'gender', 'ages', 'admission', 'discharge', 'admsource', 'time_in_hospital', 'payer_code', 'num_lab_procedures', 'num_procedures', 'num_medications', 'number_outpatient', 'number_emergency', 'number_inpatient', 'diag1', 'diag2' 'number_diagnoses', 'max_glu_serum', 'A1Cresult', 'insulin', 'change', 'diabetesMed'


After developing prediction algorithm, by adding these 24 features data, the algorithm return one of three predicted readmission classes(readmit within 30 days, readmit after 30 days, no readmission).

###Building machine learning system

Medical diagnosis was categorized into 40 categories based on ICD-9 codes. 
Data sets are splitted 4:1:5 (training set : validation set : testing set). After creating and validate prediction model with training and validation sets, the prediction algorithm was applied to test sets. Using python machine learning module, I tested K-Nearest Neighbors, Logistic regression(with Lasso and Ridge regularization), Naive Bayes (Gaussian and Multinomial), Decision Tree, Support Vector Machine (Linear and RBF Kernel), RandomForest and GradientBoosting methods. Each algorithm showed different learning courve.
<img src="{{ '/assets/img/readm_learning_curve.png' | prepend: site.baseurl }}" alt=“" style="width: 600px;"/>

Further tuning Gradient Boosting and Random Forest model with number of estimators.
<img src="{{ '/assets/img/Number_of_estimator.png' | prepend: site.baseurl }}" alt=“" style="width: 600px;"/>

RandomForest model resulted highest F1 score (average of three classes, readmitted >30days, readmitted <30days, not readmitted)
<img src="{{ '/assets/img/ML_F1score.png' | prepend: site.baseurl }}" alt=“" style="width: 600px;"/>

##Predicting patients who would be readmitted within 30 days 
In real situation, patients or hospitals would more care about people readdmited within 30 days class. Because it would be worst experience compared to other after 30 days or no-readmission case.
The precision of predicting readmission within 30 days was very high with Random Forest based algorithm, which was 0.98 (168 out of 171 prediction was true).
<img src="{{ '/assets/img/ML_Precision.png' | prepend: site.baseurl }}" alt=“" style="width: 600px;"/>

This algorithm would be a useful predictor.
At the same time we need to pay attention recall score for readmission within 30 days is low in this prediction 0.10 (168 out of actual 1730 within 30days readmission cases).
This algorithm is precision (98%) predict patient readmitted within 30days, and it cover 10% of within 30 days readmission patients population. 
Check confusion matrix(RandomForest model).
<img src="{{ '/assets/img/ML_confision_mx.png' | prepend: site.baseurl }}" alt=“" style="width: 600px;"/>
<img src="{{ '/assets/img/ML_spec_sens.png' | prepend: site.baseurl }}" alt=“" style="width: 600px;"/>


##Top18 important features for readmission classification.
Specially after top10 is very interesting for me. 
<img src="{{ '/assets/img/ML_top18features.png' | prepend: site.baseurl }}" alt=“" style="width: 600px;"/>


num_lab_procedures: Number of lab tests performed during the encounter, 
num_procedures: Number of procedures (other than lab tests) performed during the encounter, 
num_medication: Number of distinct generic names administered during the encounter, 
number_outpatient: Number of outpatient visits of the patient in the year preceding the encounter, 
number_emergency: Number of emergency visits of the patient in the year preceding the encounter, 
number_inpatient: Number of inpatient visits of the patient in the year preceding the encounter, 
number_diagnoses: Number of diagnoses entered to the system, 
change of medication: Indicates if there was a change in diabetic medications
      
-------------------------------------
If you are interested in the detail of data source, please check these reference.
[Original paper](http://www.hindawi.com/journals/bmri/2014/781670/)
[Data file](https://archive.ics.uci.edu/ml/datasets/Diabetes+130-US+hospitals+for+years+1999-2008)





