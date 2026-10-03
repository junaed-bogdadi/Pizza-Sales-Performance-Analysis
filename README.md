# Pizza Sales Performance Analysis

An interactive Power BI project exploring sales performance, purchasing patterns, and product-level trends.

## Project Overview

This project analyses pizza sales through revenue, order volume, sales quantity, and average order metrics. It helps identify demand patterns and compare performance across pizza categories, sizes, and products.

The Power BI report contains two pages:

- **Home:** Overall sales performance, monthly and weekday trends, and category and size comparisons.
- **Best/Worst seller:** Top and bottom products across the metrics displayed in the report.

## Dashboard Preview

### Sales Overview

![Sales Overview Dashboard](screenshort%201.jpeg)

### Best and Worst Sellers

![Best and Worst Sellers Dashboard](screenshort%202.jpeg)

## Business Objectives

- Track revenue, total orders, and pizzas sold.
- Measure average order value and average pizzas per order.
- Identify monthly and weekday demand patterns.
- Compare revenue contributions across pizza categories and sizes.
- Examine top- and bottom-performing products.
- Develop recommendations for inventory, staffing, and promotions.

## Tools and Technologies

| Tool | Application |
|---|---|
| Power BI Desktop | Data modelling, visualisation, and interactive reporting |
| Power Query | Data import, type conversion, and size-label transformation |
| DAX | Calculation of sales performance measures |
| Microsoft Excel | Source data format referenced by the template |

## Dataset Structure

The `pizza_sales` table contains the following fields:

| Field | Description |
|---|---|
| `pizza_id` | Pizza sales record identifier |
| `order_id` | Order identifier |
| `pizza_name_id` | Pizza product code |
| `quantity` | Number of pizzas in a sales record |
| `order_date` | Date of the order |
| `order_time` | Time of the order |
| `unit_price` | Price per pizza |
| `total_price` | Revenue recorded for the sales line |
| `pizza_size` | Pizza size |
| `pizza_category` | Pizza category |
| `pizza_ingredients` | Ingredients associated with the pizza |
| `pizza_name` | Pizza product name |

An order may contain multiple sales records. Total orders are therefore calculated using a distinct count of `order_id`.

## Key Performance Indicators

| KPI | Dashboard Value |
|---|---:|
| Total Revenue | $817.86K |
| Total Orders | 21.35K |
| Total Pizzas Sold | 49.57K |
| Average Order Value | $38.31 |
| Average Pizzas per Order | 2.32 |

> The figures above are rounded values displayed in the dashboard screenshots. They have not been independently recalculated from the source dataset.

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

For a future model update, `DIVIDE()` can be used in the two ratio measures to handle zero denominators safely.

## Analysis Workflow

1. Import the Excel worksheet into Power BI.
2. Promote the first row to column headers.
3. Assign appropriate data types to the dataset fields.
4. Transform pizza size labels using Power Query.
5. Create DAX measures for the main sales indicators.
6. Build monthly, weekday, category, size, and product-level visualisations.
7. Add slicers for pizza category, pizza size, and month.
8. Organise the report into overview and product-performance pages.

## Key Findings

### Weekday Sales Performance

Friday records the highest displayed sales volume at approximately **8.2K pizzas**, while Sunday records the lowest at approximately **6.0K**.

This pattern suggests reviewing staffing and ingredient preparation against weekday demand.

### Revenue by Pizza Category

| Category | Revenue Share |
|---|---:|
| Classic | 26.91% |
| Supreme | 25.46% |
| Chicken | 23.96% |
| Veggie | 23.68% |

Classic generates the largest revenue share and also leads category sales volume, with approximately **15K pizzas sold**.

Percentages are rounded and may not sum to exactly 100%.

### Revenue by Pizza Size

| Size | Revenue Share |
|---|---:|
| Large | 45.89% |
| Medium | 30.49% |
| Small | 21.77% |

Large pizzas contribute the greatest share of revenue. These figures represent sales contribution; profitability requires additional cost data.

### Monthly Sales Patterns

Monthly pizza sales are approximately **3.9K–4.4K** in the displayed chart. September, October, and December are near the lower end of the range.

The February tooltip displays **3,961 pizzas sold**.

### Product-Level Performance

The Best/Worst seller page displays top and bottom products by revenue and the sales metrics labelled in the report.

The displayed revenue rankings range from approximately **$43K** for the leading products to approximately **$12K** for the lowest-ranked product.

Product names are truncated in the screenshot. Full product names and the distinction between **Pizza Sold** and **Pizza Qty** should be confirmed in Power BI before reporting detailed product rankings.

## Business Recommendations

- Align staffing and ingredient preparation with higher Friday demand.
- Maintain adequate inventory for Classic pizzas and Large sizes.
- Investigate lower-volume months before introducing targeted promotions.
- Review lower-performing products alongside pricing, costs, and customer demand.
- Include ingredient costs and margins in future profitability analysis.

These recommendations are proposed actions based on the displayed patterns. Their business impact has not been measured.

## Repository Contents

| File | Description |
|---|---|
| `pizza sales analysis  .pbit` | Power BI report template |
| `screenshort 1.jpeg` | Sales overview dashboard screenshot |
| `screenshort 2.jpeg` | Best and worst sellers dashboard screenshot |
| `README.md` | Project overview, methodology, and findings |

## How to Open the Project

1. Download or clone this repository.
2. Open `pizza sales analysis  .pbit` in Power BI Desktop.
3. Open Power Query and update the Excel file path in the Source step.
4. Connect to a compatible workbook containing the `pizza_sales` worksheet.
5. Apply the changes and refresh the report.

> The template references an Excel file on the author's local computer. The source dataset is not included in this repository, so data refresh requires a compatible source file.

## Limitations and Future Improvements

- Include the source dataset where its licence permits sharing.
- Document the dataset source and reporting period.
- Correct the `Mediu` size label to `Medium`.
- Use exact-value replacements when standardising pizza size codes.
- Replace the fixed local file path with a configurable parameter.
- Use `DIVIDE()` for ratio measures.
- Validate missing values, duplicate records, and revenue calculations.
- Clarify the difference between the Pizza Sold and Pizza Qty charts.
- Improve screenshot readability by displaying full KPI labels and product names.
- Add hourly demand analysis using `order_time`.
- Incorporate cost data for profitability analysis.

## Author

**Junaed Bogdadi**

[GitHub Profile](https://github.com/junaed-bogdadi)
