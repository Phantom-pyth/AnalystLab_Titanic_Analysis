# AnalystLab_Titanic_Analysis


> Exploratory Data Analysis (EDA) to identify the key factors that determined passenger survival on the RMS Titanic.



 Project Overview

This project performs a comprehensive analysis of the Titanic passenger dataset containing 891 records across 12 features. The goal is to uncover which passenger characteristics most significantly influenced survival  providing insights for historians, data scientists, and ML practitioners building classification models.



 Repository Structure


titanicsurvivalanalysis/
TitanicDataset.csv                Original raw dataset
Titanic_Cleaned.csv                Cleaned & engineered dataset (ready for ML)
Titanic_Survival_Analysis.ipynb    Full Jupyter Notebook (EDA + visualizations)
Titanic_Insight_Report.docx        Insight Summary Report (Word document)
README.md                          This file


 Dataset Description

 Property  Details 

 Source  TitanicDataset.csv 
 Rows  891 
 Columns  12 
 Target Variable  Survived (0 = Died, 1 = Survived) 
 Overall Survival Rate  38.4% 

 Features

 Feature  Type  Description  Missing 

 PassengerId  Identifier  Unique passenger ID  None 
 Survived  Binary  Survival outcome (target)  None 
 Pclass  Ordinal  Passenger class (1, 2, 3)  None 
 Name  Identifier  Passenger name  None 
 Sex  Categorical  male / female  None 
 Age  Numeric  Age in years  177 (19.9%) 
 SibSp  Numeric  Siblings/spouses aboard  None 
 Parch  Numeric  Parents/children aboard  None 
 Ticket  Identifier  Ticket number  None 
 Fare  Numeric  Ticket fare paid  None 
 Cabin  Categorical  Cabin number  687 (77.1%) 
 Embarked  Categorical  Port of embarkation (S/C/Q)  2 (0.2%) 



 Data Cleaning Summary

 Issue  Action  Justification 

 Age (177 missing)  Median imputation  Robust to rightskewed distribution 
 Cabin (687 missing, 77%)  Column dropped  Too sparse  imputation unreliable 
 Embarked (2 missing)  Mode imputation (S)  Negligible impact; S is 72.4% of data 
 PassengerId, Name, Ticket  Dropped  Identifiers with no predictive value 

 Engineered Features
 Sex_enc  Male=0, Female=1 (for correlation analysis)
 Embarked_enc  S=0, C=1, Q=2
 FamilySize  SibSp + Parch + 1
 IsAlone  1 if FamilySize == 1, else 0



 Analysis Summary

 Part 1  Data Loading & Inspection
 891 records, 12 columns; 3 columns with missing values identified
 PassengerId confirmed unique; no duplicate passengers

 Part 2  Data Cleaning
 Missing values handled with justified imputation strategies
 Cabin dropped (77% missing); identifiers removed
 4 new features engineered

 Part 3  Exploratory Data Analysis
 Univariate: Histograms, boxplots for numeric features; bar charts for categorical
 Bivariate: Survival rate by sex, class, age, fare, embarkation, and family size

 Part 4  Correlation & Feature Importance
 Correlation matrix computed; heatmap visualized
 Features ranked by absolute correlation with Survived

 Part 5  Insights & Recommendations
 7 key insights with evidence and recommendations



 Key Insights

   Insight  Correlation (r) 

 1  Sex is the dominant survival factor  women 74.2% vs men 18.9%  0.54 
 2  Passenger class created a clear survival hierarchy (1st: 63%, 3rd: 24%)  0.34 
 3  Higher fare strongly associates with survival  survivors paid 2x more  0.26 
 4  Travelling alone reduced survival odds (30.4% vs 50.6% for families)  0.20 
 5  Cherbourg passengers had highest survival rate (55.4%)  driven by class mix  0.11 
 6  Children under 10 benefited most from "women and children first" protocol   
 7  Class imbalance (62/38 split) requires AUC/F1 metrics, not just accuracy 



 🛠️ Technologies Used

 Python 3.x
 Pandas  data loading, cleaning, manipulation
 NumPy  numerical operations
 Matplotlib  base plotting
 Seaborn  statistical visualizations and heatmaps
 Jupyter Notebook  interactive analysis environment



 Getting Started

 Prerequisites

bash
pip install pandas numpy matplotlib seaborn jupyter


 Run the Analysis

bash
 Clone the repository
git clone https://github.com/YOUR_USERNAME/titanicsurvivalanalysis.git
cd titanicsurvivalanalysis

 Launch the Jupyter Notebook
jupyter notebook Titanic_Survival_Analysis.ipynb




 Feature Importance for ML

 Tier  Features  Recommendation 

 High importance  Sex_enc, Pclass, Fare  Always include 
 Moderate importance  IsAlone, FamilySize  Include; test binned vs raw 
 Low importance  Embarked_enc, Parch, Age  Test inclusion 
 Engineered (recommended)  IsChild (Age < 10), log(Fare)  Engineer for better signal 
 Drop / redundant  SibSp+Parch (if FamilySize used), raw Cabin  Omit 

> Note: This dataset has a 62/38 class imbalance. Use F1score, Precision, Recall, and AUCROC  not raw accuracy  to evaluate model performance.



 Outputs

 Titanic_Cleaned.csv  Analysisready dataset with imputed values and engineered features
 Titanic_Survival_Analysis.ipynb  Complete reproducible analysis notebook
 Titanic_Insight_Report.docx  Executive insight summary with 7 detailed insights and recommendations



 Contributing

Pull requests are welcome. For major changes, please open an issue first.



 License

This project is open source.
