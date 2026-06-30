# Loan Default Analysis Dashboard

### Dashboard Link : https://app.powerbi.com/links/91RmFlhU4j?ctid=365342f6-b127-4d87-abba-46596874a980&pbi_source=linkShare&bookmarkGuid=bdaccc67-d27f-476f-8874-5b5f9c413085

---

## Problem Statement

This dashboard helps banks, financial institutions, credit risk analysts, and business stakeholders understand the overall performance of their loan portfolio by analyzing borrower demographics, loan characteristics, default trends, and financial risk indicators. It provides valuable insights into loan distribution, borrower income, employment status, credit score categories, education levels, and default behavior, enabling organizations to make informed lending decisions and improve risk management strategies.

The report consolidates multiple loan-related metrics into a single interactive dashboard, allowing users to evaluate borrower profiles from different business perspectives. Through dynamic visualizations and interactive filtering, users can compare loan amounts across different purposes, analyze default rates based on employment type and credit score, study borrower demographics, and monitor year-over-year changes in loan performance.

By identifying high-risk borrower segments, monitoring historical default trends, and evaluating financial indicators, banks and lending institutions can optimize credit approval policies, reduce default risk, improve portfolio quality, and enhance overall business performance. The dashboard serves as a comprehensive Business Intelligence solution for transforming raw loan data into meaningful insights that support data-driven decision making.

---

## Steps Followed

* **Step 1 :** Load the loan default dataset into **Power BI Desktop**. The dataset contains borrower demographics, loan information, employment details, income, credit score categories, mortgage details, education level, marital status, loan purpose, and loan default information.

* **Step 2 :** Open **Power Query Editor** and inspect the dataset for data quality by reviewing column names, verifying data types, checking for missing values, and ensuring data consistency before designing the dashboard.

* **Step 3 :** It was observed that the dataset contains information related to loan amounts, annual income, employment type, loan purpose, credit score category, age group, marital status, education type, mortgage status, dependents, loan issue year, and default status.

* **Step 4 :** Required data type conversions were performed to ensure numerical, categorical, and date-related columns were correctly recognized by Power BI for accurate analysis and visualization.

* **Step 5 :** The dataset was cleaned and transformed by handling inconsistencies, preparing categorical values, and organizing the data into a suitable format for reporting.

* **Step 6 :** After completing all required transformations, the cleaned dataset was loaded into the Power BI data model.

* **Step 7 :** A custom report theme was applied under the **View** tab to maintain a clean, professional, and consistent visual appearance throughout the dashboard.

* **Step 8 :** Appropriate relationships between tables were verified within the data model to ensure accurate filtering, aggregation, and interaction across report visuals.

* **Step 9 :** Business calculations were created using a combination of DAX measures and Power BI's built-in aggregation functions to analyze loan amounts, default rates, borrower income, year-over-year changes, and other financial indicators used throughout the report.

* **Step 10 :** Multiple KPI visuals and analytical charts were added to summarize important lending metrics and borrower characteristics.

These include:

(a) Loan Amount Analysis

(b) Default Rate Analysis

(c) Average Income Analysis

(d) Credit Score Analysis

(e) Year-over-Year Financial Analysis

* **Step 11 :** Interactive slicers were added to allow users to dynamically filter the report based on borrower and financial attributes.

The slicers include:

(a) Employment Type

(b) Income Bracket

(c) Credit Score Category

(d) Marital Status

(e) Age Groups

These slicers allow users to perform detailed loan analysis across different borrower segments.

* **Step 12 :** Various visualizations were created to analyze multiple business perspectives including:

- Area Charts

- Line Charts

- Clustered Column Charts

- Clustered Bar Charts

- Donut Charts

- Sankey Diagram

- KPI Cards

- Interactive Slicers

These visuals help users identify loan distribution, borrower demographics, employment trends, education patterns, credit score performance, financial risk, and default behavior.

* **Step 13 :** Interactive filters and cross-highlighting were enabled across report visuals, allowing users to drill down into specific borrower groups and financial categories by simply selecting any chart or slicer.

* **Step 14 :** Three separate report pages were designed to provide different analytical perspectives of the loan portfolio.

The report contains:

- Loan Default & Overview

- Applicant Demographic & Financial Profile

- Financial Risk Metrics

Each report page focuses on a different business objective while maintaining consistent navigation, formatting, and user experience.

* **Step 15 :** Analytical visuals were designed using appropriate chart types to compare borrower demographics, loan characteristics, financial performance, default behavior, and historical trends across multiple dimensions.

* **Step 16 :** Dynamic visual interactions were configured so that selecting any chart or slicer automatically filters all related visuals throughout the report, enabling users to perform interactive and detailed business analysis.

* **Step 17 :** Appropriate formatting, titles, legends, axis labels, data labels, tooltips, borders, color themes, and layout adjustments were applied to improve dashboard readability and provide a professional reporting experience.

* **Step 18 :** After completing dashboard development, validation, testing, and formatting, the report was published to **Power BI Service**, allowing users to securely access, interact with, and share the dashboard online.* **Step 19 :** Several DAX measures were created to calculate key business metrics and financial indicators used throughout the dashboard.

Following DAX expressions were written for the same,

---

## Default Rate (%)

```DAX
Default Rate (%) =
DIVIDE(
    CALCULATE(
        COUNTROWS(LoanData),
        LoanData[Default] = "Yes"
    ),
    COUNTROWS(LoanData),
    0
) * 100
```

A line chart was created to display the **Default Rate (%)** across different employment types and years.

This visualization helps financial institutions identify borrower segments with relatively higher default risk and monitor default trends over time.

---

## Average Income

```DAX
Average Income =
AVERAGE(LoanData[Income])
```

An area chart was designed to compare the **Average Income** across different employment categories.

This analysis helps understand income distribution among borrowers and evaluate its relationship with loan repayment behavior.

---

## Average Loan Amount

```DAX
Average Loan Amount =
AVERAGE(LoanData[LoanAmount])
```

Multiple visuals were created using this measure to compare average loan amounts across age groups, marital status, and credit score categories.

This enables users to identify borrower segments receiving comparatively higher loan amounts.

---

## Total Loan Amount

```DAX
Total Loan Amount =
SUM(LoanData[LoanAmount])
```

This measure was used throughout the dashboard to analyze loan distribution based on loan purpose, education type, mortgage status, and income brackets.

---

## YOY Loan Amount Change

```DAX
YOY Loan Amount Change =
VAR CurrentYear =
    [Total Loan Amount]

VAR PreviousYear =
    CALCULATE(
        [Total Loan Amount],
        SAMEPERIODLASTYEAR('Calendar'[Date])
    )

RETURN
DIVIDE(CurrentYear - PreviousYear, PreviousYear)
```

A line chart was designed to monitor the **Year-over-Year Loan Amount Change**, enabling users to evaluate annual lending growth and identify changes in lending patterns.

---

## YOY Default Loans Change

```DAX
YOY Default Loans Change =
VAR CurrentDefaults =
    [Default Loans]

VAR PreviousDefaults =
    CALCULATE(
        [Default Loans],
        SAMEPERIODLASTYEAR('Calendar'[Date])
    )

RETURN
DIVIDE(CurrentDefaults - PreviousDefaults, PreviousDefaults)
```

A line chart was created to analyze **Year-over-Year Default Loan Changes**, helping financial institutions evaluate changes in borrower default behavior over time.

---

## Median Loan Amount

```DAX
Median Loan Amount =
MEDIAN(LoanData[LoanAmount])
```

This measure was used to compare the median loan amount across different credit score categories, providing additional insight into borrower lending behavior.

---

## Sankey Analysis

A Sankey visual was designed using **Income Bracket**, **Employment Type**, and **Total Loan Amount** to visualize the flow of loans across borrower income groups and employment categories.

This visualization helps users understand loan distribution patterns and identify major lending segments.

---

* **Step 20 :** Various report pages were designed to provide comprehensive analysis of loan performance, borrower demographics, and financial risk.

The report contains three interactive dashboard pages:

(a) Loan Default & Overview

(b) Applicant Demographic & Financial Profile

(c) Financial Risk Metrics

Each report page provides a different analytical perspective while maintaining consistent navigation, formatting, and user experience.

---

* **Step 21 :** Appropriate formatting, interactive filtering, cross-highlighting, titles, legends, data labels, custom color themes, borders, and report layouts were applied to improve dashboard readability and enhance the overall analytical experience.

After completing dashboard development and validation, the report was published to **Power BI Service**, allowing users to securely access and interact with the report online.

# Snapshot of Dashboard (Power BI Service)

![Power BI Service Dashboard](YOUR_POWERBI_SERVICE_IMAGE_LINK)

---

# Report Snapshot (Power BI Desktop)

### Loan Default & Overview

![Dashboard 1](YOUR_GITHUB_IMAGE_LINK_1)

---

### Applicant Demographic & Financial Profile

![Dashboard 2](YOUR_GITHUB_IMAGE_LINK_2)

---

### Financial Risk Metrics

![Dashboard 3](YOUR_GITHUB_IMAGE_LINK_3)

# Insights

A three-page interactive report was created on Power BI Desktop and was later published to Power BI Service.

Following inferences can be drawn from the dashboard;

---

### [1] Overall Loan Portfolio Analysis

The dashboard provides a comprehensive overview of the organization's loan portfolio by analyzing loan amounts, borrower profiles, default trends, and financial risk indicators.

Users can quickly evaluate lending performance, identify high-risk borrower segments, and monitor overall portfolio health using interactive visualizations.

---

### [2] Loan Purpose Analysis

The dashboard analyzes the total loan amount distributed across different loan purposes.

* Personal and Home loans contribute a significant portion of the overall loan portfolio.

* Business and Education loans account for a comparatively smaller share of total lending.

* Loan purpose analysis enables financial institutions to understand customer borrowing behavior and optimize lending strategies.

---

### [3] Employment & Income Analysis

The dashboard compares borrower income across different employment categories.

* Average income varies considerably among employment types.

* Employment status plays an important role in evaluating borrower financial stability.

* Income analysis helps identify customer segments with stronger repayment capacity.

* These insights support better credit assessment and loan approval decisions.

---

### [4] Default Rate Analysis

The dashboard provides a detailed comparison of loan default rates across different borrower segments.

* Default rates vary across employment categories and borrower profiles.

* Historical default trends help identify periods with increased credit risk.

* Monitoring default rates enables financial institutions to improve risk management and strengthen lending policies.

---

### [5] Credit Score Analysis

The report evaluates borrower creditworthiness using different credit score categories.

* Borrowers with higher credit scores generally receive larger loan amounts.

* Median loan amount varies across different credit score categories.

* Credit score analysis assists banks in understanding borrower risk profiles and improving loan approval strategies.

---

### [6] Demographic Analysis

The dashboard provides detailed insights into borrower demographics, including:

* Age Groups

* Marital Status

* Education Level

* Mortgage Status

* Number of Dependents

These analyses help financial institutions understand customer characteristics and evaluate how demographic factors influence borrowing behavior and loan performance.

---

### [7] Year-over-Year Financial Analysis

The dashboard tracks yearly lending performance using Year-over-Year comparisons.

* YOY Loan Amount Change helps evaluate annual lending growth.

* YOY Default Loan Change provides insights into changes in borrower repayment behavior over time.

* Historical trend analysis enables decision-makers to monitor portfolio performance and identify long-term business patterns.

---

### [8] Sankey Analysis

A Sankey Diagram was designed to visualize the relationship between borrower income groups, employment categories, and loan distribution.

This interactive visualization provides a clear understanding of how loans flow across different borrower segments and highlights major lending patterns within the portfolio.

---

### [9] Interactive Dashboard Features

The report includes several interactive Business Intelligence features, including:

* Employment Type Slicer

* Income Bracket Slicer

* Credit Score Category Slicer

* Cross Filtering

* Cross Highlighting

* Dynamic Visual Interactions

* Interactive Tooltips

These interactive features allow users to perform detailed loan analysis by combining multiple filters simultaneously and exploring borrower characteristics from different business perspectives.

---

### [10] Business Outcome

Using this dashboard, business users can:

* Monitor overall loan portfolio performance.

* Analyze loan distribution across different loan purposes.

* Evaluate borrower demographics and financial characteristics.

* Compare income and employment trends.

* Monitor loan default behavior.

* Assess borrower creditworthiness using credit score analysis.

* Track Year-over-Year lending performance.

* Identify high-risk customer segments.

* Improve lending strategies using data-driven insights.

* Support better financial planning and risk management decisions.

Overall, this dashboard provides a comprehensive Business Intelligence solution for analyzing loan portfolios, borrower demographics, financial risk, and lending performance. It enables banks, financial institutions, and credit analysts to make informed decisions, improve portfolio quality, reduce default risk, and optimize credit approval strategies through interactive and data-driven analytics.

