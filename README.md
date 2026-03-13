# Hospital Emergency Room Analysis – Power BI Dashboard

## Project Overview
This project presents an interactive **Power BI dashboard** designed to analyze hospital emergency room (ER) operations and patient flow. The dashboard helps monitor key metrics such as patient volume, wait times, triage levels, and admission trends.

The goal of this project is to demonstrate practical **data analysis, data modeling, and visualization skills using Power BI**.

This project was developed as part of a **Data Analyst course project**.

---

## Dataset

The dataset contains simulated hospital emergency room data for **100 patient visits**.

### Data includes:

- Patient ID
- Visit ID
- Visit Date
- Arrival Time
- Age
- Gender
- City
- Triage Level
- Wait Time
- Treatment Type
- Doctor Assigned
- Disposition (Admitted / Discharged)

The dataset was imported from **Excel** and processed inside **Power BI**.

---

## Tools & Technologies

- Power BI Desktop
- DAX (Data Analysis Expressions)
- Excel
- Data Modeling
- Data Visualization

---

## Data Preparation

Steps performed in Power BI:

1. Imported dataset using **Get Data → Excel**
2. Verified and corrected column data types
3. Created calculated columns for analysis
4. Built DAX measures for KPIs
5. Organized measures into a **_Measures table**
6. Designed an interactive two-page dashboard

---

## Calculated Columns

### Age Group

```DAX
Age Group =
SWITCH(
    TRUE(),
    [Age] < 18, "Child",
    [Age] <= 40, "Youth",
    [Age] <= 60, "Adult",
    "Senior"
)
```

### Wait Category

```DAX
Wait Category =
IF(
    [Wait_Time_Min] <= 30,
    "Within 30 mins",
    "Above 30 mins"
)
```

These calculated columns help categorize patients for better analysis.

---

## DAX Measures

### Total Patients

```DAX
Total Patients =
COUNT(Patient_Visits[Visit_ID])
```

### Average Wait Time

```DAX
Avg Wait Time =
AVERAGE(Patient_Visits[Wait_Time_Min])
```

### Admission Rate

```DAX
Admission Rate =
DIVIDE(
    CALCULATE(
        COUNT(Patient_Visits[Visit_ID]),
        Patient_Visits[Disposition] = "Admitted"
    ),
    [Total Patients]
)
```

### Critical Cases

```DAX
Critical Cases =
CALCULATE(
    COUNT(Patient_Visits[Visit_ID]),
    Patient_Visits[Triage_Level] = "Critical"
)
```

---

## Dashboard Structure

The Power BI report contains **two pages**.

### Page 1 – ER Overview

This page provides a high-level overview of emergency room performance.

Visuals included:

- KPI Cards (Total Patients, Avg Wait Time, Admission Rate)
- Patient Volume Trend (Line Chart)
- Patients by Department (Bar Chart)
- Interactive slicers

---

### Page 2 – Triage & Patient Analysis

This page focuses on patient distribution and treatment patterns.

Visuals included:

- Triage Level Distribution (Donut Chart)
- Patients by Age Group (Column Chart)
- Gender Distribution by Department
- Wait Time Performance

---

## Key Insights

The dashboard helps analyze:

- Emergency room patient volume
- Wait time performance
- Critical triage cases
- Department workload
- Patient demographics

This helps hospitals understand operational performance and identify areas for improvement.

---

## Learning Outcomes

This project demonstrates skills in:

- Data modeling in Power BI
- DAX calculations
- Dashboard design
- Interactive data visualization
- Data-driven analysis

---

## Author

**Deep Parulekar**

Aspiring Data Analyst skilled in:

- Power BI
- SQL
- Excel
- Tableau
- Data Visualization
