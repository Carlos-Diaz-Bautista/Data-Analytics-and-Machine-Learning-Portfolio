# Young People BMI Exploratory Data Analysis

**Date:** October 20, 2026

## Project Overview

This project explores a survey of 1,010 young people to understand which demographic and lifestyle characteristics are associated with body mass index (BMI). Using Python, pandas, Matplotlib, and seaborn, the analysis prepares the weight and height measurements, calculates the BMI of each respondent, and compares it across 17 demographic and lifestyle variables (15 categorical and two numeric).

The project focuses on building a reliable BMI variable from survey data, documenting every decision about missing and extreme values, and communicating findings while acknowledging the limitations of the dataset.

## Business Context

Organizations that design wellness programs, health campaigns, or products for young adults need to know which groups differ in body mass index before deciding where to focus. Survey data can support that decision, but reported body measurements have missing answers and implausible values that can distort a comparison between groups, so the measurements are prepared before any group is compared.

## Objectives

- Assess the structure, completeness, and plausibility of the body measurements.
- Treat missing and extreme values in `Weight` and `Height` with documented decisions.
- Calculate the BMI of each respondent and check it for atypical values.
- Compare the BMI across demographic and lifestyle characteristics.
- Identify data-quality issues that affect the interpretation of the results.

## Dataset

The analysis uses `responses.csv`, from the [Young People Survey](https://www.kaggle.com/datasets/miroslavsabo/young-people-survey) dataset on Kaggle.

It contains 1,010 responses and 150 columns. The survey was answered in 2013 by people of Slovak nationality aged 15 to 30, who were invited by students of a statistics class. This project works with 19 of the columns: `Height` and `Weight`, used to calculate the BMI, and 17 demographic and lifestyle variables compared against it.

- **Body measurements:** `Height`, `Weight`
- **Demographic variables:** `Age`, `Number of siblings`, `Gender`, `Education`, `Only child`, `Village - town`, `House - block of flats`
- **Health and lifestyle variables:** `Smoking`, `Alcohol`, `Internet usage`, `Healthy eating`, `Spending on healthy eating`, `Eating to survive`, `Health`, `Active sport`, `Passive sport`, `Adrenaline sports`

The remaining 131 columns (music, movies, phobias, personal opinions, and similar answers) are listed in the data dictionary of the notebook but are not analyzed. The seven variables rated from 1 to 5 are treated as ordinal categorical variables.

The dataset is a convenience sample. Therefore, the findings describe the respondents of this survey and should not be generalized to other populations.

## Tools and Libraries

- **Python:** programming language used for the analysis.
- **pandas and NumPy:** used to load, inspect, filter, group, and summarize the dataset.
- **Matplotlib and seaborn:** used to create histograms and boxplots.
- **Jupyter Notebook:** used to organize the analysis, document the process, and present the results.

## Project Structure

```text
young-people-bmi-eda/
├── data/
│   └── responses.csv
├── notebooks/
│   └── young_people_bmi_eda.ipynb
└── README.md
```

- `data/`: contains the dataset.
- `notebooks/`: contains the Jupyter Notebook with the analysis.
- `README.md`: documents the project, its objectives, methodology, and findings.

## Analysis Workflow

The steps follow the numbered sections of the notebook.

1. **Load the data (section 5):** loaded the CSV file and documented the meaning of each column in a data dictionary.
2. **Inspect the dataset structure (section 6):** kept the 19 selected columns, reviewed data types and non-null counts, and converted the seven 1-to-5 ratings to ordered categorical columns.
3. **Assess missing values (section 7):** counted the missing values in `Weight` and `Height` and decided not to impute them.
4. **Examine the distribution of Weight and Height (section 8):** created histograms of `Weight` and `Height` and measured their skewness with the pandas method and Pearson's second coefficient.
5. **Detect outliers in Weight and Height (section 9):** applied the interquartile range rule to `Weight` and `Height`, reviewed boxplots, and removed the flagged records.
6. **Calculate BMI and detect its outliers (section 10):** calculated the BMI and checked it for atypical values with the same rule.
7. **Compare BMI across respondent characteristics (section 11):** counted the respondents in each category, compared the BMI across 15 categorical variables with boxplots, and calculated its Spearman correlation with two numeric variables.
8. **Conclusions and next steps (section 12):** summarized findings, data-quality issues, and next steps.

## Key Findings

- **Data quality:** `Height` and `Weight` are each missing in 20 respondents (1.98%), and 30 respondents lack at least one of them. The values were not imputed, so those respondents have no BMI. In addition, 14 records (1.39%) with extreme `Weight` or `Height` were removed, and the 6 BMI outliers, between about 30 and 32, were retained as plausible values.
- **Gender:** men have a higher median BMI than women (about 23 against about 20), the clearest difference among the variables compared.
- **Age and siblings:** `Age` has a weak positive correlation with BMI (0.20), and `Number of siblings` has practically none (-0.04).
- **Lifestyle and upbringing:** smoking, alcohol, internet usage, only child, village or city, type of housing, and the seven 1-to-5 ratings show overlapping BMI distributions with no consistent pattern.
- **Small groups:** the `doctorate degree` group has the highest median BMI but only three respondents, so it is not a reliable result.

## Limitations

- **Convenience sample:** the respondents were invited by students and are all Slovak nationals aged 15 to 30, so the findings cannot be generalized to other populations.
- **Unverified measurements:** `Weight` and `Height` come from survey responses and were not independently verified. BMI is a screening index and does not measure body composition or health status.
- **Conservative outlier removal:** the interquartile range rule flagged implausible values, such as a height of 62 cm, but also plausible ones, such as heights around 200 cm, so some real respondents were removed.
- **Small categories:** several categories contain very few respondents, so their comparisons are not reliable.
- **Associations, not causes:** the comparisons are descriptive and no statistical tests were run. Differences across variables could partly reflect the gender composition of each group.

## How to Run

1. Clone or download this repository.
2. Get `responses.csv` from the source listed in the Dataset section and save it in the `data/` directory.
3. Open `young_people_bmi_eda.ipynb` in VS Code.
4. Make sure Python and the Jupyter extension are installed in VS Code.
5. Install the required libraries if they are not already available:

```bash
python -m pip install pandas numpy matplotlib seaborn
```

6. Select the appropriate Python kernel and run the notebook cells in order, from top to bottom.

**Note:** the notebook loads the data with a relative path (`../data/responses.csv`), so keep the folder structure as it is.

## Next Steps

- Review the 14 removed records and keep the plausible ones, limiting removal to implausible values such as the 62 cm height, then check whether the conclusions change.
- Combine very small categories with neighboring ones, such as the two primary school categories, after checking the dataset documentation.
- Test whether the differences, especially by gender, are larger than expected by chance, and compare the other variables within each gender.
- Fit a multivariable model to see which variables keep an association with BMI after accounting for gender and age.

---

*This project is an exploratory data analysis for portfolio purposes. Findings are limited to the supplied dataset.*
