# Hospital Insights - Readmission and Performance Analysis
This project analyzes hospital readmissions data with the goal of identifying patterns and insights related to hospital performance. The project focuses on metrics like readmission rates, return days, and unplanned visits to evaluate and compare hospitals, aiming to provide actionable insights that will help healthcare institutions improve patient outcomes.

# Dataset Summary
This dataset, "Unplanned Hospital Visits: Provider Data," is released by Medicare to analyze provider performance on three primary measures:
1. Excess Days in Acute Care (EDAC), or return days,
2. Unplanned Readmissions following inpatient admissions, and
3. Unplanned Visits after outpatient procedures.
These measures provide insight into hospital quality and patient outcomes without requiring manual reporting from hospitals. Instead, they are calculated using Medicare claims and eligibility data, with data for some conditions (such as COPD, heart attack, heart failure, pneumonia, hip/knee replacement, and others) also sourced from VHA data. This claims-based approach offers comparable accuracy to chart reviews when calculating readmission and hospital visit rates.

Note: Data from the first and second quarters of 2020 is excluded due to the COVID-19 pandemic's impact on hospital services.

**Score Definition and Adjustment**
Each hospital’s Score represents the number of observed events—readmissions, return days, or unplanned visits—attributed to its performance. This score is risk-adjusted to account for patient characteristics such as age, medical history, and comorbidities that may increase readmission likelihood, allowing for fairer comparisons between hospitals.

For each measure:
- Readmission and hospital visit rates are compared to a national benchmark. Hospitals fall into categories based on whether their interval estimate (a 95% confidence interval) is above, below, or within the national average.
- Return days are benchmarked against zero, with hospitals categorized based on whether their result lies above, below, or includes zero.
Hospitals with too few cases for reliable estimates are marked accordingly. This classification framework ensures that results account for variability and are representative of each hospital’s relative performance.


# Data Import and Cleaning
created tables with defined data types
The raw dataset was imported into SQL Server, where initial cleaning steps were taken to ensure data quality. The steps involved:
- Identifying null values, "Not Applicable," and "Not Available" entries across key columns.
- Removing rows with null or unavailable values in critical fields like Denominator and Score.
- Dropping unnecessary columns, such as Footnote and Telephone_Number.

In Cleaning.sql, a custom table called MeasureMapping was created to map technical measure IDs to user-friendly names. Each measure, such as "Readmission Rate after Hip/Knee Replacement" or "Heart Failure 30-Day Readmission Rate," was given a readable name to improve the clarity of analysis and visualizations. Additionally, a MeasureGroup field was added to categorize measures into groups Readmissions, Return Days, and Unplanned Visits.

# Data Analysis in SQL
SQL scripts in Analysis.sql were used to perform calculations and aggregations to extract meaningful insights:
- Summary statistics (min, max, average) for numerical fields.
- Distribution of hospital performance against the national rate.
- Identification of top and bottom performing hospitals based on readmission rates.
- Average readmission rates by year and state.
- Analysis of readmission rates by specific conditions.



# Data Source
For more information on the [dataset](https://data.cms.gov/provider-data/dataset/632h-zaca#data-table), please refer to the [CMS dataset documentation](https://data.cms.gov/provider-data/dataset/632h-zaca#data-table).

