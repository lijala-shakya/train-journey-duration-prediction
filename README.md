# train-journey-duration-prediction

ML model with comparisons to predict Railways journey duration



A machine learning project to predict Indian Railways journey duration based on route and schedule data.



\## Project Overview

This project builds a predictive model that estimates total journey duration using features like distance, number of stops, and fare class.



**Dataset**

&#x20;\*\*Source:\*\* Indian Railways Schedule Data

&#x20;\*\*Records:\*\* 186,074 stop-level entries

&#x20;\*\*Trains:\*\* 11,113 unique train journeys

&#x20;\*\*Features:\*\* Station codes, arrival/departure times, distances, fares



**Problem Statement**

Given route information for a train journey, predict the total journey duration in minutes.

&#x20;\*\*Type:\*\* Supervised Regression

&#x20;\*\*Target Variable:\*\* Journey\_Duration\_Minutes



**Project Structure**

train-journey-duration-prediction/

│

├── Dataset1.csv                 

├── train\_journey\_ml.ipynb       

├── requirements.txt             

└── README.md                    



**Setup and Installation**



1\. Clone the repository:

git clone https://github.com/lijala-shakya/train-journey-duration-prediction.git

cd train-journey-duration-prediction



2\. Install dependencies:

pip install -r requirements.txt



3\. Open the notebook:

jupyter notebook train\_journey\_ml.ipynb





**Project Pipeline**



\### Level 1 — Understanding the Data

\-> Loaded 186,074 records across 12 columns

\-> Identified 11,113 unique trains

\-> Performed data quality audit — zero missing values



\### Level 2 — Data Cleaning and Feature Engineering

\-> Converted HH:MM:SS times to total minutes from midnight

\-> Calculated journey duration per train as target variable

\-> Engineered features: Total Distance, Total Stops, Fare averages, Dist Per Stop



\### Level 3 — Exploratory Data Analysis

\-> Visualized distance vs duration relationships

\-> Correlation heatmap across all features

\-> Pivot table of stops per train



\### Level 4 — Model Training and Evaluation

\-> Split data: 80% train / 20% test

\-> Applied StandardScaler for Linear Regression and KNN

\-> Trained and compared 3 models



\### Level 5 — Clustering

\-> Applied KMeans clustering (K=4)

\-> Identified 4 natural train categories



**Models and Results**



| Model             | MAE        | RMSE       | R²     |

|-------------------|------------|------------|--------|

| Linear Regression | 137.96 min | 221.21 min | 0.5230 |

| Decision Tree     | 53.47 min  | 134.29 min | 0.8242 |

| KNN (K=11)        | 60.43 min  | 135.65 min | 0.8207 |



\### Best Model: Decision Tree (max\_depth=8)





**Model Trade-offs**



\### Linear Regression

\-> Simple and fast, good baseline

\-> Cannot capture complex non-linear patterns

\-> Result: R² = 0.52



\### Decision Tree

\-> Handles non-linear relationships

\-> No feature scaling needed

\-> Tuned max\_depth=8 to prevent overfitting

\-> Result: R² = 0.82 (best model)



\### KNN

\-> Finds similar trains and averages duration

\-> Requires feature scaling

\-? Tuned K=11 using elbow analysis

\-> Result: R² = 0.82 (close second)



\## Clustering Results (KMeans K=4)



| Cluster   | Train Type         | Avg Distance | Avg Duration | Avg Fare |

|-----------|--------------------|-------------|-------------|---------|

| Cluster 3 | Short Local        | 52 km       | 80 min      | 151 Rs  |

| Cluster 0 | Medium Regional    | 144 km      | 216 min     | 243 Rs  |

| Cluster 2 | Long Express       | 746 km      | 908 min     | 847 Rs  |

| Cluster 1 | Ultra Long Premium | 1943 km     | 562 min     | 2052 Rs |





**Validation Results**



Within 30 minutes  : 66.1% of predictions

Within 60 minutes  : 78.4% of predictions

Within 120 minutes : 88.7% of predictions







**Key Findings**



\-> Decision Tree outperforms both Linear Regression and KNN

\-> Distance and number of stops are the strongest predictors

\-> High fare trains travel faster despite longer distances

\-> 4 natural train categories exist in Indian Railways data





**Technologies Used**



\-> Python 3

\-> Pandas — data manipulation

\-> NumPy — numerical computing

\-> Matplotlib and Seaborn — visualizations

\-> Scikit-learn — ML models

\-> Joblib — model saving







**Author**

Lijala Shakya

GitHub: https://github.com/lijala-shakya

LinkedIn: https://www.linkedin.com/in/lijala-shakya-7bb219310/

