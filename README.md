Differential Privacy in Healthcare: Assessing Privacy Risks in Data with Laplace and Gaussian Mechanism Approaches

1. Project Description
This project implements and evaluates Differential Privacy (DP) on a large-scale healthcare dataset containing over 318,000+ patient admission records. The goal is to measure how effectively the Laplace Mechanism (ε-DP) and the Gaussian Mechanism ((ε, δ)-DP) protect sensitive patient information while maintaining the utility of statistical queries.
Both mechanisms are applied to several real-world health statistics such as BMI, Admission Deposit, Fractional Counts, and Average Stay Duration, and their performance is compared using accuracy, RMSE, and percentage error.

2. Key Features and Goals
Data Preprocessing and Feature Engineering

Exploratory Data Analysis (EDA)

Differential Privacy Implementation on Queries:
Laplace Mechanism for pure ε-DP
Gaussian Mechanism for (ε, δ)-DP

Performance Comparison:
Accuracy, RMSE, Average Percentage Error over 1000 noise samples

Privacy Robustness Test:
Re-identification attack simulation and validating that noise scale >= impact of one record

3. Data Overview
<img width="1076" height="1110" alt="image" src="https://github.com/user-attachments/assets/ab49a1e8-e9a3-49c0-93de-f3093cbe7646" />

4. Methodology & Key Findings
Data Preprocessing and Feature Engineering:
Random value generation for Age and Stay columns
Creation of synthetic continuous features (BMI, height, weight) based on Age
Outlier capping with the IQR method
Label encoding for Type of Admission and Severity of Illness
Filtering cohorts for targeted DP queries

Exploratory Data Analysis (EDA):
To understand distributions, detect inconsistencies, and identify key patterns in patient demographics and hospital stay behavior

Differential Privacy Query Results:
Queries tested under both Laplace and Gaussian mechanisms:
Query 1 - Average stay duration for patients with more than 5 visitors
Query 2 - Average BMI for patients in different age groups
Query 3 - Fractions of patients with unique combinations
Query 4 - Minimum Admission Deposit over Hospital Code

Key Conclusion:
Laplace Mechanism outperformed Gaussian across almost all metrics.
It produced lower RMSE, lower error, and higher accuracy for most queries.
Gaussian performed poorly on continuous queries with small sensitivity.

Privacy Validation (Attack Simulation):
Query 1 - Confirmed strong privacy protection: the attacker’s maximum possible influence was only 0.0027, while the Laplace noise scale was 0.0160, ensuring successful anonymization.
Query 2 - Confirmed strong DP protection: the attacker’s maximum influence was only 0.00027, while the Laplace noise scale remained 0.0110, ensuring that the target patient’s presence stayed fully hidden.
Query 3 - Confirmed strong privacy protection: the attacker’s maximum possible influence was only 0.0000031403, while the Laplace noise scale was 0.0000104678, ensuring successful anonymization.
Query 4 - Confirmed strong DP protection: the attacker’s maximum possible influence was only 2.51378651, while the Laplace noise scale was 6.28446628, ensuring successful anonymization.

5. Steps to Run the Code:
Prerequisites
You will need the following libraries installed: pip install pandas numpy matplotlib seaborn
Download the Jupyter Notebook
Download the dataset
Execute the Notebook: Run all cells in Final_Project_Code.ipynb sequentially to perform data cleaning, analysis, differential privacy implementation, performance evaluation, and attack simulation.
