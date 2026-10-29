# Credit Risk Exploratory Data Analysis

**Date:** October 13, 2026

## Project Overview

This project explores a credit risk dataset of 32,581 loan records to understand which borrower and loan characteristics are associated with default. Using Python, pandas, Matplotlib, and seaborn, the analysis examines data quality, variable distributions, default rates by category, and relationships between numeric variables and loan status.

The project focuses on identifying patterns in the available data, flagging data-quality issues that should be addressed before modeling, and communicating findings while acknowledging the limitations of the dataset.

## Business Context

Lenders need to understand which borrower and loan characteristics are associated with default before approving credit or building a risk model. Before modeling, it is also necessary to check whether the data are complete and plausible.

## Objectives

- Assess the structure, completeness, and plausibility of the data.
- Summarize the distribution of numeric and categorical variables.
- Compare default rates across borrower and loan characteristics.
- Examine how numeric variables relate to default.
- Identify data-quality issues to address before modeling.

## Dataset

The analysis uses `credit_risk_dataset.csv`, from the [Credit Risk Dataset](https://www.kaggle.com/datasets/laotse/credit-risk-dataset) on Kaggle.

It contains 32,581 loan records and 12 variables:

- **Borrower:** `person_age`, `person_income`, `person_home_ownership`, `person_emp_length`
- **Loan:** `loan_intent`, `loan_grade`, `loan_amnt`, `loan_int_rate`, `loan_percent_income`
- **Credit bureau:** `cb_person_default_on_file`, `cb_person_cred_hist_length`
- **Outcome:** `loan_status` (0 = repaid, 1 = default)

The dataset has no date field, so changes over time cannot be analyzed. The findings describe this dataset and should not be generalized to other lenders or populations.

## Tools and Libraries

- **Python:** programming language used for the analysis.
- **pandas and NumPy:** used to load, inspect, group, and summarize the dataset.
- **Matplotlib and seaborn:** used to create histograms, bar plots, boxplots, and a correlation heatmap.
- **Jupyter Notebook:** used to organize the analysis, document the process, and present the results.

## Project Structure

```text
credit-risk-eda/
├── data/
│   └── credit_risk_dataset.csv
├── notebooks/
│   └── credit_risk_eda.ipynb
└── README.md
```

- `data/`: contains the dataset.
- `notebooks/`: contains the Jupyter Notebook with the analysis.
- `README.md`: documents the project, its objectives, methodology, and findings.

## Analysis Workflow

The steps follow the numbered sections of the notebook.

1. **Load the data (section 5):** loaded the CSV file and documented the meaning of each column in a data dictionary.
2. **Inspect the dataset structure (section 6):** reviewed the first records, data types, and non-null counts.
3. **Assess missing values (section 7):** calculated missing-value counts and percentages for each column, without imputing them.
4. **Check value plausibility (section 8):** reviewed summary statistics of the numeric variables to detect implausible values.
5. **Explore numeric variables (section 9):** created histograms for each numeric variable, and redrew those with extreme values using the range up to the 99th percentile.
6. **Explore categorical variables (section 10):** counted loans by category for home ownership, loan purpose, loan grade, and previous default, split by loan status.
7. **Compare default rates by category (section 11):** compared the default rate of each category with the overall default rate.
8. **Compare numeric variables by loan status (section 12):** compared the distribution of each numeric variable between repaid and defaulted loans with boxplots.
9. **Examine correlations (section 13):** calculated a correlation matrix, including `loan_status`.
10. **Conclusions and next steps (section 14):** summarized findings, data-quality issues, and next steps.

## Key Findings

- **Data quality:** only `person_emp_length` (2.75%) and `loan_int_rate` (9.56%) have missing values. Some values are implausible, such as ages up to 144 years, employment lengths up to 123 years, and an income of 6,000,000.
- **Default rate:** about 22% of the loans are in default.
- **Loan grade:** default rates stay below the overall rate for grades A to C and exceed 55% from grade D, approaching 100% for grade G, which has very few records.
- **Other categories:** renters, borrowers with a previous default on file, and loans for debt consolidation, medical expenses, or home improvement default more than average.
- **Numeric variables:** defaulted loans show higher interest rates, a larger loan amount relative to income, and lower borrower income. Age and credit history length look similar in both groups.
- **Correlations:** no numeric variable has a strong linear relationship with default; the highest are `loan_percent_income` (0.38) and `loan_int_rate` (0.34). `person_age` and `cb_person_cred_hist_length` are strongly correlated with each other (0.86).

## Limitations

- **No time dimension:** the dataset has no date field, so trends over time cannot be analyzed.
- **Unverified values:** implausible values were flagged but kept, and missing values were not imputed.
- **Lender-assigned variables:** `loan_grade` and `loan_int_rate` may reflect the lender's own risk assessment, which limits how they should be interpreted.
- **Unstated currency:** the dataset does not specify the currency of monetary values.
- **Small categories:** rates for categories with very few loans, such as `OTHER` home ownership and grade G, should be read with caution.
- **Associations, not causes:** the analysis describes patterns and does not establish causal relationships.

## How to Run

1. Clone or download this repository.
2. Get `credit_risk_dataset.csv` from the source listed in the Dataset section and save it in the `data/` directory.
3. Open `credit_risk_eda.ipynb` in VS Code.
4. Make sure Python and the Jupyter extension are installed in VS Code.
5. Install the required libraries if they are not already available:

```bash
python -m pip install pandas numpy matplotlib seaborn
```

6. Select the appropriate Python kernel and run the notebook cells in order, from top to bottom.

**Note:** the notebook loads the data with a relative path (`../data/credit_risk_dataset.csv`), so keep the folder structure as it is.

## Next Steps

- Decide how to treat missing and implausible values, and document how many records each decision affects.
- Check the dataset documentation to confirm how `loan_grade` and `loan_int_rate` were assigned.
- Build a baseline default-prediction model, which this exploratory analysis prepares.

---

*This project is an exploratory data analysis for portfolio purposes. Findings are limited to the supplied dataset.*
