# Young People BMI Exploratory Data Analysis

**Date:** October 20, 2026

## Project Overview

This project explores survey data from 1,010 young people to examine which demographic and lifestyle characteristics are associated with differences in body mass index (BMI). Using Python, pandas, NumPy, Matplotlib, and Seaborn, the analysis prepares the body measurements, calculates BMI, examines data quality, and compares BMI distributions across selected respondent characteristics.

The project focuses on making documented data-quality decisions before comparing groups and communicating the results as descriptive associations rather than causal relationships.

## Objectives

- Assess the structure and completeness of the selected variables.
- Identify and document missing values in `Height` and `Weight`.
- Examine the distributions of `Height` and `Weight` and identify potential outliers.
- Calculate BMI from weight and height after data preparation.
- Compare BMI across 15 categorical demographic and lifestyle variables.
- Measure the association between BMI and `Age` and `Number of siblings` using Spearman correlation.
- Summarize the findings while acknowledging the limitations of the survey and the data-quality decisions.

## Dataset

The analysis uses `responses.csv`, from the **Young People Survey** dataset on Kaggle:

https://www.kaggle.com/datasets/miroslavsabo/young-people-survey

The dataset contains **1,010 survey responses and 150 columns**. The notebook focuses on 19 variables that could plausibly relate to BMI:

- **Body measurements:** `Height`, `Weight`
- **Demographics:** `Age`, `Number of siblings`, `Gender`, `Education`, `Only child`, `Village - town`, `House - block of flats`
- **Health and lifestyle:** `Smoking`, `Alcohol`, `Internet usage`, `Healthy eating`, `Spending on healthy eating`, `Eating to survive`, `Health`, `Active sport`, `Passive sport`, `Adrenaline sports`
- **Derived variable:** `BMI`

The remaining survey columns, including music, movies, hobbies, phobias, personality, opinions, and spending preferences, are not analyzed in this project.

The survey was answered in 2013 by people of Slovak nationality between 15 and 30 years old. The sample is a convenience sample, so the findings should not be generalized to other populations.

## Tools and Libraries

- **Python:** programming language used for the analysis.
- **pandas:** used to load, inspect, clean, transform, and summarize the dataset.
- **NumPy:** used for numerical calculations.
- **Matplotlib:** used to create visualizations.
- **Seaborn:** used for statistical visualizations, including boxplots and distribution plots.
- **Jupyter Notebook:** used to organize the analysis, document decisions, and present the results.

## Project Structure

```text
young-people-bmi-analysis/
├── data/
│   └── responses.csv
├── notebooks/
│   └── young_people_bmi_eda.ipynb
└── README.md
```

- `data/`: contains the survey dataset.
- `notebooks/`: contains the Jupyter Notebook with the analysis.
- `README.md`: documents the project, methodology, findings, and limitations.

## Analysis Workflow

1. **Data Loading:** loaded `responses.csv` and reviewed the number of observations and variables.
2. **Variable Selection:** selected 19 variables relevant to BMI and documented their meaning in a data dictionary.
3. **Data Inspection:** reviewed data types, non-null counts, descriptive statistics, and categorical distributions.
4. **Categorical Preparation:** converted the seven 1-to-5 rating variables into ordered categorical variables.
5. **Missing Data Analysis:** quantified missing values in `Height` and `Weight` and assessed their impact on BMI calculation.
6. **Height and Weight Distribution:** examined the distributions and skewness of the two body measurements.
7. **Outlier Detection:** identified outliers in `Height` and `Weight` using boxplots and the interquartile range (IQR) rule.
8. **Data Cleaning:** removed 14 records identified as outliers in `Height` and `Weight` before calculating BMI.
9. **BMI Calculation:** calculated BMI as weight in kilograms divided by height in meters squared.
10. **BMI Outlier Analysis:** identified BMI outliers but retained them because they may represent plausible observations and require further investigation.
11. **Group Comparisons:** used boxplots to compare BMI across 15 categorical demographic and lifestyle variables.
12. **Numeric Associations:** examined the Spearman correlation between BMI and `Age` and between BMI and `Number of siblings`.
13. **Interpretation:** summarized the observed patterns, data-quality issues, limitations, and next steps.

## Key Findings

- **Missing data:** 17 of the 19 analyzed variables contain some missing values. `Height` and `Weight` each have 20 missing values, representing approximately 1.98% of the 1,010 responses. Records with missing body measurements were not imputed and were excluded from BMI calculation.
- **Height and Weight distributions:** `Height` shows negative skewness, while `Weight` shows positive skewness. The dataset includes potentially problematic values, such as a recorded height of 62 cm and weights above 160 kg, which require investigation.
- **Outliers:** 9 outliers were identified in `Weight` and 6 in `Height` using the IQR rule and boxplots. Fourteen records were removed during data cleaning because extreme body measurements could distort BMI.
- **BMI:** BMI was calculated from the cleaned `Height` and `Weight` variables. Six BMI outliers were identified but retained because they may represent valid individual differences.
- **Gender:** Men have a higher median BMI than women in the dataset. However, the distributions overlap substantially, so the observed difference should not be interpreted as statistically significant or causal.
- **Education:** The doctorate-degree group has a notably higher median BMI, but it contains only three observations, making this comparison particularly unstable.
- **Smoking:** BMI distributions are broadly similar across smoking categories, with current and former smokers showing slightly higher median BMIs than some other groups.
- **Alcohol:** Respondents who reported never drinking have a slightly higher median BMI than social drinkers, while the distributions overlap considerably.
- **Internet usage:** Some differences in median BMI are visible across internet-use categories, but the group reporting no internet use contains only three observations.
- **Self-reported variables:** `Healthy eating`, `Spending on healthy eating`, `Eating to survive`, `Health`, `Active sport`, `Passive sport`, and `Adrenaline sports` show substantial overlap in BMI distributions, with no strong or consistent pattern apparent from the boxplots.
- **Other characteristics:** `Only child`, `Village - town`, and `House - block of flats` show broadly similar BMI distributions across their categories.
- **Overall:** Gender and Education show some of the most noticeable visual differences in BMI, but most categorical variables display substantial overlap. The analysis identifies associations in this sample rather than causes or statistically significant effects.

## Limitations

- **Convenience sample:** The survey was answered by 1,010 people of Slovak nationality aged 15 to 30 who were invited by students of a statistics class. The sample is not representative of a broader population.
- **Self-reported measurements:** `Height` and `Weight` were reported by respondents and were not independently verified.
- **Data quality:** Some height and weight values appear extreme and may represent data-entry errors, but the original source does not provide enough information to determine their validity automatically.
- **Outlier treatment:** Fourteen records were removed based on outliers in `Height` and `Weight`. This decision can affect the resulting BMI distribution and should be considered when interpreting the findings.
- **BMI limitations:** BMI is a screening index calculated from height and weight. It does not measure body composition or overall health status.
- **Small categories:** Some categories contain very few observations, particularly `doctorate degree` and `no time at all` for internet usage. Results for these groups are therefore unstable.
- **Descriptive analysis:** The notebook uses visual comparisons and Spearman correlations. It does not establish causation or statistical significance.
- **Self-reported lifestyle variables:** Several variables measure attitudes, concerns, willingness, or interests rather than objectively measured behaviors.

## How to Run

1. Clone or download this repository.
2. Ensure that `responses.csv` is stored in the `data/` directory.
3. Open `young_people_bmi_eda.ipynb` in VS Code or Jupyter.
4. Make sure Python and the Jupyter extension are installed.
5. Install the required libraries if they are not already available:

```bash
python -m pip install pandas numpy matplotlib seaborn
```

6. Select the appropriate Python kernel.
7. Run the notebook cells in order, from top to bottom.

**Note:** the notebook loads the dataset using the relative path `../data/responses.csv`, so the folder structure should be preserved.

## Next Steps

- Investigate the extreme `Height`, `Weight`, and BMI values using the original dataset and available documentation.
- Reassess the 14 removed body-measurement outliers and determine whether there is sufficient evidence that they are erroneous.
- Compare the current results with an analysis that retains the extreme body measurements to evaluate the sensitivity of the findings.
- Evaluate an appropriate missing-data treatment and compare its results with the current complete-case approach.
- Apply statistical tests and confidence intervals if the objective is to determine whether observed group differences are statistically significant.
- Consider additional data or a more representative sample before drawing conclusions about young people more broadly.

---

*This project is an exploratory data analysis for portfolio purposes. Findings are limited to the supplied survey dataset.*
