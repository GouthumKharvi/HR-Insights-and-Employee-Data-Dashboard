# HR-Insights-and-Employee-Data-Dashboard
This Tableau dashboard provides HR managers with a clear view of workforce data, including key metrics, demographics, and income analysis. It tracks hires, terminations, department distributions, and salary variations, with detailed employee records and filters for in-depth analysis.



https://github.com/user-attachments/assets/356817a0-738a-4aa8-ae67-c806668c1a08


Certainly! Here's a refined and formatted version of your project steps and description, suitable for inclusion in a GitHub README:

---

# HR Dashboard Project

## Overview

The HR Dashboard project aims to create a comprehensive dashboard for HR managers to analyze human resources data. The dashboard will provide both summary views for high-level insights and detailed employee records for in-depth analysis.

## User Story

**As an HR manager,** I want a comprehensive dashboard to analyze human resources data, providing both summary views for high-level insights and detailed employee records for in-depth analysis.

## Summary View

The summary view will be divided into three main sections: **Overview**, **Demographics**, and **Income Analysis**.

### Overview

- **Total Employees**: Display the total number of hired, active, and terminated employees.
  - Use BANS to highlight big data and measures within the dashboard.
- **Employee Trends**: Visualize the total number of hired and terminated employees over the years.
  - **Chart Type**: Line Chart.
- **Breakdown by Department and Job Title**: Present a breakdown of total employees by department and job titles.
  - **Chart Type**: Bar Chart.
- **HQ vs. Branches**: Compare total employees between headquarters (HQ) and branches (New York is the HQ).
  - **Chart Type**: Bar Chart.
  - **Calculated Field**:
    ```sql
    CASE [State]
        WHEN 'New York' THEN 'HQ'
        ELSE 'Branch'
    END
    ```
- **Employee Distribution by City and State**: Show the distribution of employees by city and state.
  - **Chart Type**: Map.

### Demographics

- **Gender Ratio**: Present the gender ratio in the company.
  - **Chart Type**: Pie Chart.
- **Age and Education Distribution**: Visualize the distribution of employees across age groups and education levels.
  - **Chart Type**: Heatmap.
  - **Age Groups Calculation**:
    ```sql
    IF [Age] < 25 THEN '>25'
    ELSEIF [Age] >=25 AND [Age] <35 THEN '25-34'
    ELSEIF [Age] >=35 AND [Age] <45 THEN '35-44'
    ELSEIF [Age] >=45 AND [Age] <55 THEN '45-54'
    ELSEIF [Age] >=55 THEN '55+'
    END
    ```
- **Employee Count by Age Group and Education Level**: Show the total number of employees within each age group and education level.
  - **Chart Type**: Bar Chart.
- **Correlation Between Education and Performance**: Present the correlation between employees' educational backgrounds and their performance ratings.
  - **Chart Type**: Heatmap.

### Income Analysis

- **Salary Comparison**: Compare salaries across different education levels for both genders to identify any discrepancies or patterns.
  - **Chart Type**: Barbell Chart.
- **Age vs. Salary**: Present how age correlates with salary for employees in each department.
  - **Chart Type**: Scatter Plot.

## Building Data Sources

1. **Collect Data**
2. **Connect the Data**
3. **Build Data Model**
4. **Check Data Quality**
5. **Check Data Types**
6. **Understand and Explore Data**

## Hierarchy (Department & Job Title)

- Build a relationship between dimensions to allow users to drill down to finer details.
- **Implementation**: Drag and drop job title to department in the left panel.

## Building Charts

1. **Analyze Requirements and Choose Chart Types**
2. **Initial Format of Sheet**
   - **Format**: Workbook -> Trebuchet MS [Entire Project]
   - **Colors**:
     - Primary Color: `#03c4a1`
     - Secondary Color: `#c52a87`
     - Neutral Color: `#777777`
     - Background Color: `#f5f5f5`
   - **Apply Color**: Format -> Workbook -> More Colors -> `#777777`
   - **Background Color**: Format -> Shading -> First Dark Color
   - **Use Entire View for all worksheets**
3. **Create Calculated Fields & Test**
   - **Total Employees**: `COUNT([Employee ID])`
   - **Terminated Employees**: 
     ```sql
     COUNT(IF NOT ISNULL([Termdate]) THEN [Employee ID] END)
     ```
   - **Active Employees**:
     ```sql
     COUNT(IF ISNULL([Termdate]) THEN [Employee ID] END)
     ```
4. **Build and Format Charts**
   - **Terminated Employees**: Continuous
   - **Active Employees**: Continuous
   - **Employee Trends**: Line Chart
   - **Breakdown by Department and Job Title**: Bar Chart
   - **HQ vs. Branches**: Bar Chart
   - **Distribution by City and State**: Map
   - **Gender Ratio**: Pie Chart
   - **Age and Education Distribution**: Heatmap
   - **Salary Comparison**: Barbell Chart
   - **Age vs. Salary**: Scatter Plot

## Building HR Summary Dashboard

1. **Plan the Dashboard**
   - Dashboard Mockup
   - Container Mockup
2. **Create Container Structure**
3. **Put All Together**
4. **Fixing Colors**
5. **Fix Texts**
6. **Refine Charts**
7. **Fix Spacing**
   - **Outer Padding**: 20
   - **Inner Padding**: 7
   - **Spacing Between Charts**: 10
8. **Fix Tooltips**
   - Highlighted measure and words should be bold and grey
9. **Add Filters & Legends**
   - Legends
   - Action Filters
   - Quick Filters
10. **Add Logos & Icons**

## Building HR Detailed Chart

### Employee Records View

- Provide a comprehensive list of all employees with necessary information such as name, department, position, gender, age, education, and salary.
- Users should be able to filter the list based on any of the available columns.

---

