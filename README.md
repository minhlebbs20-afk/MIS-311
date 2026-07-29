Global Cost of Living & Income Analysis 

Part 1: Data Cleaning & EDA

   Welcome to the Exploratory Data Analysis (EDA) and Data Cleaning module for the Global Cost of Living & Income dataset (2000–2023).

   This document outlines the entire data preprocessing workflow, descriptive statistical analysis, and key empirical insights prepared for macroeconomic analysis.

I. Project Overview
   
   Primary Objective: To analyze the relationship between Average Monthly Income and Cost of Living across various countries over time, perform data cleaning (handling duplicates, missing values, and attribute corrections), and extract summary statistics.

   Scope: 199 valid observations across 12 countries representing 6 global regions.

   Toolstack: Microsoft Excel / Power Query.

II. Dataset Structure

The original raw dataset (`01_Cost of Living.xlsx`) contains 201 rows and 5 primary feature columns:

•	Country (Categorical (Text)): The name of the country where the data was recorded.

•	Region (Categorical (Text)): The geographical region to which the country belongs 

•	Year (Numerical (Integer)): The year when the data was recorded (2000 – 2023).

•	Average_Monthly_Income (Numerical (Decimal)): The average monthly income of individuals in USD.

•	Cost_of_Living (Numerical (Decimal)): The average monthly cost of living in USD, including essentials like housing, food, and utilities.

III. Data Cleaning Pipeline

   The dataset was processed through Power Query to ensure data integrity:

   1. Schema Validation & Data Type Casting:

      Text features (`Country`, `Region`) set to Text.

      Temporal feature (`Year`) set to Integer.

      Numerical features (`Average_Monthly_Income`, `Cost_of_Living`) set to Decimal.

   2. Duplicate Removal:

      Identified and deleted 2 full duplicate entries:

      China (2022)

      Mexico (2010)

      Cleaned dataset size reduced from 201 to 199 rows.

   3. Missing Value Imputation & Region Updates:

      Region Alignment: Standardized missing/customized region attributes (specifically assigning Mexico 2006 and Mexico 2000/2003 to North America).

      Missing Income Imputation:

      Identified 2 missing values in `Average_Monthly_Income` (Australia 2012 and Mexico 2006).

      Imputed missing entries using the overall Median Income ($4,266.46) to preserve row observations without skewing distribution variance or losing corresponding cost-of-living data.

IV. Descriptive Statistics

   The table presents the descriptive statistics for two variables: Average Monthly Income (Average_Monthly_Income) and Cost of Living (Cost_of_Living), with a sample size of N = 199. 
   
   1. Average Monthly Income (Average_Monthly_Income)
   
   Sample Size (Count): $199$ observations
   
   Central Tendency:
   
      Mean: $4,244.19
   
      Median: $4,266.46
   
      Mode: $4,266.46
   
      Interpretation: The mean and median are nearly identical, indicating a balanced distribution around the central value of $4,244.19.
   
   Dispersion / Variability:
   
      Standard Deviation: $2,116.64
   
      Sample Variance: $4,480,156.55
   
      Standard Error: $150.04
   
      Range: $7,441.82 (Minimum = $534.74, Maximum = $7,976.56)
   
      Interpretation: The large standard deviation indicates significant variance in income levels among the surveyed individuals.
   
   Distribution Shape:
   
      Skewness: $0.06 (Close to $0$, indicating a symmetric distribution with a negligible right-skew).
   
      Kurtosis: $-1.17 (Negative kurtosis indicates a platykurtic distribution—flatter peak and lighter tails than a normal distribution).
   
   2. Cost of Living (Cost_of_Living)
   
   Sample Size (Count): 199 observations
   
   Central Tendency:
   
      Mean: $3,705.13
   
      Median: $3,688.09
   
      Mode: N/A (No repeated values identified)
   
      Interpretation: The average cost of living is $3,705.13$, closely aligning with the median value of $3,688.09.
   
   Dispersion / Variability:
   
      Standard Deviation: $1,982.22
   
      Sample Variance: $3,929,182.86
   
      Standard Error: $140.52
   
      Range: $6,516.53 (Minimum = $464.49, Maximum = $6,981.02)
   
   Distribution Shape:
   
      Skewness: $-0.04 (Nearly symmetric, negligible left-skew).
   
      Kurtosis: $-1.27 (Platykurtic distribution with a flat top).
   
<img width="405" height="213" alt="Descriptive Statistics" src="https://github.com/user-attachments/assets/6a5155a4-7bc6-4b01-8c27-30d811661018" />

   3. Scatter Plot Findings

      <img width="691" height="461" alt="Scatter Chart" src="https://github.com/user-attachments/assets/b5f97f03-78db-47eb-a9a5-2eeeab407522" />

   Looking at the scatter chart:

   No Relationship: The dots are spread evenly everywhere. High income does not mean high living costs, and low income does not mean low living costs.

   Random Pattern: A person earning $7,000 can have a low living cost ($1,000), while a person earning $1,000 can have a high living cost ($6,000).

   Predictability: You cannot predict a person's living costs based on their income alone.

V. Key Insights

   Insight 1: Tight Global Disposable Income Margin
  
   Global mean monthly income ($4,244.19) exceeds mean monthly living expenses ($3,705.13) by approximately $14.5. However, large standard deviations in both income ($2,116.64) and living costs ($1,982.22) reveal that a significant portion of observations sit near or below parity, where essential expenses absorb nearly $100 of earnings.

   Insight 2: Regional Disparities in Living Affordability

   Europe and Oceania maintain healthier disposable buffers, with average incomes (Europe: $4,477.26, Oceania: $4,535.57$) comfortably above regional living costs.

   North America exhibits a much tighter equilibrium between average monthly income ($3,774.13$) and cost of living ($3,750.07), indicating higher financial strain relative to earnings in these sample records.

VI. How to Reproduce Analysis in Excel (macOS / Windows)

   1. Load Raw File: Open `01_Cost of Living.xlsx` in Microsoft Excel.

   2. Launch Power Query:. 

      Select dataset range  -> Click Data tab -> Click Get Data (Power Query) -> From Table/Range.

   4. Execute Cleaning Pipeline:**

      Select all columns -> Right-click -> Remove Duplicates.

      Fill blank `Region` cells for Mexico with `North America`.

      For `Average_Monthly_Income`, find `null` values -> Replace with `4266.46`.

   6. Generate Output & Statistics:
 
      Click Close & Load to push the clean table to a new worksheet.

      Go to Data -> Data Analysis -> Select Descriptive Statistics with Input Range ($C$1:$D$200) -> Click Label in first row and Summary Statistics (95%) -> Click Ok

   7. Make Scatter Chart

      Highlight all rows including both columns of Average Monthly Income and Cost of Living -> Click Insert and choose Scatter Chart in Recommended Charts

