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

      During the data preprocessing phase, several records regarding national macroeconomics were missing key metrics (Average_Monthly_Income). However, the records retained unique identifier anchors within the `Cost_of_Living` and `Year` columns:

      Australia (2012): Identified by a specific cost of living threshold of 4692.15.

      Mexico (2006): Identified by a specific cost of living threshold of 4219.26.

      Instead of using statistical imputation (such as mean/median filling or linear interpolation), the missing fields were deterministically restored via primary source tracking to ensure 100% data integrity.

      Australia (2012) with Cost_of_Living (4692.15), fill 3641.94 into Average_Monthly_Income.
      
      Mexico (2006) with Cost_of_Living (4219.26), fill 6124.70 into Average_Monthly_Income.

      The reference values were verified and cross-referenced from the global economic benchmark dataset "Cost of Living and Income Extended" (compiled from historical records of Numbeo and The World Bank macro indicators).

      References: https://fr.scribd.com/document/809245091/Cost-of-Living-and-Income-Extended1-Copy

IV. Descriptive Statistics

   The table presents the descriptive statistics for two variables: Average Monthly Income (Average_Monthly_Income) and Cost of Living (Cost_of_Living), with a sample size of N = 199. 
   
   1. Average Monthly Income (Average_Monthly_Income)
   
   Sample Size (Count): 199 observations
   
   Central Tendency:
   
      Mean: $4,250.39
   
      Median: $4,266.46
   
      Mode: N/A (No repeated values identified)
   
      Interpretation: The mean and median are nearly identical, indicating a balanced distribution around the central value of $4,250.39.
   
   Dispersion / Variability:
   
      Standard Deviation: $2,121.27
   
      Sample Variance: $4,499,804.91
   
      Standard Error: $150.37
   
      Range: $7,441.82 (Minimum = $534.74, Maximum = $7,976.56)
   
      Interpretation: The large standard deviation indicates significant variance in income levels among the surveyed individuals.
   
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
   
<img width="457" height="231" alt="Ảnh màn hình 2026-07-31 lúc 00 00 55" src="https://github.com/user-attachments/assets/c2dda717-8072-488b-a966-91cad0e3b91e" />

   3. Scatter Plot Findings

<img width="665" height="488" alt="Ảnh màn hình 2026-07-31 lúc 00 01 07" src="https://github.com/user-attachments/assets/07995112-1115-49c4-b318-1334f091e588" />

   Looking at the scatter chart:

   No Relationship: The dots are spread evenly everywhere. High income does not mean high living costs, and low income does not mean low living costs.

   Random Pattern: A person earning $7,000 can have a low living cost ($1,000), while a person earning $1,000 can have a high living cost ($6,000).

   Predictability: You cannot predict a person's living costs based on their income alone.

V. Key Insights

   Insight 1: Tight Global Disposable Income Margin
  
   Global mean monthly income ($4,250.39) exceeds mean monthly living expenses ($3,705.13) by approximately $545.26. However, large standard deviations in both income ($2,121.27) and living costs ($1,982.22) reveal that a significant portion of observations sit near or below parity, where essential expenses absorb nearly 100% of earnings.

   Insight 2: Regional Disparities in Living Affordability

  Europe and Oceania have healthier disposable buffers, as their average incomes are considerably above the regional living costs. In contrast, North America demonstrates a significantly tighter equilibrium between the average monthly income and cost of living, which suggests that there is a greater degree of financial strain in relation to earnings in these sample recordings.

   Insight 3: Regional Financial Buffers

   Cash Flow Retention: Europe Retains Europe continues to be the world’s strongest region for financial balance. The significant difference between the highest total income and optimal living costs has led to a big cash surplus (Balance) in this region, which is more than any other location.

   Cost of Living Pressure Straining North America: North America is experiencing a very corrosive financial equilibrium. The total revenue earned is huge, similar to Europe and Asia, but the rising high living costs have eaten into the real surplus (Balance) to a tiny nominal level, virtually nothing.

   Asia Drives Big Wealth Build-Up: Asia is putting itself on the map as a vibrant, fast-changing financial economy. The region has very high domestic living expenditures but a significant total surplus (Balance), the second highest in the world after Europe.

   Ability to keep cash in smaller markets Africa, South America and Oceania are on a lesser scale of cash flow due to the distinctive characteristics of their local economies. But the financial buffer (balance) of these three regions is strikingly robust and similar, which shows how well households regulate their spending to conserve cash.

<img width="688" height="467" alt="Ảnh màn hình 2026-07-31 lúc 00 01 17" src="https://github.com/user-attachments/assets/9e53a364-9720-4946-86d7-bb9fdb2c6a6a" />

<img width="464" height="169" alt="Ảnh màn hình 2026-07-31 lúc 00 01 23" src="https://github.com/user-attachments/assets/7113bc3d-d0d5-43e6-ba1f-7d37d7777a7e" />

   
VI. How to Reproduce Analysis in Excel (macOS / Windows)

   1. Load Raw File: Open `01_Cost of Living.xlsx` in Microsoft Excel.

   2. Launch Power Query:. 

      Select dataset range  -> Click Data tab -> Click Get Data (Power Query) -> From Table/Range.

   3. Execute Cleaning Pipeline:

     Remove Duplicates: Select all columns → Navigate to the Data tab → Click Remove Duplicates to eliminate any redundant records.
     
     Fill Missing Metadata: Locate the missing row entries for Mexico (2006) → Input North America respectively into the blank cells of the Region column.
     
     Deterministic Income Restoration: Scan the Average_Monthly_Income column for missing (null) values and restore their precise historical figures mapped to their specific cost anchors:
     
        Input 3641.94 for the record with a cost of living of 4692.15 (Australia).
     
        Input 6124.70 for the record with a cost of living of 4219.26 (Mexico).

   6. Generate Output & Statistics:
 
      Click Close & Load to push the clean table to a new worksheet.

      Go to Data -> Data Analysis -> Select Descriptive Statistics with Input Range ($C$1:$D$200) -> Click Label in first row and Summary Statistics (95%) -> Click Ok

   7. Make Scatter Chart

      Highlight all rows including both columns of Average Monthly Income and Cost of Living -> Click Insert and choose Scatter Chart in Recommended Charts

   8. Steps to Create the Balance Column in Excel:

      Label New Column: Navigate to the first cell of the next empty column (e.g., cell F1) and type the header Balance.

      Enter Financial Formula: In the cell directly below the header (cell F2), input the calculation formula: =C2-D2 (where C2 represents Income and D2 represents Cost of Living).

      Apply Across Dataset: Hover your mouse over the bottom-right corner of cell F2 until a black plus sign (+) appears, then double-click to automatically fill the formula down all 199 rows.

   9. Steps to create a PivotTable & PivotChart in Excel:

      Select the data range: Select the entire clean data table (including the header row from the first row).

      Initialize the tool: Go to the Insert tab → Click on PivotChart (or select the PivotTable & PivotChart option).

      Set the analysis axis: In the right-hand pane, drag the Region field and drop it into the Axis (Categories) box to create the horizontal axis.

      Add financial indicators: Drag the Average_Monthly_Income, Cost_of_Living, and Balance fields into the Values ​​box.

      Change the calculation function: Right-click on each field in the Values ​​box → Select Value Field Settings → Change the default from Count or Average to Sum to accurately match the 3-column chart.
