# SuperMax Retail Sales Dashboard (Power BI)

### Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Screenshots](#screenshots)
- [DAX and Data Model](#dax-and-data-model)
- [Key Takeaways](key-takeaways)
- [Areas of Opportunity](#areas-of-opportunity)


### Introduction

Over this past weekend, I took on a mini project to build my first dashboard in Power BI. The aim of this project was to highlight my ability to learn new data tools quickly and effectively, as well as challenge myself to continuously pursue additional data visualization techniques. 

The data used was originally sourced from Jagat Saikia on Kaggle [here](https://www.kaggle.com/datasets/jagatsaikia/category-brand-sales-dataset?select=Brand+Sales+Mock+Data+with+3+years+data.xlsx). As specified by Jagat, the mock data was generated to represent sales at a fictional retailer in the CPG industry.

The dashboard analyzes this mock POS sales data across time, sector, category, and brand, providing an interactive way to explore share trends and sales drivers in-store.

### Features

**KPI Cards:** Total Dollar Sales and Unit Sales
**Time Filtering:** Week-based slicer with earliest and latest available dates
**Segmentation:**
- Sales by Sector (Home Care vs. Family Care)
- Sales by Category (Dish Care, Air Care, Bath Tissue)
- Sales by Brand (ranked by total POS sales)
**Trend Analysis:** Sales over Time


### Screenshots

**Unfiltered Dashboard**

![Unfiltered Dashboard](/images/sales_dashboard_unfiltered.png)

**Filtered Dashboard**

![Filtered Dashboard](/images/sales_dashboard_filtered.png)


### DAX and Data Model

For our model, I used DAX to increase the usability of the default filtering options in Power BI for time-based analysis. Our data source was pre-aggregated at the week level and by default the *Between* slicer option allows the user to filter by any calendar date, conflicting with the underlying dataset. To resolve this issue, I decided to create the WeekIndex calculated field for filtering. The added filter allows the user to select a specified week index, and the two additional cards indicate the min and max dates of the selection.

```DAX
WeekIndex = RANKX(
    ALL('Table2 (3)'[Week]), 
    'Table2 (3)'[Week], 
    , ASC, 
    DENSE
)
```

The function above iterates over each row in the week column and applies a rank in ascending order based upon all unfiltered values and matching all ties.


### Key Takeaways

- Demonstrated learning agility by building a functional dashboard in Power BI Desktop with no prior experience over a weekend.
- Applied domain framing for CPG analytics, highlighting Sector, Category, Brand, and time-based sales insights.
- Identified areas of opportunity for continued learning in the Power BI tool.









