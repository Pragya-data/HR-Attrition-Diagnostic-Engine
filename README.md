# HR Attrition Diagnostic Engine

## 📌 Project Overview
Most human resources dashboards report strictly on historical data—telling leadership *who* left the company. The goal of this project was to move beyond standard reporting and build a **Predictive Diagnostic Engine** that identifies *who is at risk of leaving next*. 

Built entirely in Power BI, this project abandons default corporate templates in favor of a containerized, web-app UI design and advanced diagnostic analytics.

## 🗂️ Table of Contents
- [The Business Problem](#the-business-problem)
- [UI/UX & App Architecture](#uiux--app-architecture)
- [Diagnostic Analytics: The Flight Risk Matrix](#diagnostic-analytics-the-flight-risk-matrix)
- [Dashboard Components](#dashboard-components)
- [Core DAX Measures](#core-dax-measures)
- [How to Interact](#how-to-interact)

---

## 🏢 The Business Problem
Employee turnover is a massive cost center. To mitigate this, HR leadership requires actionable intelligence on the root causes of attrition. This dashboard was developed to test the hypothesis that **compensation stagnation combined with specific tenure milestones** drives the highest flight risk.

**The Executive Insight:**
> Diagnostic analysis indicates a concentrated flight risk among newer employees experiencing compensation stagnation. As visualized in the Flight Risk Matrix, attrition is heavily isolated in the lower-left quadrant. Employees with both **below-average tenure** and **below-average salary hikes** represent the highest probability of turnover.

---

## 🎨 UI/UX & App Architecture
To ensure high user adoption, this dashboard was designed to mimic a proprietary SaaS application rather than a traditional spreadsheet.

* **Containerized Layout:** Visuals are isolated in stark white, 12px rounded cards with drop shadows to create depth and hierarchy against a custom canvas background.
* **Executive Sidebar:** A dedicated navigation and insight panel engineered to house the Department slicer and the dynamic executive summary.
* **FinTech Minimalist Palette:** Completely stripped of default blue/grey BI colors.
  * **Warm Ivory (`#FDFBF7`):** App Canvas Background.
  * **Deep Plum (`#4A235A`):** Retained Employees (Safe Zone) & Executive Sidebar.
  * **Mustard Gold (`#F4D03F`):** Attrited Employees (Alert/Action Required).

---

## 📊 Diagnostic Analytics: The Flight Risk Matrix
Instead of relying on basic pie charts, the centerpiece of this engine is a custom-built **Flight Risk Matrix**.

* **Methodology:** A scatter plot mapping `Tenure (Years)` against `Salary Raise %`.
* **Dynamic Thresholds:** Applied dynamic X-axis and Y-axis average lines directly into the visual to create four distinct analytical quadrants.
* **Result:** The matrix visually isolates high-risk employees in the bottom-left quadrant, allowing HR business partners to intervene before an employee resigns.

---

## 🖥️ Dashboard Components
The engine tracks employee data across several key vectors:
* **Top KPI Ribbon:** Total Employees, Attrition Rate, Attrition Count, and Average Tenure seamlessly blended into a top navigation bar.
* **Attrition by Job Role:** Identifying specific positions with the highest turnover volume.
* **Overtime Impact on Attrition:** 100% Stacked bar chart proving the correlation between extended hours and flight risk.
* **Demographic & Compensation Tracking:** Granular breakdowns of Attrition Count by Age Tier, Tenure, and Salary Raise %.

---

## ⚙️ Core DAX Measures
Behind the UI, the dashboard relies on a clean, optimized data model powered by precise DAX calculations:

```dax
Total Employees = COUNTROWS('HR_Attrition_Data')

Attrition Count = CALCULATE(COUNTROWS('HR_Attrition_Data'), 'HR_Attrition_Data'[Attrition] = "Yes")

Attrition Rate = DIVIDE([Attrition Count], [Total Employees], 0)

Average Tenure = AVERAGE('HR_Attrition_Data'[Years_At_Company])
```

## 💻 How to Interact
1. Download the `.pbix` file from this repository.
2. Open with **Power BI Desktop**.
3. Use the **Department** dropdown in the Deep Plum sidebar to filter the diagnostic matrix across R&D, Sales, and HR.
4. Hover over individual data points in the Flight Risk Matrix to view specific employee profiles.

---
*Designed and Developed by **Pragya Singh Gour***
