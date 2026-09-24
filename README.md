# HR Attrition & Workforce Analytics Dashboard (Excel)

An end-to-end, Excel-only workforce analytics project built on the IBM HR Analytics Employee Attrition dataset — from raw data cleaning to an interactive, slicer-driven dashboard. Built to demonstrate advanced Excel skills (Tables, PivotTables, nested formulas, conditional formatting, slicers) independent of any SQL/Power BI tooling.

![Dashboard Preview](screenshots/dashboard-preview.png)

## 📊 Overview

This project analyzes employee attrition patterns across department, age, tenure, salary band, and overtime status, and scores every employee on a custom **Attrition Risk Model** built from 8 weighted behavioral/engagement signals — entirely with native Excel formulas.

**Dataset:** [IBM HR Analytics Employee Attrition (Kaggle)](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) — 1,470 employee records, 35 original fields.

## 🗂️ Workbook Structure

| Sheet | Purpose |
|---|---|
| `RAW_DATA` | Untouched source data, exactly as exported |
| `CLEANED_DATA` | Deduplicated, format-corrected table (`HR_TABLE`) with 4 derived helper columns |
| `ANALYSIS` | PivotTables driving every chart, plus supporting KPI formulas |
| `DASHBOARD` | Final interactive report — KPI cards, 5 charts, and cross-filtering slicers |

## 🧮 Key Formulas & Techniques

**Derived columns** (added to the cleaned table):
- `AgeGroup`, `TenureBucket`, `SalaryBand` — nested `IF()` bucketing
- `AttritionFlag` — binary flag for pivot-friendly rate calculations

**Attrition Risk Score** — a transparent, weighted scoring model (max 100 points) built from nested `IF()` logic across 8 factors: OverTime, Job Satisfaction, Environment Satisfaction, Work-Life Balance, Years Since Last Promotion, Number of Companies Worked, Distance From Home, and Stock Option Level. Employees are bucketed into **High / Medium / Low Risk**.

**Model validation:** `AVERAGEIFS()` comparison shows employees who actually left the company scored **38** on average vs. **27** for employees who stayed — an 11-point gap confirming the score meaningfully separates leavers from stayers.

## 📈 Dashboard Visuals

- **4 live KPI cards** (Overall Attrition Rate, Total Headcount, Avg. Risk Score — Leavers, Avg. Risk Score — Stayers), built as shapes dynamically linked to PivotTable outputs so they respond to slicer filtering
- **Attrition Rate by Department** — clustered bar
- **Age Group × Tenure Attrition** — clustered column
- **Risk Bucket Distribution** — doughnut chart, color-coded (red/amber/green)
- **Salary Band × OverTime Attrition** — clustered bar
- **Attrition Rate by Job Role** — sorted clustered bar
- **Slicers** (Department, and expandable to JobRole/Gender/OverTime) — connected to every underlying PivotTable so one click filters the entire dashboard simultaneously

## 🛠️ Skills Demonstrated

- Excel Tables & structured references
- PivotTables & PivotCharts
- Nested `IF()`, `AVERAGEIFS()`, `COUNTIFS()`, `XLOOKUP()`/`VLOOKUP()`
- Conditional formatting (color scales / heatmap logic)
- Slicers & multi-pivot report connections
- Dashboard design: KPI cards via linked shapes, consistent theming, chart decluttering

## 📁 Repo Structure

```
hr-attrition-excel-dashboard/
├── README.md
├── HR-Attrition-Dashboard.xlsx      ← full interactive workbook (add this yourself)
├── dataset/
│   └── HR-Employee-Attrition-source.xlsx   ← original raw dataset
└── screenshots/
    └── dashboard-preview.png        ← static preview of the dashboard tab
```

## 👤 Author

Built by Vijay as part of a portfolio series showcasing Excel, SQL, and Power BI skills separately — see also the companion SQL and Power BI projects in this portfolio.
