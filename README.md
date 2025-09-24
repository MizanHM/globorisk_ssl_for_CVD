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






