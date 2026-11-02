# HR Analytics: Boosting Retention with Data Insights at Adecco India

An Excel-based HR analytics case study that investigates why employees leave, with a focus on junior sales staff, and recommends actions to improve retention.

## Problem

Adecco India is seeing high employee turnover, especially among junior employees in the Sales department. Turnover raises hiring and training costs and hurts productivity and morale. This project analyses HR data to find the factors behind attrition and turn them into targeted retention strategies.

## Dataset

- **File:** `WA_Fn-UseC_-HR-Employee-Attrition.csv`
- **Source:** HR Analytics Case Study on Kaggle (Bhanu Pratap Biswas)
- **Size:** 1,470 employees, 35 fields, no missing values
- **Target:** `Attrition` (Yes/No). 237 employees left.

A full data dictionary is in the Case Study Document.

## Project Contents

| Deliverable | Description |
|---|---|
| `Adecco_HR_Analytics_Solution.xlsx` | Analysis workbook answering all 20 questions with live formulas and charts |
| Case Study Document | Problem statement, stakeholders, metrics, data dictionary and the 20 questions |
| Solution Guide | Worked answers, interpretation, recommendations and limitations |
| `README.md` | This file |

### Workbook sheets

| Sheet | What it holds |
|---|---|
| Summary | Headline KPIs, top 3 drivers, key findings, recommendations, method notes |
| Basic Q1-Q10 | Overall attrition, department, age, job role, gender test, income, distance, performance, overtime, tenure |
| Medium Q1-Q10 | Correlation ranking, job involvement, age vs satisfaction, marital status, training, work-life balance, stock options, tenure, travel, promotion gap |
| Sales Deep-Dive | Attrition among junior sales staff (Sales department, JobLevel 1) |
| Data | Raw data plus four helper columns (orange headers) |

## How to Use

1. Open `Adecco_HR_Analytics_Solution.xlsx` in Excel (or LibreOffice).
2. Start at **Summary**, then read the analysis sheets in order.
3. Every table is a formula on the **Data** sheet, so replacing the data and recalculating updates the results. The interpretation lines (amber rows) are static text and need rewriting if the data changes.

## Methods

- **Attrition rate** = leavers in group / headcount of group, using `COUNTIF` / `COUNTIFS` (equivalent to a PivotTable calculated field).
- **Averages** with `AVERAGEIF` / `AVERAGEIFS`.
- **Driver ranking:** `CORREL` between each variable and a 0/1 `AttritionFlag`, ranked by absolute value with `RANK` and `INDEX/MATCH`.
- **Gender test:** two-proportion z-test (equivalent to a t-test on the 0/1 flag).
- **Banded tables** replace the scatter plots requested in the brief, because 1-4 scales and Yes/No data plot as unreadable stripes.
- **Helper columns on Data:** `AttritionFlag`, `OverTimeFlag`, `SingleFlag`, `JuniorSales`.
- **"Junior"** is defined as `JobLevel = 1`.

## Key Findings

- Overall attrition is **16.1%** (237 of 1,470).
- **Sales** is highest at 20.6%. **Level-1 Sales** staff leave at **42.1%**; Sales Representatives at 39.8%.
- Top 3 drivers: **overtime** (30.5% vs 10.4% without), **being single** (25.5%), and **fewer total working years**.
- Leavers earn about **30% less** than stayers. Staff with no stock options leave at 24% vs 8-9% with level 1-2 options.
- Higher-risk groups: frequent travellers (24.9%), low job involvement (33.7%), zero training (27.8%).
- **No meaningful effect:** gender (p = 0.26), age vs satisfaction, tenure vs satisfaction, work-life balance vs performance, promotion gap vs performance.
- Performance ratings use only 3 and 4, so they do not distinguish employees.

## Recommendations

1. Cap and monitor overtime.
2. Review entry-level pay and add retention incentives.
3. Extend stock/ESOP grants to Level 1-2 staff.
4. Build a clear career path and mentoring for junior staff.
5. Set a minimum training commitment.
6. Revise the travel policy for frequent travellers.
7. Offer flexible commute options for distances over 10 km.
8. Recalibrate the rating scale and add pulse surveys and exit-interview analysis.

## Limitations

- Correlation is not causation, and effect sizes are modest (all correlations below 0.25).
- Some sub-groups are small (for example 22 junior sales staff on overtime), so their rates are directional.
- The dataset has three departments (Sales, R&D, HR), not the engineering/marketing/support split in the case narrative.
- Monthly income is in the dataset's own currency units.

## Ethics and Privacy

Employee data is personal. Anonymise records before sharing, restrict access, and use findings as group-level patterns to prioritise support, never to judge individuals. Avoid using protected characteristics such as gender or marital status for individual decisions.

## Suggested Repository Structure

```
adecco-hr-analytics/
├── README.md
├── data/
│   └── WA_Fn-UseC_-HR-Employee-Attrition.csv
├── analysis/
│   └── Adecco_HR_Analytics_Solution.xlsx
└── docs/
    ├── Case_Study.pdf
    └── Solution_Guide.pdf
```

## Tools

Microsoft Excel (COUNTIFS, AVERAGEIFS, CORREL, RANK, INDEX/MATCH, charts).
