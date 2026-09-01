# Global Freelancers (A Data Cleaning Project) 
# Oasis Infobytes Internship Project

## OverView
**Objective:** Demonstrate professional-level data cleaning skills by taking a deliberately messy dataset and systematically transforming it into a clean, analysis-ready dataset. Document every decision.

## Dataset:
- Source: https://www.kaggle.com/datasets/urvishahir/global-freelancers-raw-dataset
- Rows: 1000
- Columns: 10 (Raw)
- Content: Freelancer Demographics(freelancer_ID, name, gender, age, country),
professional details (primary skill, years of experience, hourly rate), and performance data (client rating)

## Methodology: 
The Jupyter Notebook follows 8 stages. Each stage is documented in line and reasoning behind it, not just code executes.

# |Stage | Summary |
|---|---|---|
| 1 | Data quality Report | count Null values, check duplicates, dtypes and resolve anomolies. |
| 2 | Missing Data Handling | Choose different strategies for each columns and imputed new value which suits there. |
| 3 | Duplicate Removal | Checked and removed duplicates but there were no duplicates. |
| 4 | Standardization |  Standardized columns having mixed casing, extra whitespace, or the same real-world value spelled multiple ways. |
| 5 | Outlier Detection | Detect outliers using IQR Technique | 
| 6 | Data Type Correction | Verified Each column dtype to their expected Data Type | 
| 7 | Before vs. After Summary | Quantified the net effect of each prior step. | 
| 8 | Save cleaned csv | Exported cleaned, verified csv | 


## Few Worth Noticing Decisions:

1.  **Missing `rating` were left unfilled on purpose,** Some freelancers have no rating (blank), and some have an actual rating of 0. These are not the same thing, means they were not rated by clients. While 0 means someone rated them and gave lowest score. So Blank were left means having no rating and new column `has_rating` with **(True/False)** in which **True** means has any rating and **False** means Not ratings(blank)
2.  **Missing hourly rates were filled in based on each person's skill, not one single average for everyone.** Different skills pay differently. For example, Cybersecurity and DevOps freelancers tend to charge more per hour than Web Development or Graphic Design freelancers. So instead of using one overall average rate to fill in blanks, we used the average rate for that specific skill. This keeps the pay differences between skills realistic instead of flattening them out.
3.  I used one method **(IQR)** instead of another **(Z-score)** to find unusual values, because **Z-score** gives misleading results when the data isn't evenly spread out.
4.  **Gender entries like "M", "male", "MALE", and "Male"** were all combined into one clear label. The dataset had 9 different ways of writing just 2 categories (Male and Female).

## Results;  Before vs. After
| Metric | Before | After |
| --- |--- | ---| 
| Row count | 1,000 | 1,000 |
| Total null values | 276 | 101 *(all in column `rating`)* |
| Duplicate rows | 0 | 0 |
| Dtype issues | 1 (`hourly_rate` stored as text) | 0 (verified) |
| Column count | 10 | 11 *(added `has_rating`)* |

No rows were deleted at any stage of this pipeline. Every missing-data and outlier decision was resolved through imputation, retention, or explicit flagging rather than deletion.


##  Limitations

1. `is_active` and `client_satisfaction`, present in a broader version of this dataset, were excluded from this project's scope and were not cleaned or analyzed here.
2.  The `NaN`-means-"unrated" interpretation for `rating` is a reasonable inference from the data (since `0.0` already exists as a distinct, real value) but is not confirmed by any dataset documentation.

## Tech Stack

Python · pandas · numpy · scipy · Jupyter Notebook

## How to Run
1. Clone the Repository
2. Open `freelancer_data_cleaning.ipynb`
3. **Restart the kernel, then Run All:** the notebook is written to run correctly top-to-bottom in  single clean pass. Running cells out of order (e.g. re-running an earlier load cell after a later cleaning cell) will reset intermediate work silently; always verify with a full Restart → Run All before trusting the output.
4. The cleaned file is written to `global_freelancers_cleaned.csv`

 
## Author
- Shazma Shaheen-Data Analytics Intern at Oasis Infobytes
- LinkedIn: linkedin.com/in/shazma-shaheen