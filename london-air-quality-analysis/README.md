# London Air Quality Exploratory Data Analysis

**Date:** October 7, 2026

## Project Overview

This project explores a dataset of 43,800 hourly air quality records collected at monitoring site CT3 in London during 2017. Using Python, pandas, and Matplotlib, the analysis examines data completeness, pollutant value distributions, and monthly variations in average values.

The project focuses on identifying patterns in the available measurements, flagging data-quality issues that should be addressed before drawing conclusions, and communicating findings while acknowledging the limitations of the dataset.

## Objectives

- Assess the structure and completeness of the data.
- Summarize the distribution of recorded values for each pollutant.
- Analyze monthly variations in average pollutant values.
- Identify missing data and unusual measurements that require further investigation.
- Summarize the findings while acknowledging the limitations of the available data.

## Dataset

The analysis uses `LaqnData.csv`, a dataset obtained from the book *Hands-On Data Preprocessing in Python*.

It contains 43,800 hourly records (8,760 for each of five pollutant codes: `NO`, `NO2`, `NOX`, `PM10`, and `PM2.5`) and six variables, recorded from January 1 to December 31, 2017:

- **Location and pollutant:** `Site`, `Species`
- **Time:** `ReadingDateTime`
- **Measurement:** `Value`, `Units`
- **Status:** `Provisional or Ratified`

The dataset represents a single monitoring site over one year. Therefore, the findings describe the available measurements at CT3 and should not be generalized to all of London or other time periods.

## Tools and Libraries

- **Python:** programming language used for the analysis.
- **pandas:** used to load, inspect, group, and summarize the dataset.
- **Matplotlib:** used to create histograms and line plots of monthly average values.
- **Jupyter Notebook:** used to organize the analysis, document the process, and present the results.

## Project Structure

```text
london-air-quality-analysis/
├── data/
│   └── LaqnData.csv
├── notebooks/
│   └── london_air_quality_analysis.ipynb
└── README.md
```

- `data/`: contains the dataset.
- `notebooks/`: contains the Jupyter Notebook with the analysis.
- `README.md`: documents the project, its objectives, methodology, and findings.

## Analysis Workflow

1. **Data Loading:** loaded the CSV file and documented the meaning of each column in a data dictionary.
2. **Data Inspection:** reviewed the first records, data types, and non-null counts.
3. **Date Preparation:** converted the timestamp column to datetime format and verified the date range.
4. **Dataset Overview:** reviewed the monitoring site, pollutant codes, measurement units, and record status.
5. **Missing Data Analysis:** calculated missing-value counts and percentages by pollutant and by month.
6. **Descriptive Statistics:** summarized pollutant values to understand their central tendency, variability, and range.
7. **Monthly Analysis:** calculated and visualized monthly average values to examine changes throughout the year.
8. **Distribution Analysis:** created histograms to explore the distribution of recorded values for each pollutant.
9. **Interpretation:** summarized findings, data-quality issues, and next steps.

## Key Findings

- **Data completeness:** PM2.5 is missing 32.27% of its records, against about 1.1% for each of the other pollutants, with no values in September and October.
- **Value distributions:** the mean is higher than the median for all five pollutants. NO, NOX, PM10, and PM2.5 are concentrated at low values with a long right tail, while NO2 is more symmetric.
- **Extreme values:** NO, NOX, and PM10 have maximum readings far above their medians (401.8, 734.3, and 633.1), which warrant further investigation before drawing conclusions about their validity.
- **Monthly variation:** January had the highest monthly average for all five pollutants. NO, NO2, and NOX reach their lowest values in June and July and rise again in November.
- **Data quality:** negative values are present for NO, PM10, and PM2.5. They should be checked against the source documentation before deciding how to handle them.

## Limitations

- **Limited coverage:** the dataset covers only one monitoring site and one year, so the findings cannot be generalized to all of London or other years.
- **Missing data:** PM2.5 has substantial gaps in several months, limiting the interpretation of its monthly patterns.
- **Measurement units:** the dataset contains different unit labels, so values should not be assumed to be directly comparable across pollutants.
- **Unverified values:** unusually high and negative measurements require further investigation before deciding whether they should be retained or excluded.
- **Associations, not causes:** the analysis describes patterns in the available data; it does not establish causes or assess regulatory compliance.

## How to Run

1. Clone or download this repository.
2. Ensure that `LaqnData.csv` is stored in the `data/` directory.
3. Open `london_air_quality_analysis.ipynb` in VS Code.
4. Make sure Python and the Jupyter extension are installed in VS Code.
5. Install the required libraries if they are not already available:

```bash
python -m pip install pandas matplotlib
```

6. Select the appropriate Python kernel and run the notebook cells in order, from top to bottom.

**Note:** the notebook loads the data with a relative path (`../data/LaqnData.csv`), so keep the folder structure as it is.

## Next Steps

- Investigate unusually high and negative measurements using the original data and source documentation.
- Review the missing-data patterns, particularly for PM2.5, before deciding how to handle missing values.
- Verify the measurement units and record-status information using the dataset documentation.
- Extend the analysis to additional monitoring sites or years to explore whether the observed patterns persist across different locations and time periods.

---

*This project is an exploratory data analysis for portfolio purposes. Findings are limited to the supplied dataset.*
