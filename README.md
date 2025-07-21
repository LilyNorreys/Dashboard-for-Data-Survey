# Data Professional Survey Results Breakdown

### Dashboard Preview

<img width="587" height="332" alt="Dashboard Preview" src="https://github.com/user-attachments/assets/679b6f99-2641-44fa-a903-bf50b7c03708" />

---

## Problem Statement

This project presents a Power BI dashboard analyzing survey data collected by **Alex The Analyst**. The survey consisted of **630 responses** from data professionals who answered questions about their careers. The survey was distributed through various social media platforms, including LinkedIn and Twitter.

The survey covered the following topics:

- Yearly salary ranges  
- Industries participants work in  
- Favorite programming languages  
- Career happiness ratings across multiple variables  
- General demographics (such as country of residence)

---

## Steps Followed

### Step 1: Load Data
- Imported the dataset (CSV format) into **Power BI Desktop**

### Step 2: Data Transformation
- Opened **Power Query Editor** to begin transformation

### Step 3: Data Cleaning
- Removed unnecessary columns  
- Split multi-response "Other" fields by delimiter to standardize data  
- Cleaned salary range field:
  - Removed non-numeric characters (`-`, `+`, `k`)  
  - Split into minimum and maximum values  
  - Created an **average salary** column using a Power Query formula:

```powerquery
Average Salary = (MinSalary + MaxSalary) / 2
```

- Converted data type from text to decimal

### Step 4: Visualizations Added
- **Cards**:
  - Total number of participants
  - Average participant salary

- **Stacked Bar Chart**:
  - Average salary by data job title (with custom axis labels and legends)

- **Stacked Column Chart**:
  - Favorite programming language by job title

- **Pie Chart**:
  - Demographics by country, with interactivity to explore salary and satisfaction by region

- **Donut Chart**:
  - Perceived difficulty entering the data profession

- **Gauge Chart**:
  - Average career happiness rating across variables

### Step 5: DAX Calculation for Overall Happiness

Used the following DAX formula to calculate the overall average career happiness rating across multiple survey variables:

```dax
AvgHappinessTrue = 
DIVIDE(
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Coworkers)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Learning New Things)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Management)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Upward Mobility)]) +
    SUM('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Work/Life Balance)]),

    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Coworkers)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Learning New Things)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Management)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Upward Mobility)]) +
    COUNT('Data Professional Survey'[Q6 - How Happy are you in your Current Position with the following? (Work/Life Balance)])
)
```

### Step 6: Report Styling
- Applied a custom theme using Power BI’s **View > Themes** feature  
- Standardized visual formatting including axis labels, titles, and legends  

### Step 7: Dashboard Delivery
- Delivered as a **single, interactive Power BI dashboard**  
- Supports filtering and cross-highlighting to explore insights interactively  

---

## File Structure

```
project-root/
├── README.md
├── DataProfessionalSurvey.csv
└── PowerBI_Dashboard.pbix
```

---
