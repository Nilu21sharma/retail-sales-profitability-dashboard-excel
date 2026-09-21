# Retail Sales & Profitability Dashboard Using Excel

An Excel analytics project that cleans Superstore retail transactions and turns them into an interactive sales and profitability dashboard. The analysis focuses on the difference between revenue growth and profitable growth, with views by time, region, category, product, customer segment, and discount level.

## Project At A Glance

| Item | Details |
| --- | --- |
| Project type | Retail sales and profitability analysis |
| Primary tool | Microsoft Excel |
| Data preparation | Excel Power Query |
| Analysis | Excel Tables, PivotTables, PivotCharts, slicers, KPI cards |
| Raw records | 10,194 |
| Cleaned records | 10,192 |
| Raw columns | 21 |
| Cleaned columns | 29 |
| Unique orders | 5,111 |
| Unique customers | 804 |
| Unique products | 1,862 |

## Business Problem

Retail sales volume alone does not show whether the business is creating value. High-sales products, categories, or regions can still produce weak or negative profit when discounts, pricing, or costs are unfavorable.

This project answers the following questions:

- How much sales and profit are being generated?
- Which regions, categories, and products perform best?
- Which customer segments contribute the most revenue?
- How does discounting affect profitability?
- Where are the loss-making products and transactions that need investigation?

## Objectives

- Monitor sales, profit, margin, order, and quantity KPIs.
- Analyse monthly sales and profit trends.
- Compare regional, category, sub-category, product, and segment performance.
- Measure the relationship between discounts and profit.
- Identify high-performing and loss-making products.
- Convert the analysis into practical commercial recommendations.

## Dataset

The source is a Superstore retail transaction dataset containing order, customer, product, location, sales, discount, and profit fields. The raw file is available at [data/raw_data/superstore_sales_raw_data.csv](data/raw_data/superstore_sales_raw_data.csv).

The source fields include `Order ID`, `Order Date`, `Ship Date`, `Ship Mode`, `Customer ID`, `Customer Name`, `Segment`, `Country/Region`, `City`, `State/Province`, `Postal Code`, `Region`, `Product ID`, `Category`, `Sub-Category`, `Product Name`, `Sales`, `Quantity`, `Discount`, and `Profit`, together with the technical `Row ID` field.

### Data Quality And Cleaning

Cleaning was completed in Power Query and documented in [project-01-data-cleaning-report.md](data/cleaned_data/project-01-data-cleaning-report.md). The process:

1. Promotes the first row to headers and applies US date culture to the source dates.
2. Assigns appropriate text, date, integer, and numeric types.
3. Keeps `Postal Code` as text because Canadian postal codes can be alphanumeric.
4. Trims and cleans text fields.
5. Removes repeated business line items while retaining the technical `Row ID`.
6. Validates shipping dates, positive sales and quantity, valid discounts, and non-null profit.
7. Retains negative profit because loss-making transactions are valid business records and are required for the analysis.

The cleaned workbook is [superstore_sales_cleaned_data.xlsx](data/cleaned_data/superstore_sales_cleaned_data.xlsx). The reusable query is [project-01-power-query-cleaning-script.pq](data/cleaned_data/project-01-power-query-cleaning-script.pq). Before running the query in another environment, replace its placeholder `File.Contents` path with the local raw CSV path.

The cleaning process adds `Order Year`, `Order Month No`, `Order Month Name`, `Order Year-Month`, `Shipping Days`, `Profit Margin`, `Profit Status`, `Discount Band`, and `Sales Bucket`.

## Dashboard

The completed dashboard workbook is [retail_sales_profitability_dashboard.xlsx](dashboard/retail_sales_profitability_dashboard.xlsx). It includes:

- KPI cards for total sales, total profit, profit margin, orders, and average order value.
- Slicers for interactive filtering.
- Monthly sales and profit trends.
- Regional sales and profit comparisons.
- Category and sub-category performance.
- Customer segment contribution.
- Discount impact analysis.
- Top 10 products by sales.
- Executive insight summaries.

Preview images are available in [Insights_screenshot](Insights_screenshot/):

- [Dashboard overview 1](Insights_screenshot/excel_dashboard_overview_01.png)
- [Dashboard overview 2](Insights_screenshot/excel_dashboard_overview_02.png)

## Reported KPIs

The dashboard analysis reports the following values:

| KPI | Value |
| --- | ---: |
| Total sales | $2.33M |
| Total profit | $292.27K |
| Profit margin | 12.56% |
| Total orders | 5,111 |
| Average order value | $455.13 |
| Total quantity sold | 38,644 |
| Average discount | 15.54% |
| Loss-making rows | 1,900 |

## Key Insights

1. The business generated $2.33M in sales and $292.27K in profit, producing a 12.56% overall margin.
2. West was the strongest region by sales and profit. East also performed strongly, while Central showed weaker profitability relative to its sales volume.
3. Technology was the strongest category by both sales and profit.
4. Furniture generated substantial sales but weaker profit, indicating potential pricing, cost, or discount pressure.
5. Consumer was the largest revenue-contributing customer segment.
6. Medium and high discount bands produced negative profit, showing that aggressive discounting can damage profitability.
7. Product decisions should use both sales and profit because high sales do not guarantee strong margins.

## Recommendations

- Reduce aggressive discounts on low-margin and loss-making products.
- Prioritise profitable Technology products and selected Office Supplies products in campaigns.
- Review Furniture pricing, costs, and discount strategy.
- Investigate loss-making products before promoting them heavily.
- Use regional performance to target improvement in weaker markets.
- Track profit margin alongside sales for product and category decisions.

## Project Progress

| Workstream | Status | Evidence |
| --- | --- | --- |
| Raw data collected | Complete | [Raw CSV](data/raw_data/superstore_sales_raw_data.csv) |
| Data cleaning logic | Complete | [Power Query script](data/cleaned_data/project-01-power-query-cleaning-script.pq) |
| Cleaning documentation | Complete | [Cleaning report](data/cleaned_data/project-01-data-cleaning-report.md) |
| Cleaned Excel dataset | Complete | [Cleaned workbook](data/cleaned_data/superstore_sales_cleaned_data.xlsx) |
| Dashboard workbook | Complete | [Dashboard workbook](dashboard/retail_sales_profitability_dashboard.xlsx) |
| Dashboard previews | Complete | [Screenshot folder](Insights_screenshot/) |
| Reproducibility setup | Ready for reuse | Update the placeholder source path in the Power Query script |

## Project Structure

```text
retail-sales-profitability-dashboard-excel/
├── README.md
├── dashboard/
│   └── retail_sales_profitability_dashboard.xlsx
├── data/
│   ├── raw_data/
│   │   └── superstore_sales_raw_data.csv
│   └── cleaned_data/
│       ├── superstore_sales_cleaned_data.xlsx
│       ├── project-01-data-cleaning-report.md
│       └── project-01-power-query-cleaning-script.pq
└── Insights_screenshot/
	├── excel_dashboard_overview_01.png
	└── excel_dashboard_overview_02.png
```

## How To Use The Project

1. Open the dashboard workbook to review the finished analysis and interact with its slicers.
2. Review the cleaning report to understand the data decisions and expected row counts.
3. Open the Power Query script in Excel and replace the placeholder source path if rebuilding the cleaned dataset.
4. Load the cleaned query to an Excel Table named `Sales_Cleaned`, then refresh the PivotTables and dashboard.

## Skills Demonstrated

- Power Query data cleaning and validation.
- Excel data typing and calculated fields.
- PivotTable and PivotChart analysis.
- Interactive slicer and KPI dashboard design.
- Profitability, discount, regional, category, and product analysis.
- Translating analysis into business recommendations.

## Documentation

This README is the primary project documentation and contains the business context, methodology, findings, recommendations, and work progress. Supporting data-cleaning documentation is available in [project-01-data-cleaning-report.md](data/cleaned_data/project-01-data-cleaning-report.md).
