# HR Analytics: Employee Attrition & Workforce Analysis

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat-square&logo=pandas&logoColor=white)
![Matplotlib & Seaborn](https://img.shields.io/badge/Visualization-Matplotlib%20%7C%20Seaborn-4C72B0?style=flat-square)
![Domain](https://img.shields.io/badge/Domain-HR%20Analytics-2E8B57?style=flat-square)

---

## 1. Executive Summary & Project Overview

Employee attrition presents a critical operational and financial challenge for organizations, directly impacting productivity, recruitment expenses, workforce stability, and team morale.

This project conducts an end-to-end **Exploratory Data Analysis (EDA)** on the **IBM HR Analytics Employee Attrition & Performance** dataset to uncover key drivers of employee turnover across demographics, job roles, satisfaction metrics, working conditions, compensation, and tenure.

* **Project Type:** Exploratory Data Analysis (EDA)
* **Domain:** Human Resources Analytics
* **Primary Objective:** Identify high-attrition employee segments and translate statistical patterns into actionable, data-informed retention recommendations.

---

## 2. Business Questions

To guide the investigation into workforce turnover, this analysis addresses the following core questions:

1. **Overall Baseline:** What proportion of employees have left the organization?
2. **Organizational & Role Impact:** How does attrition vary across departments and individual job roles?
3. **Demographics & Tenure:** How are employee age and years at the company associated with turnover?
4. **Workplace Satisfaction:** How do job satisfaction, environment satisfaction, relationship satisfaction, and work-life balance relate to attrition?
5. **Workload & Travel:** How do overtime, business travel frequency, and commuting distance correlate with employees leaving?
6. **Compensation & Career Progression:** How do monthly income, stock option levels, promotion history, and prior employers differ between retained and departing employees?
7. **Target Segments:** Which employee groups warrant prioritized investigation to strengthen retention efforts?

---

## 3. Dataset Description

* **Dataset:** IBM HR Analytics Employee Attrition & Performance (`employee_attrition.csv`)
* **Dimensions:** 1,470 employee records across 35 original features
* **Target Variable:** `Attrition` (`Yes` = left the organization; `No` = stayed)

**Feature Categories Covered:**
* **Demographics:** Age, gender, marital status, education level, education field, distance from home
* **Role & Department:** Department, job role, job level, business travel, overtime
* **Compensation:** Monthly income, daily/hourly/monthly rates, percent salary hike, stock option level
* **Tenure & Career History:** Years at company, total working years, years in current role, years since last promotion, years with current manager, number of companies worked
* **Satisfaction & Engagement:** Job satisfaction, environment satisfaction, relationship satisfaction, job involvement, work-life balance, performance rating

---

## 4. Tech Stack & Tools

* **Programming Language:** Python
* **Data Manipulation & Analysis:** Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Business Intelligence & Dashboarding:** Power BI, DAX
* **Environment & Workflow:** Jupyter Notebook, Visual Studio Code
* **Version Control:** Git, GitHub

---

## 5. Repository Structure

```text
hr-analytics/
│
├── data/
│   └── employee_attrition.csv
│
├── notebooks/
│   ├── hr_analytics.ipynb
│   └── hr_analytics_final.ipynb
│
├── powerbi/
│   └── hr_analytics_dashboard.pbix
│
├── images/
│   └── hr_dashboard.png
│
├── outputs/
│   └── visualizations/
│
└── README.md
```
**Folder descriptions:**

- `data/` contains the dataset used for analysis.
- `notebooks/` contains the original analysis notebook and the final, polished notebook.
- `outputs/` is reserved for exported charts, tables, or other project outputs.
- `powerbi/` contains the Power BI dashboard file (.pbix).
- `README.md` documents the project, methodology, findings, and recommendations.

The original notebook is retained as a backup. The final notebook is intended to contain the organized, presentation-ready analysis.



## 6. Data Cleaning and Preparation

The dataset was inspected and checked for common data-quality issues before the exploratory analysis.

The following steps were performed:

1. Loaded the dataset into a Pandas DataFrame.
2. Inspected the dataset dimensions, column names, data types, and sample records.
3. Examined numerical summary statistics.
4. Checked for missing values.
5. Checked for duplicate rows.
6. Identified columns with constant values that do not contribute useful variation to the analysis.
7. Removed the constant columns `EmployeeCount`, `Over18`, and `StandardHours`.
8. Examined the distributions of important numerical variables.
9. Created grouped features to make selected workforce patterns easier to interpret.
10. Used cross-tabulations and percentage-based comparisons to study attrition across categories.

### Data-quality results

| Check | Result |
|---|---|
| Original dataset size | 1,470 rows × 35 columns |
| Missing values | None found |
| Duplicate rows | None found |
| Constant columns removed | `EmployeeCount`, `Over18`, `StandardHours` |
| Final cleaned dataset size | 1,470 rows × 32 columns |

### Feature engineering

Selected numerical variables were grouped into categories to make the findings easier to interpret.

**Age groups**
- 18–24
- 25–34
- 35–44
- 45–54
- 55+

**Company tenure groups**
- 0–1 years
- 2–5 years
- 6–10 years
- 11+ years

**Distance-from-home groups**
- Near: 1–5
- Moderate: 6–15
- Far: 16–30

**Time-since-last-promotion groups**
- 0–2 years
- 3–5 years
- 6+ years

These groupings support comparisons between employee segments. They are analytical categories created for this project rather than original dataset fields.

---

## 7. Exploratory Data Analysis

The EDA examined employee attrition from several perspectives.

### 7.1 Overall Attrition

The overall distribution of the target variable was examined to understand how many employees stayed and how many left.

**Finding:** 237 out of 1,470 employees left the organization, representing approximately **16.12%** of the dataset. The remaining 1,233 employees, or approximately **83.88%**, stayed.

This is the proportion of employees marked as having left in the dataset. It should not automatically be interpreted as an annual attrition rate.

### 7.2 Department and Job Role

Attrition was compared across departments and individual job roles to identify groups with relatively higher and lower turnover.

**Department-level findings**
- Sales: approximately 20.63% attrition.
- Human Resources: approximately 19.05% attrition.
- Research & Development: approximately 13.84% attrition.

**Job-role findings**
- Sales Representatives have the highest observed attrition rate at approximately **39.76%**.
- Human Resources employees have an attrition rate of approximately **23.08%**.
- Laboratory Technicians have an attrition rate of approximately **23.94%**.
- Research Directors have the lowest observed attrition rate at approximately **2.50%**.
- Managers have an attrition rate of approximately **4.90%**.

**Interpretation:** Attrition varies considerably across job roles. Sales Representatives are a particularly important group for further investigation.

### 7.3 Job Satisfaction Among Sales Representatives

Job satisfaction was examined specifically among Sales Representatives to understand how turnover varied across satisfaction levels.

| Job satisfaction level | Attrition rate |
|---|---:|
| 1 | 58.33% |
| 2 | 47.62% |
| 3 | 33.33% |
| 4 | 30.43% |

**Finding:** Sales Representatives with satisfaction level 1 have the highest attrition rate, while those with satisfaction level 4 have the lowest.

The pattern shows a general decrease in attrition as job satisfaction increases within this role.

These percentages apply specifically to Sales Representatives and should not be generalized to all employees.

### 7.4 Overtime

Attrition was compared between employees who work overtime and employees who do not.

| Overtime | Employees who stayed | Employees who left |
|---|---:|---:|
| No | 89.56% | 10.44% |
| Yes | 69.47% | 30.53% |

**Finding:** Employees who work overtime have an attrition rate of approximately **30.53%**, compared with **10.44%** among employees who do not work overtime.

The observed attrition rate for employees working overtime is approximately 2.9 times that of employees not working overtime.

This is an association and does not establish that overtime directly causes employees to leave.

### 7.5 Age and Attrition

Employees were grouped by age to compare attrition across different age segments.

| Age group | Attrition rate |
|---|---:|
| 18–24 | 38.20% |
| 25–34 | 20.22% |
| 35–44 | 10.10% |
| 45–54 | 10.20% |
| 55+ | 15.94% |

**Finding:** Employees aged 18–24 have the highest observed attrition rate, at approximately **38.20%**. Attrition is lower among the middle age groups, but the pattern is not perfectly monotonic.

Further investigation could explore onboarding, career expectations, compensation, and development opportunities for younger employees.

### 7.6 Company Tenure and Attrition

Years at the company were grouped to investigate whether attrition differed by employee tenure.

| Years at company | Attrition rate |
|---|---:|
| 0–1 | 34.88% |
| 2–5 | 15.51% |
| 6–10 | 12.28% |
| 11+ | 8.13% |

**Finding:** Employees with 0–1 years at the company have the highest attrition rate, approximately **34.88%**. Employees with 11 or more years at the company have the lowest rate, approximately **8.13%**.

The attrition rate in the 0–1-year group is approximately 4.3 times that of the 11+-year group.

This suggests that early-tenure employees are an important segment to examine when investigating retention and onboarding.

### 7.7 Monthly Income

Monthly income was compared between employees who stayed and employees who left. Summary statistics and distribution characteristics were examined.

| Measure | Stayed | Left |
|---|---:|---:|
| Mean monthly income | 6,832.74 | 4,787.09 |
| Median monthly income | 5,204 | 3,202 |

**Findings**
- Employees who left had lower average and median monthly income than employees who stayed.
- Monthly income is right-skewed, meaning that a smaller number of employees have relatively high incomes.
- The IQR-based outlier check identified 114 high-income observations, approximately 7.76% of the dataset.
- The identified high-income values ranged from 16,595 to 19,999.

**Interpretation:** Compensation may be relevant to retention analysis, but income differences alone do not establish why employees leave. The high-income observations were identified for investigation rather than automatically removed.

### 7.8 Environment Satisfaction

Attrition was compared across environment satisfaction levels.

| Environment satisfaction level | Attrition rate |
|---|---:|
| 1 | 25.35% |
| 2 | 14.98% |
| 3 | 13.69% |
| 4 | 13.45% |

**Finding:** Employees with environment satisfaction level 1 have the highest attrition rate, approximately **25.35%**. The rate is lower for satisfaction levels 2–4.

This pattern suggests that lower satisfaction with the work environment is associated with higher attrition in this dataset.

### 7.9 Job Satisfaction Across the Workforce

Job satisfaction was also examined across all employees.

| Job satisfaction level | Attrition rate |
|---|---:|
| 1 | 22.84% |
| 2 | 16.43% |
| 3 | 16.52% |
| 4 | 11.33% |

**Finding:** Employees with the lowest job satisfaction level have the highest observed attrition rate, approximately **22.84%**, while employees with the highest satisfaction level have the lowest rate, approximately **11.33%**.

The middle satisfaction levels have similar attrition rates.

### 7.10 Work-Life Balance

Work-life balance levels were compared to examine their relationship with attrition.

| Work-life balance level | Attrition rate |
|---|---:|
| 1 | 31.25% |
| 2 | 16.86% |
| 3 | 14.22% |
| 4 | 17.65% |

**Finding:** Employees with work-life balance level 1 have the highest observed attrition rate, at approximately **31.25%**. The pattern is not perfectly linear: level 4 has a higher attrition rate than levels 2 and 3.

This suggests that work-life balance may be relevant to retention, but it should be considered alongside other factors.

### 7.11 Distance From Home

Employees were grouped by distance from home to compare attrition rates.

| Distance group | Attrition rate |
|---|---:|
| Near | 13.77% |
| Moderate | 16.11% |
| Far | 20.67% |

**Finding:** Employees in the Far group have the highest attrition rate, approximately **20.67%**, compared with **13.77%** for employees in the Near group.

The difference is approximately 6.90 percentage points. This association may warrant further investigation into commuting demands and employee circumstances.

### 7.12 Business Travel

Attrition was examined across business travel categories.

| Business travel category | Attrition rate |
|---|---:|
| Non-Travel | 8.00% |
| Travel_Rarely | 14.96% |
| Travel_Frequently | 24.91% |

**Finding:** Employees who travel frequently have the highest observed attrition rate, approximately **24.91%**, while employees who do not travel have the lowest rate, at **8.00%**.

The frequent-travel group has an attrition rate approximately 3.1 times that of the non-travel group.

This pattern suggests that travel requirements may be worth examining as part of a broader employee-retention review.

### 7.13 Relationship Satisfaction

Attrition was compared across relationship satisfaction levels.

| Relationship satisfaction level | Attrition rate |
|---|---:|
| 1 | 20.65% |
| 2 | 14.85% |
| 3 | 15.47% |
| 4 | 14.81% |

**Finding:** The lowest relationship satisfaction level has the highest observed attrition rate. The rates for levels 2–4 are relatively similar.

The relationship is not perfectly monotonic, so this factor should be interpreted alongside other findings.

### 7.14 Stock Option Level

Attrition rates were compared across stock option levels.

| Stock option level | Attrition rate |
|---|---:|
| 0 | 24.41% |
| 1 | 9.40% |
| 2 | 7.59% |
| 3 | 17.65% |

**Finding:** Employees at stock option level 0 have an attrition rate of approximately **24.41%**. The lowest observed rate is at level 2, approximately **7.59%**.

The pattern is non-monotonic because the attrition rate increases again at level 3. Therefore, the relationship should not be interpreted as a simple linear effect of stock option level.

### 7.15 Time Since Last Promotion

Employees were grouped according to the number of years since their last promotion.

| Time since last promotion | Attrition rate |
|---|---:|
| 0–2 years | 16.96% |
| 3–5 years | 10.13% |
| 6+ years | 16.28% |

**Finding:** The 0–2-year group has an attrition rate of approximately **16.96%**, while the 3–5-year group has the lowest rate, approximately **10.13%**. The rate increases to approximately **16.28%** for the 6+ group.

The pattern is non-linear. The groups should be examined alongside tenure, job level, and other employee characteristics before drawing conclusions.

### 7.16 Number of Companies Previously Worked For

Attrition was compared across values of `NumCompaniesWorked`.

**Finding:** Attrition rates vary across the number of companies employees have previously worked for, but the pattern is not consistent or steadily increasing.

For example, the observed attrition rate is approximately 11.68% for employees with a value of 0, 18.81% for a value of 1, 25.40% for a value of 5, and 23.08% for a value of 9.

Some categories contain fewer employees than others, so their rates may be less stable. This variable should not be treated as a simple linear predictor of attrition based on these descriptive comparisons alone.

---

## 8. Key Business Insights

The most important findings from the exploratory analysis are:

1. **Overall attrition:** Approximately 16.12% of employees in the dataset left the organization.
2. **Job-role differences:** Sales Representatives have the highest observed job-role attrition rate, approximately 39.76%, while Research Directors have the lowest, approximately 2.50%.
3. **Overtime association:** Attrition is approximately 30.53% among employees working overtime, compared with 10.44% among those not working overtime.
4. **Early-tenure retention:** Employees with 0–1 years at the company have an attrition rate of approximately 34.88%, compared with 8.13% among employees with 11+ years.
5. **Younger employees:** The 18–24 age group has the highest observed age-group attrition rate, approximately 38.20%.
6. **Job satisfaction:** Lower job satisfaction is associated with higher attrition across the workforce and within Sales Representatives.
7. **Work environment:** Employees with environment satisfaction level 1 have an attrition rate of approximately 25.35%, compared with approximately 13.45% at level 4.
8. **Business travel:** Frequent business travel is associated with higher attrition than non-travel.
9. **Commuting distance:** The Far distance group has a higher observed attrition rate than the Near group.
10. **Non-linear relationships:** Work-life balance, stock option level, time since last promotion, and number of companies previously worked for do not show simple, consistent linear patterns.

---

## 9. Business Recommendations

Based on the observed patterns, the following actions could be considered for further investigation.

### 9.1 Investigate Sales Representative Attrition

Examine workload, compensation, job satisfaction, overtime expectations, career progression, and management support among Sales Representatives.

Their high observed attrition rate makes this group a priority for more detailed analysis.

### 9.2 Strengthen Early-Tenure Support

Review onboarding, mentoring, training, manager check-ins, and early career development for employees in their first year at the company.

The high attrition rate among employees with 0–1 years of tenure suggests that early employee experience deserves attention.

### 9.3 Review Overtime and Workload

Assess how overtime is distributed, whether workload expectations are sustainable, and whether employees have adequate recovery time and support.

Further analysis should establish whether overtime patterns differ by department, role, and tenure.

### 9.4 Improve Employee Satisfaction

Gather employee feedback to understand low job satisfaction and environment satisfaction. Potential areas to examine include workplace conditions, communication, management practices, and employee support.

### 9.5 Examine Travel and Commuting Demands

Review frequent business travel and commuting challenges to determine whether more flexible arrangements or better support could improve employee experience.

### 9.6 Investigate Compensation and Career Development

Compare compensation, job levels, promotion history, and opportunities for advancement across relevant employee groups.

The descriptive findings can guide further investigation but are not sufficient on their own to justify changes to compensation or promotion policies.

### 9.7 Use Multiple Factors Together

Avoid making retention decisions based on a single characteristic. Explore how role, tenure, satisfaction, overtime, compensation, and travel overlap before designing targeted interventions.

**Important:** These recommendations are proposed actions based on descriptive patterns. Their effectiveness would need to be evaluated using additional evidence and follow-up analysis.

---

## 10. Limitations

- The project uses a single HR analytics dataset, so findings may not generalize to other organizations or time periods.
- The analysis is descriptive and does not establish causal relationships.
- The dataset provides employee-level observations, but the analysis does not establish the timing or reasons behind each departure.
- Some categories contain fewer employees, which can make their attrition percentages less stable.
- Grouping numerical variables makes patterns easier to communicate but can hide variation within each group.
- Outlier identification does not mean that an observation is erroneous. High-income observations were identified for review rather than automatically removed.
- Some relationships are non-linear, so higher or lower category values do not always correspond to a consistent change in attrition.
- The project does not currently use machine learning to predict which employees will leave.
- The recommendations have not been tested through an intervention or causal evaluation.

---

## 11. Conclusion

This exploratory analysis examined employee attrition across job roles, departments, demographics, tenure, compensation, satisfaction, overtime, travel, and other workforce characteristics.

The most notable patterns include higher attrition among Sales Representatives, employees working overtime, employees in their first year at the company, and employees reporting the lowest job satisfaction or environment satisfaction levels.

These findings provide a starting point for targeted retention investigations. They can help HR teams identify employee groups and workplace factors that deserve further attention, while recognizing that descriptive associations do not establish the reasons employees leave.

The project demonstrates practical skills in data cleaning, exploratory data analysis, feature grouping, cross-tabulation, percentage-based comparisons, statistical summaries, visualization, and translating analytical findings into business recommendations.

---

## 12. How to Run the Project

### Prerequisites

Install Python and the required libraries. A virtual environment is recommended.

### Install dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Run the notebook

1. Clone or download this repository.
2. Open the project folder in Visual Studio Code.
3. Ensure the dataset is available at `data/employee_attrition.csv`.
4. Open `notebooks/hr_analytics_final.ipynb`.
5. Select the appropriate Python kernel.
6. Run the notebook cells from top to bottom.

**Note:** The notebook uses relative file paths. Run it from the expected project structure, and check the dataset path if the notebook cannot locate the CSV file.

---

## 13. Future Improvements

Potential extensions to this project include:

- Building an interactive HR analytics dashboard in Power BI.
- Conducting deeper statistical analysis of attrition patterns.
- Comparing attrition across combinations of employee characteristics.
- Investigating relationships between compensation, satisfaction, tenure, and job role.
- Developing and evaluating a machine-learning attrition prediction model as a separate extension.
- Adding additional visualizations and exporting selected charts to the `outputs/` directory.

These are possible future improvements and are not claimed as completed work in the current EDA project.

---

## 14. Author

**Nazreen Shanavaz**

B.Tech in Computer Science and Engineering

