# Differential Privacy in Healthcare: Assessing Privacy Risks in Data with Laplace and Gaussian Mechanism Approaches

## Contributors

-   Sara Husketh
-   Jamie Vazquez-Madera
-   Aditya Sreenath
-   Siri Chandana Katari

## Project Description

This project implements and evaluates Differential Privacy (DP) on a large-scale healthcare dataset containing over 318,000+ patient admission records. The goal is to measure how effectively the Laplace Mechanism (ε-DP) and the Gaussian Mechanism ((ε, δ)-DP) protect sensitive patient information while maintaining the utility of statistical queries. Both mechanisms are applied to several real-world health statistics such as BMI, Admission Deposit, Fractional Counts, and Average Stay Duration, and their performance is compared using accuracy, RMSE, and percentage error.

## Key Features and Goals

- Data Preprocessing and Feature Engineering
- Exploratory Data Analysis (EDA)
- Differential Privacy Implementation on Queries:
Laplace Mechanism for pure ε-DP
Gaussian Mechanism for (ε, δ)-DP
- Performance Comparison:
Accuracy, RMSE, Average Percentage Error over 1000 noise samples
- Privacy Robustness Test:
Re-identification attack simulation and validating that noise scale >= impact of one record

## Data Overview

![alt text](<Screenshot 2025-12-08 200759.png>)

## Methodology & Key Findings

### Data Preprocessing and Feature Engineering:
- Random value generation for Age and Stay columns
- Creation of synthetic continuous features (BMI, height, weight) based on Age
- Outlier capping with the IQR method
- Label encoding for Type of Admission and Severity of Illness
- Filtering cohorts for targeted DP queries

### Exploratory Data Analysis (EDA):
To understand distributions, detect inconsistencies, and identify key patterns in patient demographics and hospital stay behavior

### Differential Privacy Query Results:
Queries tested under both Laplace and Gaussian mechanisms:
- Query 1 - Average stay duration for patients with more than 5 visitors
- Query 2 - Average BMI for patients in different age groups
- Query 3 - Fractions of patients with unique combinations
- Query 4 - Minimum Admission Deposit over Hospital Code

### Key Conclusion:
Laplace Mechanism outperformed Gaussian across almost all metrics.
It produced lower RMSE, lower error, and higher accuracy for most queries.
Gaussian performed poorly on continuous queries with small sensitivity.

### Privacy Validation (Attack Simulation):
Across all four queries, we simulated re‑identification attacks where an adversary tries to determine whether a specific patient is included in the dataset. In each case, the attacker attempts to do this by measuring how much the output of a query (such as an average, a fraction, or a minimum value) would change if the target patient’s data were removed.

- Query 1 (Average Stay Duration):
The attacker tried to detect whether adding or removing one extreme patient would noticeably shift the average stay duration. However, the differential privacy noise was large enough that the attacker’s influence was fully hidden.

- Query 2 (BMI by Age‑Group):
The attack attempted to identify whether an unusually high‑BMI patient belonged to a specific age group by comparing the average with and without that patient. The DP noise again dominated the potential influence, preventing any meaningful signal from leaking.

- Query 3 (Fractional Count):
This attack focused on whether altering the presence of a single patient would visibly change the fraction of patients with a particular attribute. Because this query’s sensitivity is extremely small, the DP mechanism easily masked the attacker’s maximum possible impact, ensuring strong privacy protection.

- Query 4 (Minimum Deposit per Hospital):
In this case, the attacker attempted to exploit how much one patient could shift a hospital’s minimum deposit value. Even though this metric can be more sensitive, the DP noise was still scaled adequately to prevent the attacker from learning whether any individual record influenced the result.

## Steps to Run the Code:

- Prerequisites - You will need the following libraries installed: pip install pandas numpy matplotlib seaborn
- Download the Jupyter Notebook
- Download the dataset
- Execute the Notebook: Run all cells in Final_Project_Code.ipynb sequentially to perform data cleaning, analysis, differential privacy implementation, performance evaluation, and attack simulation.
