Global Cost of Living & Income Analysis 

Part 1: Data Cleaning & EDA

Welcome to the Exploratory Data Analysis (EDA) and Data Cleaning** module for the Global Cost of Living & Income dataset (2000–2023).

This document outlines the entire data preprocessing workflow, descriptive statistical analysis, and key empirical insights prepared for macroeconomic analysis.

1. Project Overview
   
Primary Objective: To analyze the relationship between Average Monthly Income and Cost of Living across various countries over time, perform data cleaning (handling duplicates, missing values, and attribute corrections), and extract summary statistics.
Scope: 199 valid observations across 12 countries representing 6 global regions.
Toolstack: Microsoft Excel / Power Query.

2. Dataset Structure

The original raw dataset (`01_Cost of Living.xlsx`) contains 201 rows and 5 primary feature columns:

•	Country (Categorical (Text)): The name of the country where the data was recorded.

•	Region (Categorical (Text)): The geographical region to which the country belongs 

•	Year (Numerical (Integer)): The year when the data was recorded (2000 – 2023).

•	Average_Monthly_Income (Numerical (Decimal)): The average monthly income of individuals in USD.

•	Cost_of_Living (Numerical (Decimal)): The average monthly cost of living in USD, including essentials like housing, food, and utilities.

3. Data Cleaning Pipeline

The dataset was processed through Power Query to ensure data integrity:

1. **Schema Validation & Data Type Casting:**
   * Text features (`Country`, `Region`) set to **Text**.
   * Temporal feature (`Year`) set to **Integer**.
   * Numerical features (`Average_Monthly_Income`, `Cost_of_Living`) set to **Decimal**.

2. **Duplicate Removal:**
   * Identified and deleted **2 full duplicate entries**:
     * *China (2022)*
     * *Mexico (2010)*
   * Cleaned dataset size reduced from **201 to 199 rows**.

3. **Missing Value Imputation & Region Updates:**
   * **Region Alignment:** Standardized missing/customized region attributes (specifically assigning *Mexico 2006* and *Mexico 2000/2003* to **North America**).
   * **Missing Income Imputation:**
     * Identified 2 missing values in `Average_Monthly_Income` (*Australia 2012* and *Mexico 2006*).
     * Imputed missing entries using the overall **Median Income ($4,266.46)** to preserve row observations without skewing distribution variance or losing corresponding cost-of-living data.

---

## 📈 4. Descriptive Statistics

Summary metrics computed on the cleaned dataset ($N = 199$):

| Statistical Metric | Average Monthly Income (USD) | Cost of Living (USD) |
| :--- | :---: | :---: |
| **Count ($N$)** | $199$ | $199$ |
| **Mean** | $\$4,244.19$ | $\$3,705.13$ |
| **Median** | $\$4,266.46$ | $\$3,688.09$ |
| **Standard Deviation** | $\$2,116.64$ | $\$1,982.22$ |
| **Minimum** | $\$534.74$ | $\$464.49$ |
| **25th Percentile (Q1)** | $\$2,376.08$ | $\$1,882.44$ |
| **75th Percentile (Q3)** | $\$6,069.00$ | $\$5,376.12$ |
| **Maximum** | $\$7,976.56$ | $\$6,981.02$ |

---

## 💡 5. Key Insights

* **Insight 1: Tight Global Disposable Income Margin**
  Global mean monthly income ($\$4,244.19$) exceeds mean monthly living expenses ($\$3,705.13$) by approximately $14.5\%$. However, large standard deviations in both income ($\$2,116.64$) and living costs ($\$1,982.22$) reveal that a significant portion of observations sit near or below parity, where essential expenses absorb nearly $100\%$ of earnings.

* **Insight 2: Regional Disparities in Living Affordability**
  * **Europe** and **Oceania** maintain healthier disposable buffers, with average incomes (Europe: $\$4,477.26$, Oceania: $\$4,535.57$) comfortably above regional living costs.
  * **North America** exhibits a much tighter equilibrium between average monthly income ($\$3,774.13$) and cost of living ($\$3,750.07$), indicating higher financial strain relative to earnings in these sample records.

---

## 🛠️ 6. How to Reproduce Analysis in Excel (macOS / Windows)

1. **Load Raw File:** Open `01_Cost of Living.xlsx` in Microsoft Excel.
2. **Launch Power Query:**
   * Select dataset range $\rightarrow$ Navigate to **Data** tab $\rightarrow$ Click **Get Data (Power Query)** / **From Table/Range**.
3. **Execute Cleaning Pipeline:**
   * Select all columns $\rightarrow$ Right-click $\rightarrow$ **Remove Duplicates**.
   * Fill blank `Region` cells for Mexico with `North America`.
   * For `Average_Monthly_Income`, find `null` values $\rightarrow$ Replace with `4266.46`.
4. **Generate Output & Statistics:**
   * Click **Close & Load** to push the clean table to a new worksheet.
   * Go to **Data** $\rightarrow$ **Data Analysis** $\rightarrow$ Select **Descriptive Statistics** to export summary statistics.
