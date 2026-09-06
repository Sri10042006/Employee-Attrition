# Employee Attrition Analysis

Analysis of employee attrition data to identify the key factors driving turnover, using Python for data cleaning and EDA, and Power BI for an interactive dashboard.

## 🎯 Objective
Identify why employees leave, which segments are highest-risk, and provide data-backed recommendations to reduce attrition.

## 📊 Dataset
- **Source:** IBM HR Analytics Employee Attrition dataset
- **Size:** 1,470 employees, 35 original columns (31 after cleaning)
- **Target:** `Attrition` (Yes/No)

## 🔑 Key Findings
- **Overall attrition rate: 16.12%**
- **Overtime is the strongest driver** — employees working overtime leave at 30.5%, nearly 3x the rate of those who don't (10.4%)
- **Overtime compounds with other factors** — Sales Representatives working overtime hit **66.7% attrition**; single employees working overtime hit **49.6%**
- Junior-level employees (Job Level 1) leave at 26.3% vs. 4.7% at Job Level 4
- Leavers are on average 4 years younger, earn ~30% less, and have ~2 fewer years of tenure than those who stay

## 🛠️ Tools Used
- **Python** (pandas, matplotlib, seaborn) — data cleaning, EDA, KPI calculation
- **Power BI** — interactive 3-page dashboard

## 📁 Repository Contents
| File | Description |
|---|---|
| `Employee_Attrition_Final_Report.docx` | Full report: data cleaning, EDA, KPIs, segment analysis, insights & recommendations |
| `HR_Attrition_Cleaned.csv` | Cleaned dataset, ready for analysis or BI tools |
| `Employee_Attrition.pbix` | Interactive Power BI dashboard (open in Power BI Desktop) |
| `HR_Attrition_Dashboard.pdf` | Static PDF export of the dashboard (viewable without Power BI) |

## 📈 Dashboard Overview
**Page 1 — Executive Overview:** KPI cards (attrition rate, headcount, avg income, avg tenure) + attrition by department + attrition split donut

**Page 2 — Attrition Drivers:** Attrition rate by overtime, job role, marital status, business travel, job level, and work-life balance, with interactive slicers

**Page 3 — Demographics & Comparison:** Income, age, and tenure compared between employees who stayed vs. left, plus gender and education field breakdowns

## 💡 Top Recommendations
1. Audit and cap overtime, starting with Sales and Laboratory roles
2. Targeted retention programs for Sales Representatives and Lab Technicians
3. Structured onboarding/mentorship for early-tenure, junior employees
4. Review compensation for junior-level and single employees

See the full report for detailed methodology, all findings, and complete recommendations.
