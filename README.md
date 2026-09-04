# Employee-Attrition
# Employee Attrition Analysis Project

## Project Objective
Analyze employee attrition data to identify the key factors driving employee turnover, and present findings through visualizations, business insights, and actionable recommendations for HR/management.

## Dataset
- **Source:** IBM HR Analytics Employee Attrition dataset
- **Size:** 1,470 rows × 35 columns (original)
- **Target variable:** `Attrition` (Yes/No)

---

## Progress So Far

### ✅ Stage 1 — Data Understanding
- Loaded dataset and reviewed structure using `.info()`, `.describe()`, `.head()`, `.shape()`
- Manually reviewed all 35 columns and categorized them by theme (demographics, job-related, compensation, satisfaction, tenure)

### ✅ Stage 2 — Initial Inspection
- Checked null values across all columns → **0 missing values**
- Checked duplicate rows → **0 duplicates**
- Reviewed data types for all columns

### ✅ Stage 3 — Data Cleaning
- Verified zero-variance columns using `.unique()`:
  - `EmployeeCount` → constant value `[1]`
  - `StandardHours` → constant value `[80]`
  - `Over18` → constant value `['Y']`
- Dropped these along with the non-informative `EmployeeNumber` (ID column)
- **Shape after cleaning: 1,470 rows × 31 columns**
- Checked numeric columns for outliers using boxplots
- **Decision:** No outliers removed — all extreme values (e.g., high `TotalWorkingYears`, `MonthlyIncome`) represent genuine, valid employee records, not data errors

### ✅ Stage 4 — Column Classification
- **Numerical (continuous):** Age, DailyRate, DistanceFromHome, HourlyRate, MonthlyIncome, MonthlyRate, NumCompaniesWorked, PercentSalaryHike, TotalWorkingYears, TrainingTimesLastYear, YearsAtCompany, YearsInCurrentRole, YearsSinceLastPromotion, YearsWithCurrManager
- **Ordinal categorical (rating scales stored as numbers):** Education, EnvironmentSatisfaction, JobInvolvement, JobLevel, JobSatisfaction, PerformanceRating, RelationshipSatisfaction, StockOptionLevel, WorkLifeBalance
- **Nominal categorical (text):** Attrition (target), BusinessTravel, Department, EducationField, Gender, JobRole, MaritalStatus, OverTime

### ✅ Stage 5 — Exploratory Data Analysis (EDA)
- **Target balance:** Attrition is imbalanced — 83.88% stayed (No), 16.12% left (Yes)
- Ran univariate value counts on key categorical columns (Department, JobRole, Gender, MaritalStatus, OverTime, BusinessTravel)
- Ran bivariate analysis: attrition rate (%) calculated per segment (not raw counts, to avoid group-size bias)
- Built a correlation heatmap for numeric variables vs `Attrition_Flag`
  - All numeric correlations were weak (max ~0.17) — confirms that **categorical/ordinal factors (OverTime, JobRole, JobLevel) are stronger attrition predictors than continuous numeric variables** in this dataset

### ✅ Stage 6 — KPI Calculation
| KPI | Value |
|---|---|
| Overall Attrition Rate | 16.12% |
| Avg Tenure – Stayed | 7.37 years |
| Avg Tenure – Left | 5.13 years |
| Avg Monthly Income – Stayed | $6,833 |
| Avg Monthly Income – Left | $4,787 |
| Attrition Rate – No Overtime | 10.44% |
| Attrition Rate – Overtime | 30.53% |
| Highest-Risk Department | Sales (20.63%) |
| Lowest-Risk Department | R&D (13.84%) |
| Avg Age – Stayed | 37.56 |
| Avg Age – Left | 33.61 |

### ✅ Stage 7 — Segment & Compounding Risk Analysis
Key finding: **OverTime acts as a risk multiplier**, not just an independent factor.
- Single + Overtime → **49.6%** attrition (vs 16.2% for Single + No Overtime)
- Sales Representative + Overtime → **66.7%** attrition (vs 28.8% without overtime)
- Laboratory Technician + Overtime → **50.0%** attrition
- Sales Dept + Overtime → 37.5% vs 13.8% without overtime

**Highest-risk employee profile identified:** Young, single, junior-level employee in Sales Representative or Lab Technician role, working overtime, traveling frequently, with lower job satisfaction/involvement.

### ✅ Stage 8 — Visualizations (Python/Seaborn)
Built exploratory charts to validate and visualize all findings above:
- Attrition Rate by OverTime
- Attrition Rate by Department
- Attrition Rate by Job Role
- Monthly Income: Stayed vs Left (boxplot)
- Age: Stayed vs Left (boxplot)
- Attrition Rate by Work-Life Balance

Also noted: some segments (e.g., HR department, WorkLifeBalance=4) show wide confidence intervals due to small sample sizes — flagged as lower-confidence findings rather than firm trends.

### ✅ Data Export
- Cleaned dataset exported as `HR_Attrition_Cleaned.csv` (1,470 rows × 31+ columns, includes `Attrition_Flag` numeric column)
- Downloaded and ready for import into Power BI

---

## In Progress

### ⏳ Stage 9 — Interactive Dashboard (Power BI)
Dashboard plan finalized as **3 pages**:

**Page 1 — Executive Overview**
- KPI cards: Overall Attrition Rate, Total Employees, Attrition Count, Avg Income, Avg Tenure
- Charts: Attrition by Department, Attrition Yes/No donut

**Page 2 — Attrition Drivers (Deep Dive)**
- Charts: OverTime, JobRole, MaritalStatus, BusinessTravel, JobLevel, WorkLifeBalance, JobSatisfaction
- Slicers: Department, Gender, OverTime

**Page 3 — Employee Demographics & Comparison**
- Charts: Age/Income/Tenure comparison (Stayed vs Left), Gender breakdown, Education field breakdown
- Slicers: Department, Gender, OverTime

Currently building Page 1 in Power BI Desktop.

---

## Remaining Steps

- [ ] Complete Power BI dashboard (Pages 1–3)
- [ ] Add interactivity (slicers/filters)
- [ ] Write final Data Cleaning Report (formal write-up)
- [ ] Write final EDA Report (formal write-up)
- [ ] Write Business Insights & Recommendations section

---

## Tools Used
- **Python** (pandas, matplotlib, seaborn) — data cleaning, EDA, KPI calculation, visualization prototyping
- **Power BI** — interactive dashboard (in progress)

## Files
- `HR_Attrition_Cleaned.csv` — cleaned dataset, ready for BI tools
