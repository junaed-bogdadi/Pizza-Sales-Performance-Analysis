# Pizza Sales Performance Analysis

## Project Overview

This project presents an interactive Power BI dashboard for analysing pizza sales performance. It examines revenue, order volume, customer purchasing patterns, and product performance to support business decisions.

The report includes two pages: **Home** and **Best/Worst seller**.

## Dashboard Preview

![Pizza Sales Dashboard](screenshort%201.jpeg)

## Business Objectives

- Monitor overall revenue and sales performance.
- Measure average order value and pizzas sold per order.
- Identify monthly and weekday sales patterns.
- Compare revenue contributions across pizza categories and sizes.
- Explore best- and worst-selling products.

## Tools and Technologies

- **Power BI Desktop:** Data modelling and interactive reporting.
- **Power Query:** Data import, type conversion, and label transformation.
- **DAX:** Calculation of key performance indicators.
- **Microsoft Excel:** Source data format referenced by the template.

## Dataset Structure

The `pizza_sales` table contains the following fields:

| Field | Description |
|---|---|
| pizza_id | Pizza sales record identifier |
| order_id | Order identifier |
| pizza_name_id | Pizza product code |
| quantity | Number of pizzas in the sales record |
| order_date | Date of the order |
| order_time | Time of the order |
| unit_price | Price per pizza |
| total_price | Revenue recorded for the sales line |
| pizza_size | Pizza size |
| pizza_category | Pizza category |
| pizza_ingredients | Ingredients associated with the pizza |
| pizza_name | Pizza product name |

An order can contain multiple sales records. Therefore, total orders are calculated using a distinct count of `order_id`.

## Key Performance Indicators

The dashboard screenshot displays the following rounded values:

| KPI | Displayed Value |
|---|---:|
| Total Revenue | $817.86K |
| Total Orders | 21.35K |
| Total Pizzas Sold | 49.57K |
| Average Order Value | $38.31 |
| Average Pizzas per Order | 2.32 |

These values reflect the dashboard screenshot and have not been independently recalculated from the source dataset.

## DAX Measures

The following measures are included in the Power BI model:

```dax
Total Revenue =
SUM(pizza_sales[total_price])

Total order =
DISTINCTCOUNT(pizza_sales[order_id])

Avg Order value =
[Total Revenue] / [Total order]

Total Pizza Sold =
SUM(pizza_sales[quantity])

Avg Pizza Per Order =
[Total Pizza Sold] / [Total order]
```

## Analysis Workflow

1. Import the Excel worksheet using Power Query.
2. Promote the first row to column headers.
3. Assign appropriate data types to identifiers, dates, quantities, and prices.
4. Transform pizza size labels for reporting.
5. Create DAX measures for revenue, orders, and sales volume.
6. Build visualisations for monthly trends, weekday sales, categories, and sizes.
7. Add slicers for pizza category, pizza size, and month.

## Key Findings

### 1. Friday Leads Weekday Sales Volume

The weekday chart shows approximately **8.2K pizzas sold on Friday**, the highest displayed total. Sunday records approximately **6.0K**, the lowest.

This indicates that staffing and ingredient preparation should be reviewed against weekday demand.

### 2. Classic Pizzas Generate the Largest Revenue Share

The Classic category contributes approximately **26.91% of total revenue**, followed by:

- Supreme: **25.46%**
- Chicken: **23.96%**
- Veggie: **23.68%**

Classic also leads category sales volume, with approximately **15K pizzas sold**.

Percentages are rounded and may not sum to exactly 100%.

### 3. Large Pizzas Contribute the Most Revenue

Large pizzas account for approximately **45.89% of total revenue**, followed by Medium at **30.49%** and Small at **21.77%**.

Revenue contribution should be considered alongside unit sales, pricing, and product costs before making profitability decisions.

### 4. Monthly Sales Volume Varies

The monthly chart shows sales volumes of approximately **3.9K–4.4K pizzas**. September, October, and December are near the lower end of the displayed range.

The February tooltip shows **3,961 pizzas sold**.

## Business Recommendations

- Align staffing and ingredient preparation with higher Friday demand.
- Maintain sufficient stock for Classic pizzas and Large sizes.
- Investigate lower-volume months before planning targeted promotions.
- Evaluate product-level performance on the Best/Worst seller page.
- Include ingredient costs and margins in future analysis to assess profitability.

These recommendations are analytical suggestions, not measured business outcomes.

## Repository Contents

| File | Purpose |
|---|---|
| `pizza sales analysis  .pbit` | Power BI report template |
| `screenshort 1.jpeg` | Dashboard screenshot |
| `README.md` | Project documentation |

## How to Open the Project

1. Download or clone this repository.
2. Open `pizza sales analysis  .pbit` in Power BI Desktop.
3. Update the Excel file path in the Power Query Source step.
4. Select the appropriate `pizza_sales` worksheet.
5. Refresh the report.

**Important:** The template currently references an Excel file on the author's local computer. The source Excel dataset is not included in this repository, so refreshing the report requires access to a compatible dataset.

## Limitations and Future Improvements

- Add the source dataset, subject to its licence and sharing permissions.
- Document the dataset source and reporting period.
- Correct the `Mediu` size label to `Medium`.
- Use exact-value replacements when standardising size codes.
- Replace the fixed local source path with a file-path parameter.
- Use `DIVIDE()` in ratio measures to handle zero denominators safely.
- Validate missing values, duplicates, and revenue calculations before refresh.
- Add hourly demand analysis using `order_time`.
- Include cost data to distinguish sales performance from profitability.

## Author

**Junaed Bogdadi**

[GitHub Profile](https://github.com/junaed-bogdadi)
