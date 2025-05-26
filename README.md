**🔍 Project Overview**

This project explores the use of supervised machine learning techniques to classify injury severity outcomes in U.S. road traffic accidents. Utilizing the National Highway Traffic Safety Administration’s (NHTSA) Crash Report Sampling System (CRSS), we modeled injury outcomes as a binary classification problem (Minor vs. Major Injury), focusing on vehicle, environmental, and behavioral features.

**📦 Dataset**

Source: NHTSA CRSS (2016–2021)


Initial Size: 95,000+ records × 120 attributes across 4 relational tables


Final Dataset: ~37,800 filtered observations with ~30 engineered features


**Tables Used:**

**Accident:** Crash-level context (time, location, road condition)

**Vehicle:** Technical and mechanical data (impact, airbag, speed)

**Person:** Demographics and injury-related attributes

**Distraction:** Behavioral indicators (distraction types, usage context)

**⚙️ Data Processing Pipeline**


Tool Used: KNIME Analytics Platform


**Steps:**


Data Integration

**Joined tables using keys:**

CASE_ID, VEHICLE_ID, PERSON_ID


**Data Cleaning**


1.Rule-based imputation (mode/median)

2.Missing value filtering

3.Outlier handling via KNIME rule engines and math nodes


**Feature Engineering**


VEH_AGE = 2021 − model year

OVERSPEED = Travel Speed − Speed Limit

Flags: IS_COLLISION, IS_WORKZONE, SEASON (based on crash month)


**Transformation**

Binning and normalization for MLP (ANN) compatibility


**Balancing**

Class imbalance analyzed and balanced using equal size sampler and SMOTE

**🧠 Machine Learning Models**

Six classification models were trained and evaluated:


| Model               | Accuracy | AUC   |
| ------------------- | -------- | ----- |
| Logistic Regression | 0.84    | 0.784 |
| Decision Tree       | 0.76     | 0.627 |
| GBT                 | 0.82     | 0.790 |
| Random Forest       | 0.83     | 0.775 |
| Naive Bayes         | 0.87     | 0.752 |
| MLP                 | 0.78     | 0.764 |


**Top Model:** 

Naive Bayes – best balance between accuracy and interpretability.

**🔑 Key Predictors Identified**

Using feature importance analysis:

Seatbelt Usage (REST_USE)

Point of Impact (IMPACT1)

Driver Age (PERSON_AGE)

Distraction Status (DISTRACT)

Overspeeding Indicator (OVERSPEED)

Light Conditions (LGT_COND_)

Collision Type (MAN_COLL)

**📊 Technical Highlights**

Applied full CRISP-DM methodology (from business understanding to deployment)

Modular workflow developed in KNIME using visual ETL and ML nodes

Engineered key features and normalized inputs for consistent model training

**Evaluation via:**


ROC Curves

Sensitivity & Specificity

Feature Importance Scores

Comprehensive documentation maintained for variable derivation and methodology

**Outcomes**

This project served as a capstone in predictive modeling for public safety, with key learnings including:

Ensemble models (GBT, RF) perform well on structured and mixed-type data

Preprocessing and feature engineering are critical to model success

Reproducibility and explainability are essential in public policy-related modeling

Collaborative workflow management enhanced through KNIME’s visual interface
