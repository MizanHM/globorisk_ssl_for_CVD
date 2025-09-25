**Integrating a Statistical Model with Self-Training Machine Learning approach for cardiovascular disease Risk Labeling in Ethiopia.**

**This project explores how semi-supervised machine learning (SSL) can complement the Globorisk framework, a statistical model used to estimate 10-year cardiovascular disease (CVD) risk.** 



Traditionally, Globorisk estimates CVD risk in adults aged 40 and above. In this project, I experimented with SSL techniques to extend risk stratification to younger adults, thereby broadening the applicability of conventional risk labeling. Alongside, I built a custom data analysis and ML pipeline to showcase EDA, modeling, and validation using real-world health survey data.







**Objectives**

\- Calculate 10-year CVD risk using the Globorisk model.

\- Validate Globorisk predictions against WHO risk categories.

\- Build a semi-supervised learning framework to extend risk labeling beyond the 40+ cohort.

\- Showcase data science and ML workflows in a health data context.







**Work flow**



	Data Cleaning and Preparation

     o	Used the STEPs survey dataset. 

     o	Selected key features: `age`, `sex`, `Diabetes Mellitus`, `Total Cholesterol`, `smoking status`, `systolic blood pressure`, and `CVD history`. 

	Exploratory Data Analysis (EDA)

     o	Plotted distributions of continuous and categorical risk factors. 

     o	Assessed demographics and baseline health characteristics. 

	Calculating the Globorisk Score

     o	Integrated R’s Globorisk package into Python using `rpy2`.  Estimated 10-year CVD risk for adults 40+ with no prior CVD history. 

	Risk Categorization and Validation

     o	Converted Globorisk scores into percentages and categorized individuals into:

                      Low Risk (<5%)

                      Elevated Risk (≥5%)

    o	Validated against WHO risk categories for 100 individuals:

                     Sensitivity: 0.98 

                     Specificity: 0.94 

	Data preparation to building a Semi-Supervised Learning (SSL) Framework

    o	Split dataset into labeled and unlabeled portions.

    o	Scale features (StandardScaler) and handle missing values (SimpleImputer).

	Hyperparameter tuning

    o	Run grid search for RF, XGB, MLP, and SVC.

    o	Select best estimators per model.

	Baseline evaluation

    o	Train tuned models on labeled training data.

    o	Model calibration

    o	Evaluate on a held-out test set.

	Self-training

    o	Iteratively pseudo-label unlabeled samples where predicted confidence ≥ 0.99.

    o	Add pseudo-labeled samples back to the training pool.

    o	Repeat up to 15 iterations or until no new samples meet threshold.

	Comparison \& visualization

    o	Compare baseline vs SSL performance.

    o	Generate barplots of metrics, iteration history plots, and confusion matrices.

This approach demonstrates how ML can complement conventional epidemiological models by extending CVD risk stratification to populations not traditionally covered.


**EDA**
The age distribution shows that majority participants are the younger with a slightly skewed distribution with fewer elderly. Mean age is 34 ± 13.  Total Cholesterol, has a mean of 139.1 ± 36.3 mg/dl where majority participants have a normal <200mg/dl cholesterol level. The Average Systolic Blood Pressure also shows a normal distribution with a mean of 121.4 ±18.6 mmHg. 


<img width="975" height="333" alt="image" src="https://github.com/user-attachments/assets/275bd21f-a02c-40fc-a78b-22b8491dff1c" />


The CVD risk Score across predictor variables, females have slightly lower CVD risk scores compared to males. Both smoking and diabetes status are strongly associated with elevated CVD risk scores where smokers and diabetes individuals have higher median scores. There are also positive correlations between age, systolic blood pressure and cholesterol level, where a relatively increased CVD risk score was seen in older age groups, with higher systolic blood pressure and elevated total cholesterol levels.

<img width="975" height="316" alt="image" src="https://github.com/user-attachments/assets/994d0b39-fe3a-4be1-a5cb-e3540fe8a875" />
<img width="975" height="326" alt="image" src="https://github.com/user-attachments/assets/90ab6ecc-8c2c-4db0-8372-5c80f5f36e47" />


Since utilization of the Globorisk model was not applicable for individuals aged below 40, most of our dataset, remained unlabeled for CVD risk. A semi-supervised learning approach was used to label the remain data. 

<img width="707" height="415" alt="image" src="https://github.com/user-attachments/assets/e187c3a6-36ce-4cbe-849e-9a5ecd1cb108" />


MLP performance outstand others with consistently high class-wise performance where it achieved F1 score of 0.99 and 0.98 for the negative class and for the positive class respectively. This result confirms that the self-training approach is a powerful tool for CVD risk labeling in the presence of small labeled data. 
<img width="725" height="441" alt="image" src="https://github.com/user-attachments/assets/0adbf76d-fc0f-45f4-92c4-5bd3e4d18f23" />

<img width="406" height="391" alt="image" src="https://github.com/user-attachments/assets/09e73e18-c8fd-4928-bf0a-1c2b5929dd95" />




